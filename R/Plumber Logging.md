---
creation date: 2021-04-21 16:32
modification date: Wednesday 21st April 2021 16:32:53
tags: ["#r", "#api", "#plumber"]
author: Jimmy Briggs
---

# Plumber Logging

The [plumber R package](https://www.rplumber.io/docs/) is used to expose R functions as API endpoints. Due to plumber’s incredible flexibility, most major API design decisions are left up to the developer. One important consideration to be made when developing APIs is how to log information about API requests and responses. This information can be used to determine how plumber APIs are performing and how they are being utilized.

An example of logging API requests in plumber is included in the [package documentation](https://www.rplumber.io/docs/routing-and-input.html#filters). That example uses a filter to log information about incoming requests before a response has been generated. This is certainly a valid approach, but it means that the log cannot contain details about the response since the response hasn’t been created yet. In this post we will look at an alternative approach to logging plumber APIs that uses [preroute and postroute hooks](https://www.rplumber.io/docs/programmatic-usage.html#router-hooks) to log information about each API request and its associated response.

## Logging

Logging packages for R:

-  [logger](https://daroczig.github.io/logger/)

## Example API

In this example, I use the [logger package](https://daroczig.github.io/logger/) to generate the actual log entries. Using this package isn’t required, but it does provide some convenient functionality that we will take advantage of.

Since we will be registering hooks for our API, we will need both a `plumber.R` file and an `entrypoint.R` file. The `plumber.R` file contains the following:

```r
# plumber.R

library(plumber)

#* @apiTitle Logging Example
#* @apiDescription Simple example API for implementing logging with Plumber

#* Echo back the input
#* @param msg The message to echo
#* @get /echo
function(msg = "") {
  list(msg = paste0("The message is: '", msg, "'"))
}

#* Plot a histogram
#* @png
#* @get /plot
function() {
  rand <- rnorm(100)
  hist(rand)
}
```

Now that we’ve defined two endpoints (`/echo` and `/plot`), we can use `entrypoint.R` to setup logging using preroute and postroute hooks. 

First, we need to configure the logger package:

```
# entrypoint.R
library(plumber)

# logging
library(logger)

# Specify how logs are written
log_dir <- "logs"
if (!fs::dir_exists(log_dir)) fs::dir_create(log_dir)
log_appender(appender_tee(tempfile("plumber_", log_dir, ".log")))
```

The `log_appender()` function is used to specify which appender method is used for logging. Here we use `appender_tee()` so that logs will be written to `stdout` and to a specific file path. We create a directory called `logs/` in the current working directory to store the resulting logs. Every log file is assigned a unique name using `tempfile()`. This prevents errors that can occur if concurrent processes try to write to the same file.

Now, we need to create a helper function that we will use when creating log entries:

```
convert_empty <- function(string) {
  if (string == "") {
    "-"
  } else {
    string
  }
}
```

This function takes an empty string and converts it into a dash (`"-"`). We will use this to ensure that empty log values still get recorded so that it is easy to read the log files. We’re now ready to create our plumber router and register the hooks necessary for logging:

```
pr <- plumb("plumber.R")

pr$registerHooks(
  list(
    preroute = function() {
      # Start timer for log info
      tictoc::tic()
    },
    postroute = function(req, res) {
      end <- tictoc::toc(quiet = TRUE)
      # Log details about the request and the response
      log_info('{convert_empty(req$REMOTE_ADDR)} "{convert_empty(req$HTTP_USER_AGENT)}" {convert_empty(req$HTTP_HOST)} {convert_empty(req$REQUEST_METHOD)} {convert_empty(req$PATH_INFO)} {convert_empty(res$status)} {round(end$toc - end$tic, digits = getOption("digits", 5))}')
    }
  )
)

pr
```

***
Links: [[R Development]]
Source: [Plumber Logging · R Views (rstudio.com)](https://rviews.rstudio.com/2019/08/13/plumber-logging/)

