---
layout: content-feature
client: nhs
title: "Patient Safety text mining"
subtitle:  "NHS"
lowdown: "Automatically finding trends and patterns in patient safety reports in a large hospital trust, helping to spot potentially dangerous issues in a complex environment before they cause real harm."
logo: logo-nhs.jpg
bgimage: examplebg2.jpg
download: casestudy.pdf
---
## The scene
We worked with a large London hospital trust to explore ways to improve patient safety reporting. Patient safety is a critical concern in hospitals, and in such a complex human and medical environment there are always incidents which could cause harm to patients. A strong “reporting culture” is an important aspect of avoiding harm: whenever an incident does or could harm a patient, staff are required to write up a description of the incident and causes, tag it with some relevant information (ward, time, incident type, etc) and submit it to a central database.

The hospital trust in question has a strong reporting culture, which is excellent for patient safety. However, there are around 10,000 incidents a year which get written up, meaning that it’s not realistic for any single person to have a handle on the content of all reports, especially in cases where new incident patterns are spread across wards (for example, equipment issues), and don’t fall under the view of any single person in the management hierarchy. As a result, there is a risk that patterns of incidents are not noticed until they cause significant harm, and that more minor patterns of incidents go unnoticed.

We were asked to review the current reporting system, and to prototype the use of dashboard technology and text mining algorithms to make it easier for the professionals involved to notice patterns more easily in the report text.    

## What we found
We created a prototype system which automatically detected ‘topics’ in the reporting text, and was able to successfully classify reports into these topics (for example, pressure ulcers, errors in drug dosages).  


<figure>
<img src="{{ site.baseurl }}/assets/images/nhs-figure1.png" alt="" />
 <figcaption>
  Examples of report extracts automatically classified as being about pressure ulcers
</figcaption>
</figure>
We were also able to automatically tag a large number of incident reports mentioning specific drugs: 10% of reports named at least one drug. This is helpful in a hospital setting, as errors or omissions in dosage are very common, and are not specific to a single ward. A few reports also mentioned mixups between similarly named or packaged drugs, which are particularly important to note and to fix before such errors are repeated.

This was only a prototype project, but showed very high potential to reduce patient harm in future. The hospital trust in question are now considering how they might take on and develop this as part of their processes in future, and at the same time we are exploring options to develop this further as a service with other trusts and patient safety stakeholders. Like all of our projects, this was run in an agile manner and continues to make use of and add to state of the art open source technology.
