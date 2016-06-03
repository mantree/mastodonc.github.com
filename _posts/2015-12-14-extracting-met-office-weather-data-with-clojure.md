---
layout: post
title: Extracting Met Office weather data with Clojure
date: 2015-12-14 12:03
author: jason
comments: true
categories: [Hacks, Uncategorized]
---
Living in York for the majority of my life, I've got used to flooding. With the number of floods increasing, and the probability of that flood causing long lasting damage also increasing, it would be a good idea to start peeking at past data and seeing if there's anything jumping out at us.
<!--more-->
### Getting Historical Met Office Data
The Met Office provided an open data set in 2011 on the <a href="https://data.gov.uk/data/search?q=daily&amp;publisher=met-office">data.gov.uk</a> portal. There are a number of different feed types so it's certainly worth taking the time to have a look and see which fits best for your needs. In this walkthrough I will concentrate on hourly observation data.

Historical <a href="https://data.gov.uk/metoffice-data-archive">data comes by way of a form</a> which generates a file from the data archive and sends back the data as a CSV file.

<img class="aligncenter size-large wp-image-1280" src="https://dataissexy.files.wordpress.com/2015/12/moffice.png?w=529" alt="moffice" width="529" height="366" />

The form can only deal with one date at a time, which is fine if you want one day but is rather a pain if you want to get data between two dates. With some unix scripting (using curl for example) you can easily pull the data in, but there is an issue with that. When you fire the search form, the data is pulled and then forwarded to another url with a unique id. So unless you're great at handling redirects within unix it's going to be difficult to get the data out. Well, it <em>was </em>difficult to get the data out, but now I have good news for you.
<h3>A Clojure Alternative?</h3>
The Mastodon C team created an open source project called <a href="https://github.com/MastodonC/kixi.hecuba.weather">kixi.hecuba.weather</a>, whose primary purpose is to pull historical weather data and send it up to our Hecuba platform. It's fully open source so even if you're not using Hecuba you can still use some of the component parts of k.h.w. to pull the Met Office data for your own needs.

The project is hosted on <a href="https://github.com/mastodonc/kixi.hecuba.weather">Github</a> and anyone can use it for grabbing Met Office historical weather data.
<h3>Clone The Project</h3>
First of all you need to clone the project. From the command line run the following git command from your terminal or command prompt.
<pre>git clone git@github.com:MastodonC/kixi.hecuba.weather.git</pre>
You'll see the repository download to your machine.
<pre>dev:mctemp jasonbell$ git clone git@github.com:MastodonC/kixi.hecuba.weather.git
Cloning into 'kixi.hecuba.weather'...
remote: Counting objects: 209, done.
remote: Total 209 (delta 0), reused 0 (delta 0), pack-reused 209
Receiving objects: 100% (209/209), 39.05 KiB | 0 bytes/s, done.
Resolving deltas: 100% (68/68), done.
Checking connectivity... done.
dev:mctemp jasonbell$</pre>
With that done you can now start the REPL and start running functions to pull down the data.
<h3>Starting The REPL</h3>
I'm going to first compile the k.h.d. project and then start the REPL from the command line:
<pre>dev:mctemp jasonbell$ lein compile
dev:mctemp jasonbell$ lein repl</pre>
Give it a few moments then you will see the output as the REPL starts and then the prompt. Once you have the prompt you can start working.
<pre>nREPL server started on port 55453 on host 127.0.0.1 - nrepl://127.0.0.1:55453
REPL-y 0.3.7, nREPL 0.2.10
Clojure 1.7.0
Java HotSpot(TM) 64-Bit Server VM 1.8.0_60-b27
 Docs: (doc function-name-here)
 (find-doc "part-of-name-here")
 Source: (source function-name-here)
 Javadoc: (javadoc java-object-or-class-here)
 Exit: Control+D or (exit) or (quit)
 Results: Stored in vars *1, *2, *3, an exception in *e
kixi.hecuba.weather.core=&gt;</pre>
The namespace where the Met Office functions are is called "<strong>kixi.hecuba.weather.metoffice-api</strong>", so you will need to change namespace first.
<pre>kixi.hecuba.weather.core=&gt; (ns kixi.hecuba.weather.metoffice-api)</pre>
Now we can turn our attention to retrieving the Met Office data.
<h3>Retrieving The Data</h3>
The <strong>run-data-pull</strong> function takes three parameters: a start date, an end date, and a path to save the files to. For example if I want to pull historical data from the 1st of January 2013 to the 1st of February 2013 I would run the following. The dates are entered as a <strong>dd/mm/yyyy</strong> format, so for example:
<pre>kixi.hecuba.weather.metoffice-api=&gt; (run-data-pull "01/01/2013" "01/02/2013" "/Users/jasonbell/Documents/work/projects/mctemp/")</pre>
The function will call the API and save the data for each hourly observation and then save it to the directory specified.
<pre>-rw-r--r-- 1 jasonbell staff 21427 7 Dec 13:18 01-01-2013-0000.csv
-rw-r--r-- 1 jasonbell staff 20759 7 Dec 13:18 01-01-2013-0100.csv
-rw-r--r-- 1 jasonbell staff 20690 7 Dec 13:18 01-01-2013-0200.csv
-rw-r--r-- 1 jasonbell staff 20755 7 Dec 13:18 01-01-2013-0300.csv
-rw-r--r-- 1 jasonbell staff 20734 7 Dec 13:18 01-01-2013-0400.csv
-rw-r--r-- 1 jasonbell staff 20809 7 Dec 13:18 01-01-2013-0500.csv
-rw-r--r-- 1 jasonbell staff 21328 7 Dec 13:18 01-01-2013-0600.csv
-rw-r--r-- 1 jasonbell staff 21234 7 Dec 13:18 01-01-2013-0700.csv
-rw-r--r-- 1 jasonbell staff 21312 7 Dec 13:18 01-01-2013-0800.csv
-rw-r--r-- 1 jasonbell staff 20789 7 Dec 13:18 01-01-2013-0900.csv
-rw-r--r-- 1 jasonbell staff 20673 7 Dec 13:18 01-01-2013-1000.csv
-rw-r--r-- 1 jasonbell staff 20825 7 Dec 13:18 01-01-2013-1100.csv
-rw-r--r-- 1 jasonbell staff 20812 7 Dec 13:18 01-01-2013-1200.csv
-rw-r--r-- 1 jasonbell staff 21003 7 Dec 13:18 01-01-2013-1300.csv
-rw-r--r-- 1 jasonbell staff 20888 7 Dec 13:18 01-01-2013-1400.csv</pre>
The make up of the CSV files is documented by the Met Office, here's a quick look at one of the files for your reference.
<pre>Site Code,Site Name,Latitude,Longitude,Region,Observation Time,Observation Date,Wind Direction,Wind Speed,Wind Gust,Visibility,Screen Temperature,Pressure,Pressure Tendency, Significant Weather
"3005","LERWICK (S. SCREEN) (3005)","60.1390","-1.1830","Orkney &amp; Shetland","12:00","2013-01-01","WNW","10","","14000","3.80","989","R","Light rain shower (Day)",
"3031","LOCH GLACARNOCH SAWS (3031)","57.7250","-4.8960","Highland &amp; Eilean Siar","12:00","2013-01-01","WNW","16","29","18000","3.70","997","R","Heavy Rain",
"3041","AONACH MOR (3041)","56.8200","-4.9700","Highland &amp; Eilean Siar","12:00","2013-01-01","W","17","32","","-1.20","","#","N/A",
"3063","AVIEMORE (3063)","57.2060","-3.8270","Highland &amp; Eilean Siar","12:00","2013-01-01","WSW","3","","16000","3.50","997","R","Light rain shower (Day)",
"3066","KINLOSS (3066)","57.6494","-3.5606","Grampian","12:00","2013-01-01","WSW","17","","40000","5.20","996","R","(Black) Low-level cloud",</pre>
<h3>Conclusion</h3>
The kixi.hecuba.weather service provides you with a simple method to retrieve data published from the Met Office. The ability to pull hourly data across a number of days, weeks or months into CSV files makes it perfect for placing in Hadoop's distributed file system (HDFS) enabling you to do further analysis with Hadoop or Spark for example.

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;
