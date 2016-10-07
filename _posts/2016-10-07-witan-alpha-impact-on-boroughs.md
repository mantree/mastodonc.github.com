---
layout: post
title: Breaking down silos around demographic data and models - experience of a city’s local authorities
date: 2016-10-07 12:00
author: sunny
comments: true
categories: [bsps, demography, talks, videos]
---
Earlier this year we built a web-based interface for London’s local authorities (known as ‘boroughs’) to run their own population projections. Six months on we review their experience.
<!--more-->

## The scene
School rolls projections are used by London boroughs to apply for critical funding to support the building of new schools.

Each borough has unique demands because each has a different population profile due to differences in migration, ethnicity, affluence, housing development etc. While some boroughs work closely with the Greater London Authority (GLA) to generate bespoke projections that best reflect their borough’s circumstances, others have little interaction and rely on the GLA to make decisions around data and model configuration inputs.

## What we did
We worked with the GLA to provide the London boroughs with a way to run their own population projections.

The projections are based on housing development assumptions, use the GLA’s demographic models and run on Mastodon C’s platform Witan. We worked closely with the GLA to meet their requirements that the software was self-service, robust and customisable.

Providing the model through Witan has led to 3 fundamental changes to how the boroughs engage in the population projection process:

In the original system...|In the new system...|What impact did the new system have?
--- | --- | ---
GLA configured the population projection model|Borough configures population projection model|Boroughs able to test scenarios and sensitivity to assumptions
Boroughs could default to the GLA providing future housing data|Boroughs actively choose what to use as future housing data|Increased communication within the borough, particularly with the planning department
Data template optional|Data template enforced through software|Realised problems with the data quality - now being chosen and cleaned by the people who know that data best


The key benefit of all of these effects is a population projection for each borough that will better reflect their unique circumstances, helping them obtain the funding they need to meet the specific demands they each face.

You can [listen to the talk on which this blog post is based](https://youtu.be/yBKKFXz9Gog), which was given at the [British Society for Population Studies](http://www.lse.ac.uk/socialPolicy/Researchcentresandgroups/BSPS/Home.aspx) Annual Conference on 14 September 2016.
