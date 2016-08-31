---
layout: post
title: Text Mining Defra
date: 2016-08-03 12:00
author: fhr
comments: true
categories: [data science, text mining, geeky,cows]
---
We did some interesting work a while ago with the UK’s Department for Environment, Food, and Rural Affairs, which tested the possibility of using text mining to highlight upcoming risks from incoming reports from the field.

In this blog post, we’ll dig into some of the technical details of how to do this, and why it’s interesting. A longer case study of the project is <a href="http://www.mastodonc.com/casestudies/defra/">here</a>.
<!--more-->

## Context

Monitoring and identifying emerging threats to animal health is difficult, as some of the most useful data is contained in long unstructured reports from the field, and in-house experts’ time is often too constrained to read all the incoming reports and spot new trends. This is a common problem across many businesses - there is useful information hidden in the unstructured incoming flow of documents, but not enough time for humans to extract it.

## Adding structure using topic detection

Unstructured data such as text is a challenge because in order to apply any further data science methods to it, we need to add some meaningful structure. One of the most useful ways to do this in the case of text is topic modelling, where we try and find a set of natural and human-understandable “topics” in a collection of documents (or “corpus”) (see <a href="http://www.mastodonc.com/data%20science/technology/geeky/2016/08/03/better-topic-detection-in-text-with-lda2vec.html">Elise’s blog post</a> for more detail). This gives us a set of labels for each document, and means from then on we can treat the text corpus as structured data.

We developed a new open source <a href="https://github.com/MastodonC/kixi.text.mining">kixi.text.mining</a> library to do this with Latent Dirichlet Allocation, which uses a wrapper for Mallet in Clojure.

As so often, most of the work here was actually in refining the model to make sense in the client’s particular context, in particular by building up the list of “stop words” to exclude from analysis - for example in this case, we stripped out a number of commonly mentioned places and institutions, since mentions of these didn’t give us any insight into new symptoms of disease.

## Creating alerts

Once we’d developed a good topic engine, and labelled documents into the right boxes, we could treat this as a straightforward anomaly detection problem - looking at the number of occurrences of a topic in each period, and setting off an alert for human review whenever a particular topic suddenly started to get a lot more mentions than it had in previous periods. By back-testing this against the real data, we found that the system could indeed make epidemics of new diseases visible early on in their rise, even before they had an official diagnosis or label for a disease.

## Conclusion

Text data - whether reports, emails, or just free text fields in a database - is often one of the richest untapped data sources in an enterprise, and can offer surprisingly quick wins in terms of new predictions and insights for your business. <a href="http://www.mastodonc.com/contact/">Contact us</a> if you’d like to talk more about ideas for using the text that’s sitting unused in your organisation.
