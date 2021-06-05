%%
ID: 4382432
Updated: 2020-09-06
%%
![](https://readwise-assets.s3.amazonaws.com/static/images/article0.00998d930354.png)

# About
Title: [[Re-Exporting the Magrittr Pipe Operator › Petermeissner]]
Author: [[Peter Meissner]]
Category: #articles
Number of Highlights: ==2==
Last Highlighted: *2020-09-04*
Readwise URL: https://readwise.io/bookreview/4382432
Source URL: https://petermeissner.de/blog/2018/04/27/re-exporting-the-pipe/


# Highlights 
Magrittr’s pipe operator is one of those newish R-universe features that I really want to have around whenever I put some lines into an R-console. This is even TRUE when writing a package.  ^83464324

---

So the first thing I do is put magrittr into the DESCRIPTION file and add an __imports.R file to the packages R/-directory with the following lines:  ^83464325

**Note: R/_imports.R

#' re-export magrittr pipe operator
#'
#' @importFrom magrittr %>%
#' @name %>%
#' @rdname pipe
#' @export
NULL**

