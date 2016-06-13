---
layout: content-feature
client: any
title: "Kixi big data pipeline build and daily management"
subtitle:  "A&NY Media"
lowdown: "Managing and processing large volumes of daily incoming data for a £1bn-turnover consumer media organisation, making it available in a data warehouse for their analysts to query. "
logo: logo-any.png
bgimage: bg-any.jpg
download: casestudy.pdf
---
## The scene
Our client, A&NY Media, is part of dmg::media – a large consumer media organisation with an annual turnover of over £1 billion. They manage the advertising for a number of major web properties, and their analysts needed up to date, detailed data in order to manage that advertising effectively.
<aside>
  <p>The system contains 12 TB (over 106 billion datapoints in total) of compressed data stored</p>
</aside>
We used our Kixi cloud-based system to create customised data processing pipelines, which bring together, scrub, and summarise over 10 billion datapoints from 18 different sources overnight each night.

The system uses Hadoop and other open source technologies, to reliably and efficiently process large volumes of data so that they are ready for analysts to use each morning. The post-processed data is available to in-house analysts to datamine through an Amazon Redshift data warehouse, which they can query with SQL.

## Our approach
This project embodied three key elements of our approach:
- The architecture and code are transparent to the client, meaning that the client retains control and is not tied to a particular approach or vendor in future.
- Commodity hardware in the cloud and standard open source software is used for infrastructure. The Mastodon C platform code (Kixi) is also available under an open source software license; the value that we add is in building, customising, and managing a system to the client’s specific needs.
- Uniquely, we combine a deep understanding of both practical Hadoop cloud architectures and advanced analytics, ensuring that systems both function effectively and provide real business insight.

## By the numbers
The system contains:

- 12 TB (over 106 billion datapoints in total) of compressed data stored
- Over 70 GB of data added daily from 18 sources via 5 different data vendors via various https web services and files via sftp
- Runs very efficiently: only one ETL server, and 8 database servers at peak times

## Ongoing support
Having built the original system, we also operate the system day to day, including:

- Ongoing platform maintenance and on-call support
- Cloud server usage management
- Data quality checks and alerts, so that the client is immediately aware of any issue with incoming raw data
- Two developer days per month for ongoing smaller tweaks and additions as requested

## Business impact
The infrastructure allows our client to join data inputs that weren’t previously joined, then roll this up to make big data small again. This means that they are seeing new trends that they didn’t see before, but are still able to pivot this information in Excel – where their analysts can extract most value from it.

The result of this insight has been a 360% increase in usage of their targeting products for improving campaign performance

It has also enabled true ‘big data’ analysis using MATLAB to analyse granular data points such as fraudulent IP addresses – this has allowed our client to reduce the amount of fraudulent behaviour they see more than tenfold.
