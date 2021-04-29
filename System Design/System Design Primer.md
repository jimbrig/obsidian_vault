---
creation date: 2021-04-29 11:38
modification date: Thursday 29th April 2021 11:38:32
tags: ["#dev"]
author: Jimmy Briggs
---

# System Design Primer

![](https://github.com/donnemartin/system-design-primer/raw/master/images/jrUBAF7.png)

## Performance vs scalability

A service is **scalable** if it results in increased **performance** in a manner proportional to resources added. Generally, increasing performance means serving more units of work, but it can also be to handle larger units of work, such as when datasets grow.[1](http://www.allthingsdistributed.com/2006/03/a_word_on_scalability.html)

Another way to look at performance vs scalability:

-   If you have a **performance** problem, your system is slow for a single user.
-   If you have a **scalability** problem, your system is fast for a single user but slow under heavy load.

### [](https://github.com/donnemartin/system-design-primer#sources-and-further-reading-1)Source(s) and further reading

-   [A word on scalability](http://www.allthingsdistributed.com/2006/03/a_word_on_scalability.html)
-   [Scalability, availability, stability, patterns](http://www.slideshare.net/jboner/scalability-availability-stability-patterns/)

## [](https://github.com/donnemartin/system-design-primer#latency-vs-throughput)Latency vs throughput

**Latency** is the time to perform some action or to produce some result.

**Throughput** is the number of such actions or results per unit of time.

Generally, you should aim for **maximal throughput** with **acceptable latency**.

### [](https://github.com/donnemartin/system-design-primer#sources-and-further-reading-2)Source(s) and further reading

## Availability vs consistency

### [](https://github.com/donnemartin/system-design-primer#cap-theorem)CAP theorem

[![](https://github.com/donnemartin/system-design-primer/raw/master/images/bgLMI2u.png)](https://github.com/donnemartin/system-design-primer/blob/master/images/bgLMI2u.png)  
_[Source: CAP theorem revisited](http://robertgreiner.com/2014/08/cap-theorem-revisited)_

In a distributed computer system, you can only support two of the following guarantees:

-   **Consistency** \- Every read receives the most recent write or an error
-   **Availability** \- Every request receives a response, without guarantee that it contains the most recent version of the information
-   **Partition Tolerance** \- The system continues to operate despite arbitrary partitioning due to network failures

_Networks aren't reliable, so you'll need to support partition tolerance. You'll need to make a software tradeoff between consistency and availability._

#### [](https://github.com/donnemartin/system-design-primer#cp---consistency-and-partition-tolerance)CP - consistency and partition tolerance

Waiting for a response from the partitioned node might result in a timeout error. CP is a good choice if your business needs require atomic reads and writes.

#### [](https://github.com/donnemartin/system-design-primer#ap---availability-and-partition-tolerance)AP - availability and partition tolerance

Responses return the most readily available version of the data available on any node, which might not be the latest. Writes might take some time to propagate when the partition is resolved.

AP is a good choice if the business needs allow for [eventual consistency](https://github.com/donnemartin/system-design-primer#eventual-consistency) or when the system needs to continue working despite external errors.

### [](https://github.com/donnemartin/system-design-primer#sources-and-further-reading-3)Source(s) and further reading

-   [CAP theorem revisited](http://robertgreiner.com/2014/08/cap-theorem-revisited/)
-   [A plain english introduction to CAP theorem](http://ksat.me/a-plain-english-introduction-to-cap-theorem)
-   [CAP FAQ](https://github.com/henryr/cap-faq)
-   [The CAP theorem](https://www.youtube.com/watch?v=k-Yaq8AHlFA)

-   [Understanding latency vs throughput](https://community.cadence.com/cadence_blogs_8/b/sd/archive/2010/09/13/understanding-latency-vs-throughput)

***
Links: [[System Design]] | [[Web Development]] | [[Databases]]
Source: [donnemartin/system-design-primer](https://github.com/donnemartin/system-design-primer)


