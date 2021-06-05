%%
ID: 6483598
Updated: 2020-12-01
%%
![](https://readwise-assets.s3.amazonaws.com/static/images/article4.6bc1851654a0.png)

# About
Title: [[Rd Formatting]]
Author: [[roxygen2.r-lib.org]]
Category: #articles
Number of Highlights: ==4==
Last Highlighted: *2020-11-30*
Readwise URL: https://readwise.io/bookreview/6483598
Source URL: https://roxygen2.r-lib.org/articles/rd-formatting.html


# Highlights 
To turn on markdown for the whole package, insert this entry into the DESCRIPTION file of the package:

Roxygen: list(markdown = TRUE)  ^115290478

---

Alternatively, you can use the @md tag to turn on markdown support for a single documentation chunk. This is a good option to write any new documentation for existing packages in markdown.

There is also a new @noMd tag. Use this if you turned on markdown parsing globally, but need to avoid it for a single chunk. This tag is handy if the markdown parser interferes with more complex Rd syntax.

Here is an example roxygen chunk that uses markdown.

#' Use roxygen to document a package
#'
#' This function is a wrapper for the [roxygen2::roxygenize()] function from
#' the roxygen2 package. See the documentation and vignettes of
#' that package to learn how to use roxygen.
#'
#' @param pkg package description, can be path or package name.  See
#'   [as.package()] for more information
#' @param clean,reload Deprecated.
#' @inheritParams roxygen2::roxygenise
#' @seealso [roxygen2::roxygenize()], `browseVignettes("roxygen2")`
#' @export
#' @md  ^115290479

---

The R code is evaluated in a new environment that is the child of the package environment of the package you are documenting. This means that you can call (internal or exported) functions of the package. packageName() will also report the name of the package:  ^115290480

---

Links

To other documentation:

\code{\link{function}}: function in this package

\code{\link[MASS]{abbey}}: function in another package

\link[=dest]{name}: link to dest, but show name

\code{\link[MASS:abbey]{name}}: link to function in another package, but show name.

\linkS4class{abc}: link to an S4 class

To the web:

\url{http://rstudio.com}

\href{http://rstudio.com}{Rstudio}

\email{hadley@@rstudio.com} (note the doubled @)  ^115290481

