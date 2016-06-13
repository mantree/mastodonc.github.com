---
layout: content-feature
client: defra
title: "Open source data analysis prototype"
subtitle:  "Defra"
lowdown: "Helping Defra, a large UK government department, to explore the use of new analytics and technologies and create a more data-driven approach to spotting threats faster than current surveillance methods."
logo: logo-defra.jpg
bgimage: examplebg4.jpg
download: casestudy.pdf
---
## The scene
Defra's Animal and Plant Health Agency (APHA) is tasked with safeguarding animal and food health in the UK. One way that they do this is by monitoring and collecting large numbers of data sources on animal health and disease, including farm data, geographic data, and animal post mortems.

Monitoring and identifying emerging threats to animal health from all of these sources is challenging, as they have complex structures (and, in the case of post mortems, contain large amounts of unstructured text), and vary widely in volume, quality, and availability, and because there is a drive to make better use of experts time than just going through raw data to try to find patterns, trends and outliers.

<aside>
  <p>We were asked to assist in development of a prototype dashboard and analytics system which would help APHA to understand the options in this field, and to test their potential value for the agency.</p>
</aside>

Therefore APHA are keen to take advantage of new open source technologies which enable experts to focus their attention on likely areas of new patterns or issues, by using both analytical methods (for example text mining) and data visualisation techniques, to get a new view on their data.

### What we did
We created a prototype system using Spark which automatically detected 'topics' in post mortems, and created automated alerts when there was a sudden spike either in text topics or in other quantifiable data such as counts of animal abortions in a region. We also showed how to visualise this complex data in a way which was user-friendly for experts to use day-to-day, to help focus their attention on problem areas.

This was only a prototype project, but showed very high potential to help with disease detection in future. In particular, it demonstrated high potential in techniques including:

- **topic detection**, which turns large amounts of free form text into quantifiable counts, and lets us tag and arrange documents into more rapidly understandable forms;
- **Interactive, web-based visualisations** such as Sankey diagrams, which help experts to visualise complex processes and more rapidly spot anomalies or surprises in these processes than standard or static visualisations, and;
- **Automated alerting** when standard seasonal and growth patterns stopped being followed.

It also demonstrated the value of an open source toolset in building cost-effective and flexible solutions for advanced analytics and visualisation.
