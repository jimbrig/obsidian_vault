%%
ID: 2962968
Updated: 2020-06-08
%%
![](https://readwise-assets.s3.amazonaws.com/static/images/article2.74d541386bbf.png)

# About
Title: [[Shiny- Load Testing and Horizontal Scaling]]
Author: [[Eoda Gmbh]]
Category: #articles
Number of Highlights: ==1==
Last Highlighted: *2020-06-07*
Readwise URL: https://readwise.io/bookreview/2962968
Source URL: https://eoda.de/en/wissen/blog/shiny-load-testing-und-horizontale-skalierung


# Highlights 
We use the R package shinyloadtest provided by RStudio and the associated Java application shinycannon as load testing tools.

The functionality of the tools can be explained by the figure above:

The package shinyloadtest offers the possibility to open a shiny application and record a user session of any length. The recorded session can then be used for load testing by providing a link to the shinycannon application. A fixed number of users (so called „workers“) is specified, who try to execute the recorded session on the server as often as possible within a selected time period. Finally, a report can be generated from the collected data of the load test, which will be discussed in the next paragraph.  ^64489441

