%%
ID: 2962971
Updated: 2020-06-08
%%
![](https://readwise-assets.s3.amazonaws.com/static/images/article3.5c705a01b476.png)

# About
Title: [[Rstudio - Use Internal Links in RMarkdown HTML Output - Stack Overflow]]
Author: 
Category: #articles
Number of Highlights: ==1==
Last Highlighted: *2020-06-07*
Readwise URL: https://readwise.io/bookreview/2962971
Source URL: https://stackoverflow.com/questions/39281266/use-internal-links-in-rmarkdown-html-output


# Highlights 
Pandoc supports explicit and implicit section references for headers; see the pandoc manual.

explicit: you give a custom name to a header ## Test {#test} and later refer to it with a link syntax: see [the relevant section](#test).
implicit: headers where you don't set a custom name, like ## Test, can still be refered to: See the section called [Test].  ^64489449

