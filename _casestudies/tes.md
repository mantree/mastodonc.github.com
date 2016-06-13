---
layout: content-feature
client: tes
title: "Supporting the TES World University Rankings"
subtitle:  "TES Global"
lowdown: "Performing complex data processing and checking, to create the business-critical and highly sensitive World University Rankings."
logo: logo-tes.jpg
bgimage: bg-tes.jpg
download: casestudy.pdf
---
## The scene
Our client, TES Global, owns the Times Higher Education Supplement, which publishes the annual World University Rankings. These rankings are critical not only to our client, but to the hundreds of global universities for whom their ranking position is a key success measure. These rankings depend on a number of data sources, including detailed papers and citations data, reputation surveys, and large amounts of data about students and funding per institution.

TES Global had previously outsourced much of the rankings production; they wished to begin owning more of the process in-house and to be more transparent about the methodology to universities. They also wished to begin producing a number of additional standardised data products based on similar concepts, to increase the list of universities ranked from 250 to over 1000, and to develop the capacity to deliver customised data products for particular industries or other clients with interest in academic rankings data.

## Our approach
Working from existing documentation from a previous outsourced vendor, we worked alongside the TES in-house team to:

  - Understand the old rankings methodology, which used a number of complex analytical and statistical steps
  - Develop new tests and checks to ensure that, as the data sources grow and change and data becomes more complex, the rankings produced are accurate, consistent with previous years, and fair
  - Develop a data storage and processing approach which is simple, performant, and allows very clear understanding of data versioning and adjustments performed along the way - this is critical to allow future audit and understanding of where numbers come from

We developed a set of Clojure scripts, backed by a cloud-based JSON data store, and accessed via a simple command-line interface, to enable analysts to run ranking variants and output results files and audit reports quickly, easily, and repeatably.

## The results
The new setup enabled TES to produce rankings in-house for the first time, which were launched publicly in October 2015.
They are now using the same code to develop new data products which are expected to expand their universities business significantly in future years, making it a more data-driven and high impact business than ever before.
