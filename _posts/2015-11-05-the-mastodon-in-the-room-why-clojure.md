---
layout: post
title: "The Mastodon in the room: Why Clojure?"
date: 2015-11-05 10:16
author: antony
comments: true
categories: [Uncategorized]
---
Mastodon C advertises itself as a 'Clojure shop' when talking to clients and partners, but let's delve a bit deeper into what this means and why we believe it's a key advantage for us. Ultimately, it comes down to a <strong>simple</strong> idea:
<!--more-->
<blockquote>"Simplicity is hard work. But, there's a huge payoff. The person who has a genuinely simpler system - a system made out of genuinely simple parts, is going to be able to affect the greatest change with the least work. He's going to kick your ass. He's gonna spend more time simplifying things up front and in the long haul he's gonna wipe the plate with you because he'll have that ability to change things when you're struggling to push <del>elephants</del> mastodons around."
- <strong>Rich Hickey, Creator of the Clojure programming language</strong> (edited for effect)</blockquote>

<h2>Clo-what?</h2>
<img class="aligncenter" style="box-shadow:none;" src="http://java.ociweb.com/mark/clojure/images/clojure.png" alt="" width="396" height="116" />
<a href="http://clojure.org/">Clojure</a> is a computer programming language that promotes simplicity, whilst simultaneously being incredibly powerful and broad. It hails from a <em>family</em> of languages known as LISPs (<strong>Lis</strong>t <strong>P</strong>rocessor), which are famous for their distinctive, fully parenthesized <a title="Polish notation" href="https://en.wikipedia.org/wiki/Polish_notation">Polish prefix</a> notation. It looks a bit like this...
<pre>(require '[clojure.string :as string])
(defn say-hello [name]
  (-&gt;&gt; name
       (string/capitalize)
       (println "Hello")))

#=&gt; (say-name "archibald")
"Hello Archibald"</pre>
If you've ever seen code from other languages, such as JavaScript or Python, you'll notice immediately that this is aesthetically very different. However, like any programming languages, once you've learnt the nuances and the idioms, writing code that is concise yet expressive becomes quite straight-forward. Clojure is especially geared toward a style of programming known as <em>declarative</em>, whereby a programmer, rather than solve problems imperatively ("do this, then this") is more descriptive ("change this data to look like this"), allowing the underlying language and/platform (<a href="https://en.wikipedia.org/wiki/Java_virtual_machine">the JVM</a> in Clojure's case) to do the heavy-lifting. The result is often much less actual code - and the less code there is, the less there is to go wrong!

Clojure is predominantly used as a 'server' language which means that it's usually the workhorse at the bottom of a technology stack, doing all of the business logic, logging, management and logistics. This suits us quite nicely, as this is where most of the Mastodon C magic tends to happen -  reading in data, crunching lots of numbers, managing distributed computations across the cloud. Having all of our solutions written in Clojure means that we significantly reduce the effect of "silo-ing" people into specific projects. One person can easily move between jobs and this is something we actually mandate as part of our support process.
<h2>Pretty things</h2>
Recently there has been a big movement to bring Clojure to more platforms. Where once it was almost exclusively big, beefy servers, Clojure is now also available in your browser via <a href="https://github.com/clojure/clojurescript">ClojureScript</a> - a near-perfect reproduction of the Clojure language which <em><a href="https://en.wikipedia.org/wiki/Source-to-source_compiler">transpiles</a></em> to JavaScript. This opens up a vast amount of opportunities for development across browser, mobile and desktop, as well as allowing seamless integration with lots of powerful and popular JavaScript libraries - such as <a href="https://github.com/omcljs/om">React</a>, <a href="https://github.com/ibdknox/jayq">jQuery</a>, <a href="https://github.com/dribnet/strokes">D3</a> and <a href="http://cljsjs.github.io/">many more</a>. It's completely possibly now to write entire client-side web applications using ClojureScript - <a href="https://www.youtube.com/watch?v=LNtQPSUi1iQ">and many have</a>.

Considering Mastodon C is already bursting with experienced Clojure developers, using ClojureScript for our frontend work is a total no-brainer, and of course comes with the added benefit that - once again - no one is left-behind when it comes to rolling up their sleeves and contributing to the code. There is no "server team" and "frontend team" as is so typical at most polyglot organisations - everyone does everything.
<img class="aligncenter" style="box-shadow:none;" src="http://d3310hm27mievn.galaxant.com/000/029/327/hugging_animals_08.jpg" alt="" width="375" height="252" />
<h2>Once more, with feeling</h2>
It's important to note that although our preference lies firmly in Clojure and ClojureScript, we aren't scared of cutting our teeth on other languages, especially if they are designed for and excel at a specific task - R is a good example of this. However, the benefits of working in a predominantly Clojure organisation are paying dividends for us:
<ul>
	<li><a href="http://blog.mastodonc.com/2015/03/15/handoffs-considered-expensive/">Expensive handoffs between teams and skill bottlenecks are reduced because anyone can work on anything, most of the time</a>.</li>
	<li>Clojure can leverage a huge set of libraries from both its own ecosystem and also that of Java.</li>
	<li>The programs we write are simple, concise, easy to maintain and trivial to test; the bug count is low, the productivity is high.</li>
	<li><a href="http://www.itworld.com/article/2693998/big-data/clojure-developers-are-the-happiest-developers.html">Our developers are happy</a> and that counts for a lot!</li>
</ul>
<h2>Further reading/listening</h2>
<ul>
	<li><a href="http://www.infoq.com/presentations/Simple-Made-Easy">Simple Made Easy</a> - Rich Hickey</li>
	<li><a href="https://www.youtube.com/watch?v=MTawgp3SKy8">ClojureScript: Lisp's Revenge</a> - David Nolen</li>
	<li><a href="http://blog.venanti.us/why-clojure/">Why Clojure? </a>- Venantius</li>
	<li><a href="http://clojure.org/rationale">Clojure Rationale</a></li>
</ul>
