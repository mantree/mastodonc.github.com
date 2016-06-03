---
layout: post
title: Hadoop vs Data Warehouses
date: 2012-08-20 10:20
author: fran
comments: true
categories: [big data, data warehousing, hadoop, hive, technology, Uncategorized]
---
A friend asked me this week what the difference is between using Hadoop and its related ecosystem for data storage and analysis, and using a traditional Data Warehouse.
<!--more-->

You might want to skip this post if you're already way ahead on this topic, but for everyone else, I thought I'd try and clarify...

<!--more-->

A <strong>Data Warehouse</strong> is a structured relational database, where you aim to collect together all the interesting data from multiple systems. When putting data into a warehouse, you need to clean and structure it at the point of insertion. This cleaning and structuring process is usually called ETL - Extract, Transform, and Load. The data warehouse approach is helpful because then your data looks clean and simple, but it is also very limiting: you're now unable to change the questions you want to ask later since the data's already been pre-processed, or to correct for errors in the ETL process. It can also get very expensive, as enterprise data warehouses are typically built on specialised infrastructure which becomes very pricey for large datasets. There's a nice diagram of a full data warehouse structure on <a href="http://en.wikipedia.org/wiki/Data_warehouse">the Wikipedia article here</a>.

The <strong>Hadoop</strong> ecosystem (could also be called the 'Big Data' approach) starts from the same aim of wanting to collect together as much interesting data as possible from different systems, but approaches it in a radically better way. With this approach, you dump all data of interest into a big data store (usually HDFS - Hadoop Distributed File System). This is often in cloud storage - cloud storage is good for the task, because it's cheap and flexible, and because it puts the data close to cheap cloud computing power. You can still then do ETL and create a data warehouse using tools like Hive if you want, but more importantly you also still have all of the raw data available so you can also define new questions and do complex analyses over all of the raw historical data if you wish. The Hadoop toolset allows great flexibility and power of analysis, since it does big computation by splitting a task over large numbers of cheap commodity machines, letting you perform much more powerful, speculative, and rapid analyses than is possible in a traditional warehouse.

One of the most confusing things in this field is naming - one man's data warehouse is another man's data store - so I'm sure I'll get some corrections from people who use different terminology from that above. However, I hope this does untangle things at least a little bit.
