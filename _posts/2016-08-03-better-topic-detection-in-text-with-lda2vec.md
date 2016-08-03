---
layout: post
title: Better topic detection in text with LDA2VEC
date: 2016-08-03 12:00
author: elise
comments: true
categories: [data science, technology, geeky]
---
At Mastodon C we're always keeping an eye out for new libraries or data science techniques which might help us make our models faster or smarter. We very often need to work with large collections of text documents for our clients - all sorts of very useful insights can be extracted from the unstructured material that gets collected all the time in reports, notes, emails, or support tickets, as long as we can figure out how to put it to work.
<!--more-->

One of the most common needs is topic recognition. Companies having a large body of documents want to classify each document as covering a certain number of topics, with some quantitative measure of how important that topic is. This could be for market analysis, such as social media, or for a good overview and classification of their own document stores.

As with most machine learning you can choose an unsupervised or supervised approach. Unsupervised means you let the algorithm round up the topics for you instead of presetting them yourself. Unsupervised is usually a good initial approach, as it’s not always clear which topics can be expected.

This post from here onwards gets into lots of geeky detail about a new-ish technique called lda2vec - dive in if you're feeling brave...

## What sort of ML is this?

For those who are not very familiar with machine learning algorithms, a common pattern you’ll find in many of them:

- determine desired representation of data (features)
- determine objective function: what do we want to maximize or minimize to have the best possible result? This step and previous one are interdependent.
- determine how good our result has to be
- determine iterative steps to take to improve our objective function
- run until desired criteria have been achieved or the objective function is no longer improving
- depending on result, tune, apply techniques to avoid mistraining, and rinse and repeat

A little bit more background is in order, since LDA2Vec aims to mix the best of two techniques to produce a better result: Latent Dirichlet Allocation and Word2Vec

## Background

### Latent Dirichlet Allocation aka LDA

This is a way to find topics in models based on Bayesian stats.

The intuition is that each document is a mixture of various topics, and every word is assigned to a topic. We try to find topics.

We decide beforehand how many topics we want to discover (this can be tuned later if it doesn’t work out). For every word, we randomly assign each word in the document to one of the topics. Now for every word in every document we calculate the proportion of words in a document that is assigned to a topic (p(t\|d))) and the proportion of assignments of topic t over all documents from word w (p(w\|t)). We then reassign the word to a new topic (assuming for just that step that that word only was assigned to the wrong topic), where we choose topic t with max probability p(t\|d)\*p(w\|t) – and we do this for every word. Repeat several times until assignments are fairly good. Then we use these assignments to calculate the topic mixture for each documents depending on which words they contain.

The result is a set of topics that have a number of words assigned to them, and each document has a topic distribution.

The last step requires human intervention: we want to make sense of the result, we need to look at the words grouped under a certain topic, and assign a label (say "broccoli pasta banana chicken" is probably a "food" topic).

Downsides of LDA: assigning a topic is not always trivial, and if there’s no recognizable topic then the process probably needs tuning.

A second disadvantage is that it effectively sees a document as a bag of words, it doesn’t use context, how they are ordered and grouped together.

### word2vec

word2vec is a vector space model, in that it represents words as vectors with an arbitrary number of dimensions. All words are located in an x-dimensional vector space.
The underlying idea of word2vec is that if certain words are close together (euclidean distance) in many documents, they probably have a lot in common in terms of semantics (this is called the "distributional hypothesis"). Google have written a <a href="https://papers.nips.cc/paper/5021-distributed-representations-of-words-and-phrases-and-their-compositionality.html" title="Original paper by Google researchers">paper</a> on it.

It’s even the case that relationships in meaning are reflected in the vector space location, e.g. king - man + woman = queen (or country to capitals, as in the graph below)

![Picture of a PCA Chart](/assets/images/pca-pic.png "PCA image from Google original paper")

There are two main variants for word2vec, one is CBOW (continuous bag of words) which predicts a word from its context, and skip-gram which attempt to predict context words from its target. CBOW does better on small data sets, skip-gram better on large ones (<a href="https://href.li/?https://www.tensorflow.org/versions/r0.7/tutorials/word2vec/index.html">source here</a>).

Skip-Gram models uses a moving window around every word (like n words before and n words after) to have a context, so that we have an input-output tuple as follows: e.g. "the quick brown fox jumped over the lazy dog" has ([the, brown], quick) as a (context, target) tuple.

So in this case the objective function is to try to maximize the probability of "the" and "brown" given "fox" – for all words and all documents of the corpus.

Skip-gram models with negative sampling add a negative term to remove ‘noise words’, that is words that are present in all contexts but don’t add much in terms of semantics (‘stop words’ like the, a, in, etc).

All this is trained with feedforward neural networks (networks without cycles, straightforward input – projection – hidden – output layers).

This is a computationally intensive process, so much work has been done in getting clever shortcuts.

Improvements that were added in the model: using idiomatic phrases instead of words – some words should be grouped together, say the Financial Times has little to do with time measurement.

As an interesting aside: Google has the software patent for this technique, but doesn't seem to have done much with that patent at the moment.

## Lda2vec

<a href="https://github.com/cemoody/lda2vec">Lda2vec</a> is a research project by Chris E. Moody, PhD at Caltech.  Lda2vec’s aim is to find topics while also learning word vectors to obtain sparser topic vectors that are easier to interpret, while also training the other words of the topic in the same vector space (using neighbouring words).

This is achieved by changing the objective function of skip-gram negative sampling we described in previous paragraph to add document feature vectors in the mix. The intuition here is that a word is enriched by the knowledge of the document it’s embedded in: if a document is about airlines, Germany might be close to Lufthansa, while another document might evoke other associations.

The desired result is both words and document vectors, where word vectors can be added to the document vectors for meaningful results.

#### Training

The objective function is trained using stochastic gradient descent to look for minima (Adam optimizer).

At every iteration, the metric to see if we’ve achieved the right result is done by trying to find a coherence measure (with <a href="http://palmetto.aksw.org/palmetto-webapp/">Palmetto</a>, an online tool). This examines a measure over large sliding windows in the documents and checks whether the calculated probabilities of occuring for neighbouring pairs of words looks high (NPMI normalized pointwise mutual information).

#### Results

This technique was used on a corpus of bulletin board messages, and on Hacker News comments, and yielded coherent topics.

| Topic label        | "Space"           | "Encryption"  |"X-Windows"|"Middle East"
| ------------- |-------------| -----|
| Top tokens     | astronomical<br>Astronomy<br>satellite<br>planetary | encryption<br>encrypt<br>wiretap<br>escrow |mydisplay<br>xlib<br>window<br>cursor|Armenian<br>Lebanese<br>Muslim<br>Turk
| Topic coherence      | 0.712      | 0.675 |0.472|0.615



## Conclusion

This is a research project – exceptionally, it has really decent open source code in Python which is rare for research papers (props to Chris Moody). The technique looks promising, and intuitively makes sense, and the results look exciting.

Running time: on a high-spec laptop it takes multiple-days-scale scale durations to run the bulletin board example (11312 documents, 3.4GB, 20 topics) – this may be shorter when using the CUDA optimizations he uses and there's definitely room to parallellize the calculations to obtain better running times.

In short, this is definitely one to watch.
