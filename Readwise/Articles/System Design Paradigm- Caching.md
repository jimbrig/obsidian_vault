%%
ID: 9301598
Updated: 2021-05-28
%%
![](https://readwise-assets.s3.amazonaws.com/static/images/article4.6bc1851654a0.png)

# About
Title: [[Readwise/Articles/System Design Paradigm- Caching]]
Author: [[Abracadabra]]
Category: #articles
Number of Highlights: ==1==
Last Highlighted: *2021-05-28*
Readwise URL: https://readwise.io/bookreview/9301598
Source URL: https://medium.com/p/e57a25ab2f0a


# Highlights 
The solution is a lease. The first cache miss will grant the app server a lease token. Only the app server having the token for a key can query DB and fill the cache. After a token is issued, all subsequent requests to the cache will be asked to retry after a period. The lease expires after a while to avoid deadlock  ^184655479

