%%
ID: 2756819
Updated: 2020-05-23
%%
![](https://readwise-assets.s3.amazonaws.com/static/images/article3.5c705a01b476.png)

# About
Title: [[Usethis Workflow for Package Development  Emil Hvitfeldt]]
Author: 
Category: #articles
Number of Highlights: ==21==
Last Highlighted: *2020-05-14*
Readwise URL: https://readwise.io/bookreview/2756819
Source URL: https://www.hvitfeldt.me/blog/usethis-workflow-for-package-development/


# Highlights 
The usethis promises to

… it automates repetitive tasks that arise during project setup and development, both for R packages and non-package projects.  ^61947475

---

Before creation
Before we get started we need to make sure we have the essential packages installed to create a R package development workflow


library(devtools)
library(roxygen2)
library(usethis)  ^61947476

---

library(available)
available("utwf")  ^61947477

---

create_package("~/Desktop/utwf")
use_git()
use_github()  ^61947478

---

We can check that the package works by pressing “Install and Restart” in the “Build” panel. Alternatively you can use the keyboard shortcut Cmd+Shift+B (Ctrl+Shift+B for Windows).  ^61947479

---

DESCRIPTION file and make sure that the Authors@R is populated correctly and modify the Title and Description fields.

Next we will license the package. This can be done using one of the following functions (we will use MIT for this example)  ^61947480

---

use_readme_rmd()  ^61947481

---

use_travis()
use_appveyor()
use_coverage(type = c("codecov"))  ^61947482

---

use_testthat()  ^61947483

---

use_spell_check()  ^61947484

---

use_data_raw()  ^61947485

---

use_news_md()  ^61947486

---

Multiple time modifications  ^61947487

---

You typical workflow will be repeating the following steps in the order that suits your flow

Write some code
Restart R Session Cmd+Shift+F10 (Ctrl+Shift+F10 for Windows)
Build and Reload Cmd+Shift+B (Ctrl+Shift+B for Windows)
Test Package Cmd+Shift+T (Ctrl+Shift+T for Windows)
Check Package Cmd+Shift+E (Ctrl+Shift+E for Windows)
Document Package Cmd+Shift+D (Ctrl+Shift+D for Windows)
Writing code most likely includes writing functions, this is helped by the use_r() function by adding and opening a .R file that you write your function in

use_r("function_name")  ^61947488

---

but it will also open the files if they are already created, this makes navigating your R files much easier  ^61947489

**Note: wow-did not know this!**

---

Once you have created your function it is time to add some tests! This is done using the use_test() function, and it works much the same way as the use_r().

use_test("function_name")  ^61947490

---

In the creating of your functions, you might need to depend on another package, to add a function to the imports field in the DESCRIPTION file you can use the use_package() function

use_package("dplyr")  ^61947491

---

Special cases function includes use_rcpp(), use_pipe() and use_tibble().

An vignette provides a nice piece of documentation once you have added a bunch of capabilities to your package.

use_vignette("How to do this cool analysis")  ^61947492

---

Before every commit
Before you commit, run the following commands one more time to make sure you didn’t break anything.

Restart R Session Cmd+Shift+F10 (Ctrl+Shift+F10 for Windows)
Document Package Cmd+Shift+D (Ctrl+Shift+D for Windows)
Check Package Cmd+Shift+E (Ctrl+Shift+E for Windows)  ^61947493

---

Before every release
You have worked and have created something wonderful. You want to showcase the work. First go knit the readme.Rmd file and then run these commands again to check that everything is working.

Restart R Session Cmd+Shift+F10 (Ctrl+Shift+F10 for Windows)
Document Package Cmd+Shift+D (Ctrl+Shift+D for Windows)
Check Package Cmd+Shift+E (Ctrl+Shift+E for Windows)  ^61947494

---

update the version number with the use of

use_version()  ^61947495

