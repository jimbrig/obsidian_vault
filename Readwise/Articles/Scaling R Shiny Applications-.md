%%
ID: 6401239
Updated: 2021-05-13
%%
![](https://readwise-assets.s3.amazonaws.com/static/images/article1.be68295a7e40.png)

# About
Title: [[Readwise/Articles/Scaling R Shiny Applications-]]
Author: [[Siva Anne]]
Category: #articles
Number of Highlights: ==5==
Last Highlighted: *2020-11-24*
Readwise URL: https://readwise.io/bookreview/6401239
Source URL: https://medium.com/p/b32d56b24f03


# Highlights 
R and Shiny are popular tools to analyze data and visualize insights quickly. The single-threaded implementation of open-source R kernel constrains the scalability of R Shiny applications. Scaling R Shiny applications with commercial offerings may incur high licensing costs. The cloud-native implementation offers a cost-efficient solution to scale R Shiny applications.  ^113155386

---

The R Shiny application can be scaled using a cloud-native architecture. Typically the nexts step are:  ^113155387

---

Package the application code, its dependencies, and R Shiny Server for runtime into a Linux Docker image.  ^113155388

---

Deploy the containerized application to a Kubernetes cluster and configure to run multiple replica instances.  ^113155389

---

Configure a load balancer service to distribute the incoming requests across the collection of pods  ^113155390

