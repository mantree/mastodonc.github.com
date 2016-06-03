---
layout: post
title: Network analysis to find 'innovators'
date: 2014-01-15 14:22
author: fran
comments: true
categories: [Uncategorized]
---
We’re midway through some work with Nesta to systematically find ‘innovators’ in the UK technology scene. It’s been a really interesting project so far, and we’re looking forward to launching the work more widely in 2014.
<!--more-->

The system we’re building is collecting and joining together data from multiple sources about software developers and what they work on, the idea being to spot innovative people, innovative companies, and to understand the tech innovation landscape better than we can just using official information. “Innovative” is a pretty subjective term, but we’ve been exploring ways of identifying innovative individuals and companies by analysing their apparent importance and influence in their professional networks.

<a href="http://mastodonc.files.wordpress.com/2014/01/software_innovators.jpg"><img class="aligncenter size-full wp-image-290" alt="software_innovators" src="http://mastodonc.files.wordpress.com/2014/01/software_innovators.jpg" width="400" height="400" /></a>

Our sources are pretty varied, and aren’t usually used in official tracking. Namely, we’re finding data from:
<ul>
	<li>Github, a popular code sharing service which many programmers use to store, track, and share their projects, both public and private</li>
	<li>StackOverflow, a question and answer site for technical issues</li>
	<li>Twitter, where a lot of social chat goes on, and</li>
	<li>Open Corporates, the open database of the corporate world, which pulls together the official public data available on companies</li>
</ul>
We’re still working out what the final interface will look like - and would be really interested to hear any thoughts on what would be most useful - but we expect it to be a web-based way to identify explore innovators and their relationships by region, specialty, and maybe other factors as well. We hope that this will give a way to escape the ‘filter bubble’ of known innovators and start to spot those people and companies who are slightly under the official radar at present.

Here are five of the interesting things we’ve found so far:

1.    As in lots of other social networks, the number of followers of UK Github users follows the Pareto (80/20) principle, where 80% of followers are watching just 20% of the total users. This is handy for us, since there are a few central users and innovators who are genuinely influential

2.    Big network analysis is <em>way</em> more computationally intensive than you might guess. Because everybody can be linked to everybody else, there are lots of potential relationships to analyse: if there are only 1,000 users, there are 1,000,000 relationships, so the sums get very big very fast. In fact, there are about 15,000 UK ‘innovators’, plus their friends, who we want to look at. We’ve been working with modern open source tools including <a href="http://www.neo4j.org/" target="_blank">Neo4j</a> and <a href="https://gephi.org/" target="_blank">Gephi</a>, which are pretty good, but we’re still stretching the limits of what’s practical.

3.    Living in our own filter bubble at a technology company in Shoreditch, it’s easy to imagine that all the innovators work at small technology companies in Shoreditch. In fact, that’s off the mark: we find lots of people working for big corporations, for organisations like the BBC, and for universities.

4.    On the other hand, our filter bubble isn’t <em>too </em>bad: in our random sample of innovators, we also found a few people who we knew and who Nesta knew personally, so we’re pretty sure that we are hitting the right networks of people.

5.    Innovative people seem to have side projects; we’d initially assumed that we could link people with companies just by looking at their websites. The fact is, a lot of the innovators we identified have got their own personal websites, as well as corporate identities - they’re connected to multiple projects and not just their main employer

(cross posted from <a href="http://www.nesta.org.uk/blogs/">http://www.nesta.org.uk/blogs/</a>)
