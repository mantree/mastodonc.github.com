---
layout: post
title: Handoffs considered expensive
date: 2015-03-15 20:29
author: bruce
comments: true
categories: [Uncategorized]
---
It is a truth universally acknowledged, that a team of coders in possession of dependencies must be in trouble. Much of agile at scale is about reducing or eliminating the dependencies between teams, usually by making multiskilled teams (see devops et al). Since working at Mastodon C though I’ve noticed that I’ve not suffered this as much as I used to. I figured it might have just been to do with being in a startup and having escaped the madness of enterprise software and bureaucratic large companies and massive teams.
<!--more-->

However, I've noticed this pain again in some of the projects we've done, where we have dependencies on other teams to deliver either front end or back end things for us. I know the people well on the other teams and I know that they are *very* skilled, so their ability to execute isn't the problem. They do everything right. The communication levels are high and they build things that we couldn’t do ourselves.

People usually say that choice of language doesn't really affect what you are doing that much, but I feel it is making a big difference for us. From deployments, to database access, to services, to the front end we are using clojure and clojurescript. Most of our features go from the database to the front end and are delivered by one developer or a pair of developers. This is an amazing freedom.

All of our team members can do the basics, with only a few times when we need expert help on deploying, design or data science. This gives them a chance to improve on weak spots in addition to gaining more expertise. Using effectively the same language at all layers gives us this strength. I can look at code in the front end and look at code running in spark and know that there will be map/reduce/keep working on data structures where I'm going to assoc and dissoc things on a hashmap and then working on the values held there.

This means that any developer can implement a whole idea. They may need help, but they can do the vertical slice themselves and this also helps them think about the user needs as they are taking the feature all the way to the end rather than just implementing something in the backend. It also helps them think about performance and monitoring as they aren't just implementing a bit of UI.

I like working with experts. It helps us to do things better than we could have done on our own, but there is a cost to this. The cost is in waiting and communication with the expert and being blocked if they aren't available. Sometimes this cost is worth it, but I'm glad that most of the time we don't have to take on that cost and that we can usually choose when we want to.
