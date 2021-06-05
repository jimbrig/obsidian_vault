%%
ID: 2903153
Updated: 2020-08-25
%%
![](https://readwise-assets.s3.amazonaws.com/static/images/article1.be68295a7e40.png)

# About
Title: [[How to Distribute Data With Your R Package - R-Hub Blog]]
Author: 
Category: #articles
Number of Highlights: ==16==
Last Highlighted: *2020-06-02*
Readwise URL: https://readwise.io/bookreview/2903153
Source URL: https://blog.r-hub.io/2020/05/29/distribute-data/


# Highlights 
If the data is for the user to load and use in examples or their own code, you’re looking for exported data. Since it’s exported, it has to be documented. For an example, see the babynames data/ folder and R/data.R file  ^63768443

---

If the data is for your functions to use internally, you’re after R/sysdata.R or an internal function.  ^63768444

---

If the data is to showcase how to tidy raw data, and you want the user to be able to access it, you’re after… raw data living in inst/extdata.  ^63768445

---

If you want to keep the raw data used to create your exported or internal data, which you should, you’re after the data-raw folder. See the data-raw folder of the babynames package, in particular its R scripts. Note that data-raw has to be in the .Rbuildignore file (but usethis would help you with that).  ^63768446

---

For data used in test, i.e. fixtures, you could create a folder under e.g. tests/testthat/ and whose content would be found using the testthat::test_path() function.  ^63768447

---

Data as small as possible
As “Writing R Extensions” underlines, for data under data/ and, “If your package is to be distributed, do consider the resource implications of large datasets for your users: they can make packages very slow to download and use up unwelcome amounts of storage space, as well as taking many seconds to load.". So what do you do?

You can compress the data, internal or external. Your friends are tools::resaveRdaFiles()  ^63768448

---

Data outside of your package
Now, sometimes the data is too big to be in your package, or follows a different development cycle i.e. is updated more or less often. What can you do about that? Well, have data live somewhere else.  ^63768449

---

Data packages
Yes, this subsection makes the point of having data live inside another package. 😑 You could develop companion packages to go with your package, that hold data. A data package is user-friendly in the sense that installing it saves the data on the machine and makes it available.  ^63768450

---

You could also check out the datastorr package (not on CRAN) for integrating data packages with GitHub.  ^63768451

---

You could use an existing infrastructure: GitHub releases (with the piggyback package whose documentation includes a thorough comparison with other approaches such as git-LFS), Amazon S3 (using the pins package?), etc.. You could make use of scientific data repositories (DataONE, Zenodo, OSF, Figshare…).  ^63768452

---

You could use an existing infrastructure: GitHub releases (with the piggyback package whose documentation includes a thorough comparison with other approaches such as git-LFS), Amazon S3 (using the pins package?), etc  ^63768454

---

The data could be cached in an app dir which we explained in a previous blog post, using the rappdirs or hoardr package;  ^63768455

---

For other approaches, your package could take a dependency on a package aimed at data storage and retrieval such as the aforementioned piggyback and pins packages, the bowerbird package, the rdataretriever package.  ^63768456

---

In this post we went over different setups allowing you to distribute data with or for your R package: some standard locations in your package source (inst/extdata/, data/, R/sysdata.rda); locations outside of your package (using drat, git-LFS, GitHub releases via piggyback, a web API you’d build yourself), that your package would know how to access, and potentially save locally (in an app dir, or using a tool like bowerbird). Do you have a “data and R package” setup you’d like to share? How do you document the data you share, when it’s bigger than a small table  ^63768457

---

In this post we went over different setups allowing you to distribute data with or for your R package: some standard locations in your package source (inst/extdata/, data/, R/sysdata.rda); locations outside of your package (using drat, git-LFS, GitHub releases via piggyback, a web API you’d build yourself), that your package would know how to access, and potentially save locally (in an app dir, or using a tool like bowerbird). Do you have a “data and R package” setup you’d like to share? How do you document the data you share, when it’s bigger than a small table?  ^63768458

