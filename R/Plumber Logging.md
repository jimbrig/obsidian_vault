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

Now that we’ve defined two endpoints (`/echo` and `/plot`), we can use `entrypoint.R` to setup logging using preroute and postroute hooks. First, we need to configure the logger package:

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

***
Links: [[R Development]]
Source: [Plumber Logging · R Views (rstudio.com)](https://rviews.rstudio.com/2019/08/13/plumber-logging/)

