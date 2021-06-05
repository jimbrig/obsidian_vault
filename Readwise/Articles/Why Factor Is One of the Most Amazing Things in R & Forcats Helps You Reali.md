%%
ID: 3007930
Updated: 2020-06-12
%%
![](https://readwise-assets.s3.amazonaws.com/static/images/article1.be68295a7e40.png)

# About
Title: [[Why Factor Is One of the Most Amazing Things in R & Forcats Helps You Reali]]
Author: [[Kan Nishida]]
Category: #articles
Number of Highlights: ==9==
Last Highlighted: *2020-06-11*
Readwise URL: https://readwise.io/bookreview/3007930
Source URL: https://blog.exploratory.io/why-factor-is-one-of-the-most-amazing-things-in-r-e967fe27d292


# Highlights 
R is like wine, the more you experience it, the more you appreciate what it does, how it does, and why it does. You might hit the initial learning curve, but after you overcome it, then you start feeling how it is beautifully and practically designed to address very common challenges of the everyday data analysis.  ^65137759

---

Factor data type is one of them. It is designed to address typical challenges we encounter when we work with categorical data. This data type looks like Character data type from the outset, but it can contain additional information to manage the levels and the order (or sequence) of the categorical values.  ^65137760

---

Factor data type alone separates R from other BI tools
So basically, with Factor data type, we can register the levels (number of the categories) and the orders as part of the columns (or variables) natively so that we can let the columns dictate how to handle such level and sorting information. This is a huge advantage especially comparing to other tools like Excel or typical BI tools.  ^65137761

---

A gift from God — forcats package
But the only problem is, it was not so straightforward to assemble and manage such levels and order with Factor for many of us.  ^65137762

---

In this post, I’m going to demonstrate why Factor should be your best friend and how ‘forcats’ package makes the journey of knowing Factor data type super easy and fun. I’m going to use Exploratory as a front end (UI), but obviously, you can do the same things in RStudio or other tools as well.  ^65137763

---

Set the Order of Categories based on Another Column Values  ^65137764

---

Another way is to use ‘fct_reorder’ function, which can take another column as a reference for the order, so the original data doesn’t need to be sorted beforehand.  ^65137765

---

If we want to show the US Presidents from the latest to the oldest, then we can simply use ‘fct_rev’ from ‘forcats’ package to reverse the original order we have set above.  ^65137766

---

This is when the ‘fct_lump’ function from ‘forcats’ package comes to rescue. It keeps only a top N number of the categories, in this case, that is US states, and moves everything else into an ‘Other’ bucket.  ^65137767

