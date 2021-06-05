%%
ID: 2756796
Updated: 2020-05-23
%%
![](https://m.media-amazon.com/images/I/71AVbBLqg9L._SY500.jpg)

# About
Title: [[Reproducible Research With R and RStudio]]
Author: [[Christopher Gandrud]]
Category: #books
Number of Highlights: ==42==
Last Highlighted: *2020-04-19*
Readwise URL: https://readwise.io/bookreview/2756796

# Highlights 
the data and code used to make a fnding are available and they are suÿcient for an independent researcher to recreate the fnding. ([11798](https://readwise.io/to_kindle?action=open&asin=B08528HRYZ&location=11798)) %% Color: yellow %% ^61947389

---

In particular, you will learn tools for dynamically “knitting”5 the data and the source code together with your presentation documents. Combined with wellorganized source fles and clearly and completely commented code, independent researchers will be able to understand how you obtained your results. This will make your computational research easily reproducible. ([12234](https://readwise.io/to_kindle?action=open&asin=B08528HRYZ&location=12234)) %% Color: yellow %% ^61947390

---

Reproducible research is one of the main components of science. If that’s not enough reason for you to make your research reproducible, consider that the tools of reproducible research also have direct benefts for you as a researcher. ([12234](https://readwise.io/to_kindle?action=open&asin=B08528HRYZ&location=12234)) %% Color: yellow %% ^61947391

---

Reproducibility enhances replicability. ([12671](https://readwise.io/to_kindle?action=open&asin=B08528HRYZ&location=12671)) %% Color: yellow %% ^61947392

---

Avoiding e˙ort duplication and encouraging cumulative knowledge development Not only is reproducibility important for evaluating scientifc claims, it can also contribute to the cumulative growth of scientifc knowledge ([12672](https://readwise.io/to_kindle?action=open&asin=B08528HRYZ&location=12672)) %% Color: yellow %% ^61947393

---

Reproducible research cuts down on the amount of time scientists have to spend gathering data or developing procedures that have already been collected or fgured out. Because researchers do not have to discover on their own things that have already been done, they can more quickly build on established fndings and develop new knowledge. ([12672](https://readwise.io/to_kindle?action=open&asin=B08528HRYZ&location=12672)) %% Color: yellow %% ^61947394

---

Making a project reproducible from the start encourages you to use better work habits. It can spur you to more e˙ectively plan and organize your research. It should push you to bring your data and source code up to a higher level of quality than you might if you “thought ‘no one was looking’ ” (Donoho, 2010, 386). This forces you to root out errors–a ubiquitous part of computational research–earlier in the research process (Donoho, 2010, 385). Clear documentation also makes it easier to fnd errors.7 Reproducible research needs to be stored so that other researchers can actually access the data and source code. By taking steps to make your research accessible for others, you are also making it easier for yourself to fnd your data and methods when you revise your work or begin a new project. You are avoiding personal e˙ort duplication, allowing you to cumulatively build on your own work more e˙ectively. ([13108](https://readwise.io/to_kindle?action=open&asin=B08528HRYZ&location=13108)) %% Color: yellow %% ^61947395

---

If you are an experienced R user you may want to skip over the frst section of Chapter 3: Getting Started with R, RStudio, and knitr/rmarkdown. But don’t skip over the whole chapter. The latter parts contain important information on the knitr/rmarkdown packages. If you are experienced with R data manipulation, you may also want to skip all of Chapter 7. ([17915](https://readwise.io/to_kindle?action=open&asin=B08528HRYZ&location=17915)) %% Color: orange %% ^61947396

---

Before we start learning the details of the reproducible research workfow with R and RStudio, it’s useful to cover a few broad tips that will help you organize your research process and put these skills in perspective. The tips are: 1. Document everything! 2. Everything is a (text) fle. 3. All fles should be human readable. 4. Explicitly tie your fles together. 5. Have a plan to organize, store, and make your fles available. ([20973](https://readwise.io/to_kindle?action=open&asin=B08528HRYZ&location=20973)) %% Color: yellow %% ^61947397

---

In order to reproduce your research, others must be able to know what you did. You have to tell them what you did by documenting as much of your research process as possible. Ideally, you should tell your readers how you gathered your data, analyzed it, and presented the results. Documenting everything is the key to reproducible research and lies behind all of the other tips in this chapter and tools you will learn throughout the book. ([21409](https://readwise.io/to_kindle?action=open&asin=B08528HRYZ&location=21409)) %% Color: yellow %% ^61947398

---

Document your R session info ([21410](https://readwise.io/to_kindle?action=open&asin=B08528HRYZ&location=21410)) %% Color: yellow %% ^61947399

---

Learn from the text fle: keep it simple ([22283](https://readwise.io/to_kindle?action=open&asin=B08528HRYZ&location=22283)) %% Color: yellow %% ^61947400

---

Text fles are simple. Their simplicitly increases the probability of baseline usefulness in the future to researchers who will reproduce the work. We can extend the logic of the simple text fle to all of the tools we use: keep it simple. Avoid adding dependencies you don’t need to actually gather your data, analyze it, and present the results. For example, I have been tempted to make my presentation slides look nicer with custom fonts. I was later burned when I wanted to make minor changes to slides a year after I frst presented them (and a day before teaching an upcoming class) only to fnd that the custom fonts were no longer available. This broke my slides and forced me to spend considerable time reworking writing my source documents. If I, the creator of the slides, found this time consuming and annoying, an independent researcher would likely fnd it even more diÿcult. ([22283](https://readwise.io/to_kindle?action=open&asin=B08528HRYZ&location=22283)) %% Color: yellow %% ^61947401

---

All fles should be human readable ([22284](https://readwise.io/to_kindle?action=open&asin=B08528HRYZ&location=22284)) %% Color: yellow %% ^61947402

---

Literate programming ([23157](https://readwise.io/to_kindle?action=open&asin=B08528HRYZ&location=23157)) %% Color: yellow %% ^61947403

---

2.2.4 Explicitly tie your fles together ([23158](https://readwise.io/to_kindle?action=open&asin=B08528HRYZ&location=23158)) %% Color: yellow %% ^61947404

---

A data fle is used as input for an analysis fle. ([23158](https://readwise.io/to_kindle?action=open&asin=B08528HRYZ&location=23158)) %% Color: yellow %% ^61947405

---

The results of an analysis are shown and discussed in a markup fle that is used to create a PDF document. Researchers often do not explicitly document the relationships between fles that they used in their research. For example, the results of an analysis–a table or fgure–may be copied and pasted into a presentation document. It can be very diÿcult for future researchers to trace the table or fgure back to a particular statistical model and a particular data set without clear documentation. Therefore, it is important to make the links between your fles explicit. ([23158](https://readwise.io/to_kindle?action=open&asin=B08528HRYZ&location=23158)) %% Color: yellow %% ^61947406

---

Tie functions are the most dynamic way to explicitly link your fles together. These functions instruct the computer program you are using to use information from another fle. In Table 2.1, I have compiled a selection of key tie functions you will learn how to use in this book. We’ll discuss many more, but these are some of the most important. ([23159](https://readwise.io/to_kindle?action=open&asin=B08528HRYZ&location=23159)) %% Color: yellow %% ^61947407

---

Have a plan to organize, store, and make your fles available ([24030](https://readwise.io/to_kindle?action=open&asin=B08528HRYZ&location=24030)) %% Color: yellow %% ^61947408

---

Finally, in order for independent researchers to reproduce your work, they need to be able access the fles that instruct them how to do this. Files also need to be organized so that independent researchers can fgure out how they ft together. So, from the beginning of your research process, you should have a plan for organizing your fles and a way to make them accessible. One rule of thumb for organizing your research in fles is to limit the amount of content any one fle has. Files that contain many di˙erent operations can be very diÿcult to navigate, even if they have detailed comments. For example, it would be very diÿcult to fnd any particular operation in a fle that contained the code used to gather the data, run all of the statistical models, and create the results, fgures and tables. If you have a hard time fnding things in a fle you created, think of the diÿculties independent researchers will have! Because we have so many ways to link fles together, there is really no need to lump many di˙erent operations into one fle. So, we can make our fles modular. One source code fle should be used to complete one or just a few tasks. Breaking your operations into discrete parts will also make it easier for you and others to fnd errors (Nagler, 1995, 490). Chapter 4 discusses fle organization in much more detail. Chapter 5 teaches you a number of ways to make your fles accessible through the cloud computing services like GitHub. ([24030](https://readwise.io/to_kindle?action=open&asin=B08528HRYZ&location=24030)) %% Color: yellow %% ^61947409

---

cache Logical Whether or not to save results from the code chunk in a cache database. Note: cached chunks are only run when they are changed. cache.vars Character Vector Specify the variable names to save in the cache database. ([34516](https://readwise.io/to_kindle?action=open&asin=B08528HRYZ&location=34516)) %% Color: yellow %% ^61947410

---

When include=FALSE the chunk is evaluated, but the results are not included in the presentation document. ([34517](https://readwise.io/to_kindle?action=open&asin=B08528HRYZ&location=34517)) %% Color: yellow %% ^61947411

---

tidy ([34517](https://readwise.io/to_kindle?action=open&asin=B08528HRYZ&location=34517)) %% Color: yellow %% ^61947412

---

Hooks come in two types: chunk hooks and output hooks. Chunk hooks run a function before or after a code chunk. Output hooks change how the raw output is formatted. I don’t cover hooks in much detail in this book. For more information on hooks, please see Yihui Xie’s webpage: http://yihui.name/knitr/hooks. ([34954](https://readwise.io/to_kindle?action=open&asin=B08528HRYZ&location=34954)) %% Color: yellow %% ^61947413

---

root.dir in knittable documents ([43692](https://readwise.io/to_kindle?action=open&asin=B08528HRYZ&location=43692)) %% Color: yellow %% ^61947414

---

opts_knit$set(root.dir = "/example-project/analysis") ([43692](https://readwise.io/to_kindle?action=open&asin=B08528HRYZ&location=43692)) %% Color: yellow %% ^61947415

---

Note: In general it is preferable to use the knittable fle’s default directory and fle paths relative to it rather than manually specifying root.dir(). Setting an alternate root directory will make reproducibility more diÿcult. ([43692](https://readwise.io/to_kindle?action=open&asin=B08528HRYZ&location=43692)) %% Color: yellow %% ^61947416

---

mkdir ([45439](https://readwise.io/to_kindle?action=open&asin=B08528HRYZ&location=45439)) %% Color: yellow %% ^61947417

---

Organize Your Data Gathering: Makefles ([59422](https://readwise.io/to_kindle?action=open&asin=B08528HRYZ&location=59422)) %% Color: yellow %% ^61947418

---

Using GNU Make does require learning some more new syntax. However, it has one very clear advantage: it only runs a source code fle that has been updated since the last time you ran the makefle. This is very useful if part of your data-gathering process is very computationally and time intensive. ([59857](https://readwise.io/to_kindle?action=open&asin=B08528HRYZ&location=59857)) %% Color: yellow %% ^61947419

---

Segmenting your data gathering into modular fles and tying them with some sort of makefle allows you to more easily navigate research text and fnd errors in the source code. The makefle’s output is the data set that you’ll use in the statistical analyses. There are two types of source code fles that the makefle runs: data gathering/cleanup fles and merging fles. Data cleanup fles bring raw individual data sources into R and transform them so that they can be merged with data from the other sources. Many of the R tools for data cleanup and merging will be covered in Chapter 7. In this chapter, we mostly cover the ways to bring raw data into R. Merging fles are executed by the makefle after it runs the data gathering/cleanup fles. It’s a good idea to have the source code fles use very raw data as input. Your source code should avoid directly changing these raw data fles. Instead, changes should be put into new objects and data fles. Doing this makes it easier to reconstruct the steps you took to create your data set. Also, while cleaning and merging your data you may transform it in unintended ways, for example, accidentally deleting some observations that you wanted to keep. Having the raw data makes it easy to go back and correct your mistakes. ([59858](https://readwise.io/to_kindle?action=open&asin=B08528HRYZ&location=59858)) %% Color: yellow %% ^61947420

---

cache If you want to run a code chunk once and save the output for when you knit the document again, rather than running the code chunk every time, set the option cache=TRUE. When you do this the frst time the document is knitted, the chunk will be run and the output stored in a sub-directory of the working directory called cache. When the document is subsequently knitted, the chunk will only be run if the code in the chunk changes or its options change. This is ([77772](https://readwise.io/to_kindle?action=open&asin=B08528HRYZ&location=77772)) %% Color: yellow %% ^61947421

---

very handy if you have a code chunk that is computationally intensive to run. The cache option is set to FALSE by default. Later in this chapter (Section 8.4), we will see how to use the cache.vars function to cache only certain variables created by a code chunk. dependson Cached chunks are only rerun when their code changes. Sometimes one chunk will depend on the results from a prior chunk. In these cases, it is good to rerun the chunk if the prior chunk one is also rerun. The dependson option allows you to do this automatically. You can specify either a vector of the labels for the chunks depended on or their numbers in order from the start of the document. For example, dependson=c(2, 3) specifes that if the second or third chunks are rerun, then the current chunk will also be rerun. cache.extra Sometimes to ensure reproducibility, it may be useful to rerun a chunk when some other condition changes, such as when a new version of R is installed or a dependent fle changes. You can feed a list of conditions to cache.extra to do this. For instance: cache.extra=list(file.info(data.csv)$mtime, R.version) Here we set two conditions under which the chunk will be rerun. The frst specifes that the chunk should be rerun whenever the data.csv fle is modifed. The file.info function extracts information about the fle and mtime gives the last time that the fle was modifed. If this di˙ers from when the chunk was last run, then it will be run again. This is very useful for keeping your cached chunks and the fles they rely on in sync. The second condition enabled by R.version reruns the chunk whenever the R version or even the operating system changes. If you only want to rerun the chunk when the version of R is di˙erent, then use R.version.string. ([78207](https://readwise.io/to_kindle?action=open&asin=B08528HRYZ&location=78207)) %% Color: yellow %% ^61947422

---

8.2 Dynamically Including Modular Analysis Files ([79519](https://readwise.io/to_kindle?action=open&asin=B08528HRYZ&location=79519)) %% Color: yellow %% ^61947423

---

...cache.vars If the code chunk you want to cache creates many objects, but you only want to save a few of them, you can use knitr’s cache.vars chunk option. Simply give it a character vector of the objects’ names that you want to save. ([82139](https://readwise.io/to_kindle?action=open&asin=B08528HRYZ&location=82139)) %% Color: yellow %% ^61947424

**Note: Knitr's cache.vars chunk option.**

---

In this chapter we covered in more detail key knitr syntax for including code chunks in our presentation documents. This and other tools we learned in this chapter are important for tying our statistical analyses directly to its advertising, i.e. our presentation documents. In the next two chapters, we will learn how to take the output from our statistical analysis and, using knitr, present the results with dynamically created tables and fgures. ([82140](https://readwise.io/to_kindle?action=open&asin=B08528HRYZ&location=82140)) %% Color: yellow %% ^61947425

---

9.3.6 Creating variable description documents with xtable ([91752](https://readwise.io/to_kindle?action=open&asin=B08528HRYZ&location=91752)) %% Color: yellow %% ^61947426

---

In the frst line we use the names() function to create a vector of the swiss data frame’s column names. Then we create a vector of descriptions with the combine function (c()). Now we can combine these vectors into a matrix and use it to create an HTML table. ([92188](https://readwise.io/to_kindle?action=open&asin=B08528HRYZ&location=92188)) %% Color: yellow %% ^61947427

---

For the HTML version of the document we do not want a table of contents as we set toc: no. We specifed a CSS theme called Flatly for our HTML document using theme: "flatly". As of this writing, rmarkdown has a built-in ability to use a range of themes from Bootswatch (https://bootswatch.com/). Alternatively, you can link to a custom CSS fle with the css option. Use html_document to see other options. Notice that we can use no and yes instead of false and true, respectively. We linked to two BibTeX fles with the bibliography option. Using Pandoc syntax, the references will apply to both the PDF and HTML documents. If you want to also enable the creation of a Microsoft Word document, include output: word_document in the header. ([117092](https://readwise.io/to_kindle?action=open&asin=B08528HRYZ&location=117092)) %% Color: yellow %% ^61947428

---

Bibliographies with Pandoc Pandoc via rmarkdown allows us to insert citations from normal BibTeX fles (see Chapter 11) specifed in the header with bibliography. The main di˙erence is that Pandoc has a di˙erent syntax from LaTeX for making in-text citations. Basic Pandoc citations begin with @ followed by the BibTeX citation key. Square brackets ([]) create parentheses around the citation. Here is an example: This is a citation \[@donoho2009]. Pandoc uses natbib by default, so the citation [@donoho2009] will appear as (Donoho et al., 2009). To add text before and after the citation inside of the parentheses, use something like this: [see @donoho2009, 10]; which creates: (see Donoho et al. 2009, 10). If you do not want the parentheses around the entire citation (only the year) then omit the square brackets. To include only the year, and not the authors’ surnames, add a minus sign, e.g. [-@donoho2009]. See the table above for more options. Full bibliographic information for each item that is cited in the text will be produced at the end of the output document. I suggest placing a heading like #References at the very end of your document so that the bibliography will be di˙erentiated from the document’s text. ([117093](https://readwise.io/to_kindle?action=open&asin=B08528HRYZ&location=117093)) %% Color: yellow %% ^61947429

---

Footnotes with Pandoc You can also include footnotes in documents rendered with rmarkdown by using Pandoc’s footnote syntax. In the text where you would like a footnote to be located, use: [ˆNOTE_KEY]. Then at the end of your document, place [ˆNOTE_KEY]: The footnote text. 8 NOTE_KEYs generally follow the same rules as BibTeX citation keys, so no spaces. The footnotes will be numbered sequentially when rendered. To sum up, here is an example of a document that can be rendered in HTML or PDF using R Markdown. It includes footnotes and a bibliography. ([117529](https://readwise.io/to_kindle?action=open&asin=B08528HRYZ&location=117529)) %% Color: yellow %% ^61947430

