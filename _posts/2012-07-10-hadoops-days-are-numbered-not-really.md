---
layout: post
title: Hadoop's days are numbered? Not really
date: 2012-07-10 10:57
author: fran
comments: true
categories: [big data, bigquery, data science, dremel, hadoop, hive, mapreduce, tenzing, Uncategorized]
---
GigaOm published this <a href="http://gigaom.com/cloud/why-the-days-are-numbered-for-hadoop-as-we-know-it/">interesting and provocative article</a> last week, headlined 'Why the days are numbered for Hadoop as we know it'.
<!--more-->

It's actually a pretty good argument, despite the sensational headline. The tl;dr, as I interpret it, is that:<!--more-->
<ul>
	<li>Hadoop is an excellent solution for management and processing massive datasets on commodity hardware - hence makes big data a genuinely practical cost-effective proposition, especially when compared to legacy technology</li>
	<li>However, the interactivity and low-latency requirements of much data analysis - where the analyst wants to run a bunch of speculative, ad-hoc queries in order to explore the dataset - can be a poor fit for map-reduce jobs if you're running them over a whole, extremely large dataset, since mapreduce takes a while to spin up and to return results, especially when done through an analyst-friendly but unoptimised query interface like Hive, so it clogs up the analysis workflow</li>
	<li>Google have already moved beyond the mapreduce paradigm to an approach using Dremel (exposed as the BigQuery product) to run the same types of jobs much faster</li>
</ul>
The argument stacks up if you're Google, and you have humungous amounts of data and very strict latency requirements.

However, Hadoop, MapReduce, and the related ecosystem are still going to be around as core functions for a long time (even the GigaOm article says 'at least another decade', which is forever in technology years) as they are still fundamentally good ways of processing a lot of data cheaply and effectively. Also, most datasets that people think are 'big' are really not at Google scale - so the MapReduce time penalty is not such an issue. Hadoop's still got plenty of room to grow and mature, and it's massively better than the technology that most corporations are currently running on.

All that said, I'd definitely be up for trying out an open-source version of Dremel/BigQuery as soon as someone builds it; faster queries are always nice.
