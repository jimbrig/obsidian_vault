%%
ID: 2962970
Updated: 2020-06-08
%%
![](https://readwise-assets.s3.amazonaws.com/static/images/article3.5c705a01b476.png)

# About
Title: [[Getting Data From PDFs the Easy Way With R - Open Source Automation]]
Author: 
Category: #articles
Number of Highlights: ==3==
Last Highlighted: *2020-06-07*
Readwise URL: https://readwise.io/bookreview/2962970
Source URL: http://theautomatic.net/2018/08/24/getting-data-from-pdfs-the-easy-way-with-r/


# Highlights 
package called tabulizer was released in R, which allows you to automatically pull out tables and text from PDFs. Note, this package only works if the PDF’s text is highlightable (if it’s typed) — i.e. it won’t work for scanned-in PDFs, or image files converted to PDFs  ^64489446

---

You can extract tables from this PDF using the aptly-named extract_tables function, like this:


# default call with no parameters changed
matrix_results <- extract_tables(site)

# get back the tables as data frames, keeping their headers
df_results <- extract_tables(site, output = "data.frame", header = TRUE)  ^64489447

---

Scraping text from our sample PDF can be done using extract_text:  ^64489448

