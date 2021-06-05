%%
ID: 3078604
Updated: 2020-06-18
%%
![](https://readwise-assets.s3.amazonaws.com/static/images/article1.be68295a7e40.png)

# About
Title: [[R Tips and Tricks – Utilities]]
Author: 
Category: #articles
Number of Highlights: ==8==
Last Highlighted: *2020-06-17*
Readwise URL: https://readwise.io/bookreview/3078604
Source URL: https://eranraviv.com/r-tips-tricks-utilities/


# Highlights 
Methods are functions which are specifically written for particular class  ^66118083

---

Have a look at the sloop package, maintained by Hadley Wickham (that alone is a reason). Use the function s3_methods_generic to get a nice table with some relevant information:  ^66118084

---

Percent formatting
In the code snippet above I used the scales package’s percent function, which spares the formatting annoyance.  ^66118085

---

Get your object’s size
When I load a data, I often want to know how big is it. There is the basic object.size function but it’s ummm, ugly. Use the aptly named object_size function from the pryr package.  ^66118086

---

Memory management
Use the gc function; gc stands for garbage collection. It frees up memory by, well, collecting garbage objects from your workspace and trashing them. I at least, need to do this often.  ^66118087

---

heta function
I use the head and tail functions a lot, often as the first thing I do. Just eyeballing few lines helps to get a feel for the data. Default printing parameter for those function is 6 (lines) which is too much in my opinion.  ^66118088

---

heta <- function(x, k= 3){
cat("Head -- ","\n", "~~~~~", "\n")
print(head(x, k))
cat("Tail -- ","\n", "~~~~~", "\n")
print(tail(x, k))
}  ^66118089

---

Sound the alarm
If you stretch your model enough, you will have to wait until computation is done with. It is nice to get a sound notification for when you can continue working. A terrific way to do that is using the beepr package.  ^66118090

