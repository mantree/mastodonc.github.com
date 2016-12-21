---
layout: post
title: How we’re building a new city platform
date: 2015-09-09 17:05
author: chrisa
comments: true
categories: [Uncategorized]
---
As we mentioned <a href="http://blog.mastodonc.com/2015/08/19/witan-the-flexible-city-modelling-platform/">earlier</a> on the blog, we’re working on a very big and ambitious project to create a new city modelling platform, Witan, with London as the first test bed.
<!--more-->

Since there is so much that could be done in this field, and so many possible ways to do it, there are some tough choices for us to make, to ensure that the platform works and is widely adopted, both in London and in other world cities.

<figure>
<a href="https://mastodonc.files.wordpress.com/2015/09/simple-process.png"><img class="size-large wp-image-366" src="https://mastodonc.files.wordpress.com/2015/09/simple-process.png?w=660" alt="Oh, if only." width="660" height="372" /></a>
<figcaption>Oh, if only.</figcaption>
</figure>

We wish that new product development was predictable - a straight line from seeing a user need, to building a tool which meets that need, then selling it to lots of other similar users. Unfortunately, it’s rarely that simple or predictable.

<figure>
<a href="https://mastodonc.files.wordpress.com/2015/09/what-its-more-like.png"><img class="alignnone size-large wp-image-367" src="https://mastodonc.files.wordpress.com/2015/09/what-its-more-like.png?w=660" alt="what-its-more-like" width="660" height="372" /></a>
</figure>

There’s no easy way to make that path predictable - but we can do things which reduce the overall risk, and this is a big part of our lives at the moment. This post outlines how we’re tackling the challenge for Witan, drawing some inspiration from the stellar resources shared by the GDS with their <a href="https://userresearchmethods.hackpad.com/">user research method</a> wiki, how companies <a href="https://marcabraham.wordpress.com/2013/03/23/learning-about-how-spotify-builds-products/">like Spotify build their products</a>, and good agile (with a small A) practices.

<figure>
<a href="https://mastodonc.files.wordpress.com/2015/09/rough-stages-to-delivery.png"><img class="alignnone size-large wp-image-368" src="https://mastodonc.files.wordpress.com/2015/09/rough-stages-to-delivery.png?w=660" alt="rough-stages-to-delivery" width="660" height="372" /></a>
</figure>
<b>Understanding the problem first</b>

If we start by casting our net wide early on, we can improve our understanding of the problems our users have, to end up with a larger set of user needs.

We can’t serve every need, so we validate and prioritise which needs we want to meet with further research. <a href="https://userresearchmethods.hackpad.com/How-to-write-a-user-need-nEEabE3vm1r">At this point we focus on the problem</a>, not on how we’d solve it.

<b>Choosing the smallest way to meet a need</b>

When we  have a smaller set of needs we’re aiming to meet, we diverge again, to come up with solutions to the problems we’ve decided to target. We’d typically describe these as user stories.

<b>Checking we’ve actually solved it</b>

We choose the smallest subset of user stories possible to deliver to users, build a solution which meets those needs, and see how well it works for the users in reality. When we’re building those solutions, we use multi-skilled teams because <a href="http://blog.mastodonc.com/2015/03/15/handoffs-considered-expensive/">we want to minimise handoffs</a> between experts, and we get our team to work with directly with users in order to <a href="https://gds.blog.gov.uk/2013/08/30/how-we-do-user-research-in-agile-teams/">create a sense of empathy</a> and make sure that the technology really meets their needs.

<b>And repeat…</b>

Inside Mastodon C, we've been working in weekly iterations for a while: each week we demo what we've made, and then we plan what we'll do the following week. One key thing we're trying now, is using the mental model above to decide what activities in our 'toolbox' are most appropriate for that week.


<figure>
<a href="https://mastodonc.files.wordpress.com/2015/09/earlier-tool-selection.png"><img class="size-large wp-image-369" src="https://mastodonc.files.wordpress.com/2015/09/earlier-tool-selection.png?w=660" alt="Early on – when our focus is discovery" width="660" height="372" /></a>
<figcaption>Early on – when our focus is discovery</figcaption>
</figure>


<em>Early on - when our focus is discovery</em>

Early on in the project, most of our time is spent generating ideas, and exploring them, so we have a set of needs to validate, most of our activities are in the left hand side of our 'toolbox'.


<figure>
<a href="https://mastodonc.files.wordpress.com/2015/09/popup-testing-of-storyboards-and-sketches.png"><img class="alignnone size-large wp-image-370" src="https://mastodonc.files.wordpress.com/2015/09/popup-testing-of-storyboards-and-sketches.png?w=660" alt="popup-testing-of-storyboards-and-sketches" width="660" height="372" /></a>

</figure>

<em>A</em>s we learn more, we’ll move more of our efforts to activities in the middle, where we're validating our understanding of user's needs, and see how they currently try to solve their problems themselves. It's not uncommon for some of our team to focus on activities on the left after discovering something new, while the rest focus on the middle, on problems that we have a better understanding of. Again, we share what we learn each week in a show-and-tell like session, (<a href="http://blog.mastodonc.com/2013/09/03/what-and-why-is-democake/">but with added cake</a>).

<figure>
<a href="https://mastodonc.files.wordpress.com/2015/09/testing-html-and-production-code.png"><img class="size-large wp-image-371" src="https://mastodonc.files.wordpress.com/2015/09/testing-html-and-production-code.png?w=660" alt="Testing out a solution to a problem we feel we understand" width="660" height="372" /></a>
<figcaption>Testing out a solution to a problem we feel we understand</figcaption>
</figure>
Later on, when we're confident we understand enough of the problem to build a solution to it, we're likely to be spending most of our time on activities on the right.

That is, until we discover something interesting enough to warrant spending some time using tools from the left hand side of our toolbox again. In some cases, we might discover a killer new feature that makes sense to add to what we have built already.

In others, we might discover the beginnings of a new product that is interesting, but not key to meeting the needs of the users we're designing for right now. We'll save it for later to see if it comes up again, at which point we'll make a call about whether we should investigate further.
<h3>Well, that's the plan at least</h3>
We're working on one of the most complex problems we've ever come across, in one of the greatest cities on earth - if you'd like to see how we get on, <a href="http://witan.mastodonc.com/">watch this space</a>.
