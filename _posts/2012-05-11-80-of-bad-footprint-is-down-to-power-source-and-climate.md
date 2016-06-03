---
layout: post
title: 80% of bad footprint is down to power source and climate
date: 2012-05-11 18:03
author: fran
comments: true
categories: [cloud footprint, cue, green power, pue, Uncategorized]
---
I've heard some very confident but completely conflicting claims lately about what is 'the important thing' in the carbon footprint of compute jobs. The dissonance was starting to get to me, so I've done some back-of-envelope calculations of different scenarios to figure out what the order of importance of the factors actually is. I soft-pedalled the impact of power source as much as possible, since a priori I thought that was the most important one and I didn't want to be biased.
<!--more-->

The results were really interesting, and not only because they show that I'm right :)

<strong>60% of a bad footprint is down to power source, and 20% is down to climate.</strong> The remainder is factors like physical design and occupancy; ironically, those smaller ones are the factors that people tend to highlight when talking about 'green' data centres. This waterfall chart breaks it down:

<a href="http://mastodonc.files.wordpress.com/2012/05/rplot.png"><img class="aligncenter size-full wp-image-99" title="Waterfall chart from bad to good footprint" src="http://mastodonc.files.wordpress.com/2012/05/rplot.png" alt="" width="519" height="424" /></a>

Here's how I calculated the numbers shown in the chart - these are all approximations, but I'm confident they're in the right ballpark. I would be particularly interested to hear any adjustments to the model that you'd make.

Start with a good footprint baselined at <strong>1</strong>

PUE of different physical designs: Good case 1.2 (this is very good: the superstar PUE from OpenCompute is claimed as 1.08) bad case 1.9 (this is very bad since we're assuming no climate or occupancy impact yet)

Physical design PUE impact 1.9/1.2<strong> = 1.58</strong> times impact<strong> </strong>

Occupancy: very good case 100%, bad case 50% (assuming a fairly good worst case as a public cloud operator with very low occupancy is probably going to go out of business). Impact <strong>1.22 </strong>times, read off from chart at the British Computer Society Data Science Simulator http://dcsg.bcs.org/welcome-dcsg-simulator

Cold and dry to hot and humid climate <strong>2.0</strong> times impact - assume massive extra air conditioning load

Power source assume bad case UK power grid, good case Sweden power grid. Deliberately understimated this one (e.g. many US regions are much worse than UK, and Iceland is much better than Sweden) to make sure I don't overstate the case. <strong>8.0</strong> times impact according to Defra international energy figures.

Overall bad footprint 1 * 1.58 * 1.22 * 2.0 * 8.0 = <strong>30 </strong>times worse than the starting 'good' case.

To convert multiplicative impacts into percentage shares, take logarithms.

End result:

<strong>61%</strong> is down to power source

<strong>20%</strong> climate

<strong>13%</strong> physical PUE factors

<strong>6%</strong> occupancy

That's some pretty dramatic stuff - and it means, thankfully, that our model of estimating footprints based on external climate and power source data without always having access to physical PUE and occupancy data is heading the right way. Good news for us - we can indeed have a big impact with carbon ratings without the big providers playing ball!

Thoughts, comments, very welcome.
