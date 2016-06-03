---
layout: post
title: Transcript of Saving the world with Hadoop - talk at London Hadoop User Group
date: 2012-04-26 13:32
author: fran
comments: true
categories: [aws, big data week, cloud footprint, cue, follow the moon, hadoop, huguk, Uncategorized]
---
<em>This post is the transcription of a talk given in April 2012 by Francine Bennett of Mastodon C (<a href="http://www.mastodonc.com">www.mastodonc.com</a>). View the Live Carbon Ratings of the data centres <a href="http://www.mastodonc.com/dashboard">here</a>.</em>
<!--more-->

<em>[the legal bit] Our data and analysis are based on assumptions and represent opinions not facts. We aim to update our models as better data becomes available.</em>

Hi. My name’s Francine Bennett, and I’m here to talk to you about a less technical topic than usual, but one that’s still very important: how to save the world with Hadoop.

I’m the cofounder of Mastodon C, a new clean-tech company which builds green cloud computing tools, and other than that am mainly a data nerd. I used to work with Big Data at Google, using their internal MapReduce stuff, and I was very sad not to get to play with those tools any more when I left, which is why I think Hadoop is awesome. Taking that awesomeness as read, I’m going to explain some things which you can do to save the world while using Hadoop.

So, why am I talking about saving the world? It starts with this chart:

[caption id="attachment_50" align="aligncenter" width="300" caption="source: http://en.wikipedia.org/wiki/File:Global_Carbon_Emission_by_Type.png"]<a href="http://mastodonc.files.wordpress.com/2012/04/global_carbon_emission_by_type.png"><img class="size-medium wp-image-50 " title="Global_Carbon_Emission_by_Type" src="http://mastodonc.files.wordpress.com/2012/04/global_carbon_emission_by_type.png?w=300" alt="" width="300" height="217" /></a>[/caption]

This shows carbon emissions on the Y axis and time on the X axis. Most critically it shows how those emissions have exploded over the most recent decades.

Many extremely credible scientists and agencies have pointed out, with increasing urgency, that with current behaviour we’re getting locked into a carbon emissions path which is likely to lead to catastrophic global events. The latest figure on this is the International Energy Agency models, which say that we need major change by 2017 in order to keep global warming down to a we-<em>might</em>-be-OK level.
<blockquote><strong>"The world is locking itself into an unsustainable energy future which would have far-reaching consequences" </strong>

<strong>International Energy Agency, November 2011</strong></blockquote>
So what has any of this got to do with Hadoop?

That’s where this graph comes in.

[caption id="attachment_52" align="aligncenter" width="290" caption="Source: The Economist"]<a href="http://mastodonc.files.wordpress.com/2012/04/amazon-vm-growth-economist-dec10.gif"><img class="size-full wp-image-52 " title="Amazon-VM-Growth-Economist-dec10" src="http://mastodonc.files.wordpress.com/2012/04/amazon-vm-growth-economist-dec10.gif" alt="" width="290" height="281" /></a>[/caption]

As awesome as on-demand cloud services are in terms of functionality, there’s a problem with them. The data centres consume a <em>lot</em> of power, and some of the biggest facilities are running on some of the worst power sources possible. In particular, AWS’ biggest facility, in Virginia, which is estimated to hold 70% of their global servers [<a href="http://www.datacenterknowledge.com/archives/2012/03/14/estimate-amazon-cloud-backed-by-450000-servers/">source</a>], is located on a coal-heavy power grid [<a href="https://docs.google.com/a/greenpeace.org/viewer?url=http://www.greenpeace.org/international/Global/international/publications/climate/2012/iCoal/Facilities%2520Table.pdf">source</a>]. By the way, I’m focussing on AWS for this talk, but the points I’m making apply to all providers.

The chart above shows the explosion of use of Amazon Web Services; the number of virtual machines on AWS is roughly tripling each year. If you are using Hadoop at scale, you may well be using Elastic MapReduce on AWS; you’re almost certainly using some kind of public cloud facility, as it’s the most sensible way to access large clusters of machines for a short time, and do the really super high powered Big Data stuff that you need to do.

[caption id="attachment_54" align="aligncenter" width="300" caption="Copyright Bruno and Ligia Rodrigues"]<a href="http://mastodonc.files.wordpress.com/2012/04/299545533_d44a4e8007_b.jpg"><img class="size-medium wp-image-54 " title="Coal fired power plant" src="http://mastodonc.files.wordpress.com/2012/04/299545533_d44a4e8007_b.jpg?w=300" alt="" width="300" height="201" /></a>[/caption]

Carbon footprint is not something which most public cloud providers are keen to discuss. Dirty energy often doesn't cost much, and power is one of the biggest costs of a data centre, so it can be good for the P&amp;L to run on dirty energy. Instead, many providers would much prefer to keep ‘green’ discussion on the topic of efficiency and PUE (power usage effectiveness), which describes the proportion of a data centre’s power usage which goes directly into powering the servers, and which aligns pretty closely with their costs. The thing is, being power-efficient is not the same thing as being green. If you run an uber-efficient data centre on coal, it’s still an environmental calamity. If you run it on something like geothermal power, the power consumption and the cost of operation can be similar, but the environmental profile totally different.

[caption id="attachment_55" align="aligncenter" width="300" caption="Copyright ThinkGeoEnergy"]<a href="http://mastodonc.files.wordpress.com/2012/04/4473295553_75678832d1_b.jpg"><img class="size-medium wp-image-55 " title="Geothermal energy plant" src="http://mastodonc.files.wordpress.com/2012/04/4473295553_75678832d1_b.jpg?w=300" alt="" width="300" height="225" /></a>[/caption]

So, the carbon footprint of a server is determined by a number of independent multipliers: physical design of the data centre, environment around it - in a hot and humid environment, a compute job can require up to twice as much energy as the server needs to be cooled, and the other factor that I’m highlighting here and which providers prefer not to expose, the power source.

There are three reasons why this is particularly relevant to Hadoop users:
<ul>
	<li>Hadoop work is intermittent anyway, so nothing breaks if you point it to a different place - jar files are standard and portable</li>
	<li>Hadoop jobs are typically not as latency-sensitive as something like web-hosting, which means that you have more choice of where to run them - you don’t need to use the closest facility</li>
	<li>A big map/reduce job uses a <em>lot</em> of machines - typical cluster size of around 30, and some people are going up to cluster sizes of hundreds. Next I’ll get onto what that number of machines represents in terms of energy.</li>
</ul>
As an individual in the UK, your personal annual carbon footprint is about 11 tonnes. A large server draws up to half a kilowatt of direct power and up to an additional half kilowatt in cooling, and the emissions related to this power usage depend on the power source. [server and cooling power estimates vary. <a href="http://msdn.microsoft.com/en-us/library/dd393312.aspx">Example source</a>, <a href="http://www.infoq.com/articles/power-consumption-servers">Example source</a>]

If we take AWS Virginia in US East, the most common location, as our baseline, we estimate using these figures that your personal emissions equate to those of <strong>3 servers</strong> running fulltime in Virginia.

Staying within AWS, let’s take a look at Oregon in US West, which is priced identically to US East. Using data on the energy grid there, we estimate that Oregon’s emissions are more than 3x lower, so that same personal footprint equates to an estimated <strong>11 servers</strong> in the Oregon zone.

So, as an individual orchestrating large Hadoop clusters, you can see that you have a way bigger impact by making informed choices about where to send compute work, than by making any amount of change to your personal life.

Looking further afield, there are also totally renewables-powered providers such as <a href="www.greenqloud.com">Greenqloud</a> available, which in a sense would make this chart give you infinitely many servers in ratio to your personal footprint. However, right now they don’t have a tool like Elastic MapReduce available, which makes anything non-AWS unattractive to many Hadoop users, and is why I'm focussing on Amazon in particular.

So, here’s a full ratings picture of Amazon locations, ranked by estimated emissions per server hour. Amazon are extremely quiet about anything to do with their power draw or carbon footprint, so we’ve calculated this using data on those power grids [<a href="www.amee.com">source</a>] and from public data on server power usage. As you can see, Virginia, the most popular location, is right up at the top end for modelled emissions. As I pointed out earlier, Oregon’s down nearer the bottom. You’ll also notice that we have both a ‘hot’ and a ‘cold’ rating for each place. These represent the modelled emissions for the maximum local temperature - summer daytime, pretty much - and the minimum local temperature - midnight in winter. As you can see from this, there’s also carbon value in ‘following the moon’. We also just launched a live ratings model using current temperatures for all of these on our <a href="http://www.mastodonc.com">website</a>, so please make use of that.
<p style="text-align:center;"><a href="http://mastodonc.files.wordpress.com/2012/04/2012_04_22_hadoop_ug_slides_1.png"><img class="size-full wp-image-58 aligncenter" title="2012_04_22_Hadoop_UG_slides_" src="http://mastodonc.files.wordpress.com/2012/04/2012_04_22_hadoop_ug_slides_1.png" alt="" width="519" height="320" /></a></p>
The thing that’s really exciting about this situation, is that people have written speculatively and done academic work on ‘follow the moon’, green compute grids and so on for a number of years, but this is the first time it’s been realistic to make it happen for the vast majority of users. Because of the global ubiquity of cloud resources, it’s become almost trivial to shift compute work around, particularly if you already have your data backed up to a number of zones - which is in any case good practice for business continuity.

Not only is it easy, it’s also inexpensive to make different choices - this chart shows the cost vs estimated emissions, again just covering AWS. As you can see, Oregon and Virginia are equally priced, with Oregon having much lower estimated emissions, so if you're locked into AWS with immobile data, I’d urge you to at least choose Oregon  as your default. If your processing is more mobile, please ping our API for live ratings on where to send jobs, and please let us know if there are other providers you'd like us to add to the list. And if you can contribute additional data to this effort, please let us know - it's very hard for us to get direct access to accurate information from inside the providers' walls, for the reasons I mentioned before, so we would like to use shared expertise to improve our precision.
<p style="text-align:center;"><a href="http://mastodonc.files.wordpress.com/2012/04/2012_04_22_hadoop_ug_slides_2.png"><img class="size-full wp-image-59 aligncenter" title="2012_04_22_Hadoop_UG_slides_2" src="http://mastodonc.files.wordpress.com/2012/04/2012_04_22_hadoop_ug_slides_2.png" alt="" width="519" height="307" /></a></p>
Before I finish, I’m just going to zoom back out again and give you a sense of the overall potential scale of this. IT was responsible for 2% of the world’s carbon footprint in 2007, and that is projected to double to 4% by 2020 [<a href="http://www.environmentalleader.com/2008/06/21/smart-2020-it-could-cut-global-emissions-15-saving-800-billion/">source</a>]. At the same time, it’s projected by some that 50% of the world’s data will be stored and processed in Hadoop by 2017. Let’s say we could knock off ¼ from those 4% IT emissions - not such a crazy assumption, given that just within a single provider’s locations we calculate a greater than 10x range in emissions, and as we’ve discussed Hadoop is highly portable. Then that would mean 1% reduction in global emissions. That’s a pretty huge deal.

So, here’s what I’d like you to take away from today:
<ul>
	<li>Hadoop and cloud computing are awesome, but some default settings have an ugly carbon footprint</li>
	<li>Carbon footprint and PUE are not at all the same thing. Efficient != green. If a provider tells you about their excellent efficiency and low PUE, please ask them difficult questions about their power sources.</li>
	<li>And, the main point: you, personally, have the ability to massively reduce the carbon footprint of your dev work by making informed choices of location and provider. So do it.</li>
</ul>
