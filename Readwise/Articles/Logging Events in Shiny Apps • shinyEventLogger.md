%%
ID: 2982155
Updated: 2020-06-09
%%
![](https://readwise-assets.s3.amazonaws.com/static/images/article0.00998d930354.png)

# About
Title: [[Logging Events in Shiny Apps • shinyEventLogger]]
Author: 
Category: #articles
Number of Highlights: ==4==
Last Highlighted: *2020-06-09*
Readwise URL: https://readwise.io/bookreview/2982155
Source URL: https://kalimu.github.io/shinyEventLogger/index.html


# Highlights 
Simple app logging different events to R console, browser JavaScript console and to a file.

shinyEventLogger::run_demo()  ^64752124

---

Dashboard that allows for interactive analysis of events from demo app.

shinyEventLogger::run_demo_dashboard()  ^64752125

---

library(shiny)
library(shinyEventLogger)
set_logging()
shinyApp(
  ui = fluidPage(log_init()),
  server = function(input, output) {
    set_logging_session()
    log_event("Hello World")
 }
)  ^64752126

---

For other logging packages see: https://github.com/daroczig/logger  ^64752127

