---
layout: post
title: Hive pain reduction tricks
date: 2012-08-05 14:53
author: fran
comments: true
categories: [big data, data science, hadoop, hive, Uncategorized]
---
Hive is a SQL-like interface onto Map Reduce. It feels nice and familiar to analysts who are used to thinking in a SQL paradigm, but it has some nasty gotchas that can make jobs verrrrrry slow or make them fail altogether. Either way, you waste a lot of time, blood pressure, and machine hours.
<!--more-->

I went to a great talk recently by Philip Tromans at the London Hive meetup which covered some very useful Hive Optimisation tips. His full deck is <a href="https://speakerdeck.com/u/philiptromans/p/hive-optimisation-tips-tricks">here</a>, but I've shamelessly recopied a couple of the most useful points here:<img title="More..." src="http://wordpress.com/wp-includes/js/tinymce/plugins/wordpress/img/trans.gif" alt="" />

<!--more-->
<ol>
	<li><strong>Avoid NULLs in join fields.</strong> The field that you're joining on gets hashed and then the hash mod (some value) determines which reducers the job goes to. NULL values all get sent to the same reducer, which is usually pointless and is time consuming if there are a lot of NULL values. Push a non-null condition into the join to make things go much faster, i.e. instead of "A join B on (A.id=B.id)", do "A join B on (A.id=B.id and B.id IS NOT NULL)"</li>
	<li><strong>Use map-side joins and order join tables well. </strong>There is a default which is set to 'off' which selects the optimal join. If you precede your query with 'SET hive.auto.convert.join=TRUE;' then it will do a map-side join where appropriate, which can make things much faster. Also, joins happen one at a time, left to right, and joining to a big table is expensive, so use sub-joins to minimise size of join.</li>
	<li><strong>There are a bunch of other useful defaults</strong> in conf/hive-default.xml.template. Taking a look at these, and setting the ones you like to TRUE, will save an awful lot of unnecessary woe.</li>
</ol>
I'd recommend reading his whole deck to get some more insight.
