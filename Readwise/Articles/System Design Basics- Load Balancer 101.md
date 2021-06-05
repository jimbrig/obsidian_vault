%%
ID: 6528513
Updated: 2021-05-13
%%
![](https://readwise-assets.s3.amazonaws.com/static/images/article2.74d541386bbf.png)

# About
Title: [[Readwise/Articles/System Design Basics- Load Balancer 101]]
Author: [[Ashis Chakraborty]]
Category: #articles
Number of Highlights: ==5==
Last Highlighted: *2020-12-03*
Readwise URL: https://readwise.io/bookreview/6528513
Source URL: https://medium.com/p/adc4f602d08f


# Highlights 
Round Robin: This is one of the most common load balancing methods. It’s a method where the LB redirects incoming traffic between a set of servers in a certain order. Check figure 2; there is a list of five servers; the first request goes to server 1, the second one goes to server 2, and so on. When LB reaches the end of the list, it starts over at the beginning, from server number 1 again. It almost evenly balances the traffic between the servers. But in this method, server specifications are not considered. The servers need to be of equal specification for this method to be useful. Otherwise, a low processing powered server may have the same load as a high processing capacity server.  ^116204046

---

Random selection: In this method, the servers are selected randomly. There are no other factors calculated in the selection of the server. There might be a problem with some of the servers sitting idle, and some are overloaded with requests in this technique.  ^116204047

---

The load balancer is a server that usually sits between client devices and a set of servers and distributes client requests across servers. Load balancers can be placed in various places of a system. The loads on the servers need to be distributed in a balanced way; that’s why they are called a load balancer  ^116204048

---

Its primary purpose is to optimize the response time of each task. Now let’s assume a system has one server that is overloaded with the request of clients. The server has a limit of serving requests per second. So, we need to add more servers to handle large amounts of requests. But we may need a load balancer to balance the loads between the servers.  ^116204049

---

According to Wikipedia, “Load balancing refers to the process of distributing a set of tasks over a set of resources.”  ^116204050

