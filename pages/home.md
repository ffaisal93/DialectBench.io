---
layout: home
title: DIALECTBENCH
description: A NLP Benchmark for Dialects, Varieties, and Closely-Related Languages.
permalink: /
toc: true
---

<div class="button-container text-center">
  <a href="https://aclanthology.org/2024.acl-long.777.pdf" target="_blank" class="text-center">
    <img src="assets/theme/images/paper_preview.png" alt="Paper Preview" class="preview-image paper-border">
    <div>Paper</div>
  </a>
  <a href="https://github.com/ffaisal93/DialectBench" target="_blank" class="text-center">
    <img src="assets/theme/images/github_preview.png" alt="GitHub Preview" class="preview-image github-border">
    <div>GitHub</div>
  </a>
  <a href="https://drive.google.com/file/d/19M4vDHi8N8jtUEpjdhXlHGin51aGmHIt/view?usp=sharing" target="_blank" class="text-center">
    <img src="assets/theme/images/slides_preview.png" alt="Slides Preview" class="preview-image slides-border">
    <div>Slides</div>
  </a>
  <a href="https://drive.google.com/file/d/199TJFb9A6pj9zak61VmsjUD8VmoYaIJq/view?usp=sharing" target="_blank" class="text-center">
    <img src="assets/theme/images/poster_preview.png" alt="Poster Preview" class="preview-image poster-border">
    <div>Poster</div>
  </a>
</div>

<style>
  .button-container {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 30px;
    margin: 20px 0;
  }
  .button-container a {
    text-align: center;
    text-decoration: none;
    color: inherit;  /* Use the default text color */
  }
  .preview-image {
    display: block;
    margin: 0 auto 5px;
    height: 100px;
    border: 2px solid #ccc;  /* Default border color */
    border-radius: 8px;  /* Optional: rounded corners */
  }
  .paper-border {
    border-color: #6c757d; /* Gray border for Paper */
  }
  .github-border {
    border-color: #ff6347; /* Tomato border for GitHub */
  }
  .slides-border {
    border-color: #ffa500; /* Orange border for Slides */
  }
  .poster-border {
    border-color: #4682b4; /* Steel blue border for Poster */
  }
  .button-container div {
    font-weight: bold;  /* Make the text bold for emphasis */
    margin-top: 5px;  /* Add spacing between the image and text */
  }
</style>






DIALECTBENCH is the first-ever large-scale benchmark for NLP on varieties, aggregating an extensive set of 281 language varieties over 10 text-level task datasets.

{:.clearfix .mx-auto}
![alt text](assets/theme/images/dialectbench_framework.png){:.rounded .float-end .col-md-5}
**Data and Language Varieties Selection** We looked through papers published in the ACL Anthology from the last 10 years to find usable language resources, as well as commonly used online data repositories. We selected languages that
have well-established, high-resourced varieties. Varieties may vary by location, ethnicity, or other factors.<br>
**Cluster-Variety Mapping** We construct several language clusters comprising of both high-resourced dialects and their low-resourced counterparts. We use the Glottolog language database to define clusters and assign varieties.

### Tasks

![alt text](assets/theme/images/tasks.png)
_The tasks and data sources of DIALECTBENCH_

### Language Clusters and Varieties

![alt text](assets/theme/images/dialect_count.png)
_DIALECTBENCH language clusters with their variety counts per task._

### Summaries

![alt text](assets/theme/images/result_summary.png)
_Task specific result summary using Maximum Obtainable Score. The varieties with the minimum scores exhibit a noticeable lag in performance across various tasks when compared to the average task performance._


### Bibtex

```
@inproceedings{faisal-etal-2024-dialectbench,
    title = "{DIALECTBENCH}: An {NLP} Benchmark for Dialects, Varieties, and Closely-Related Languages",
    author = "Faisal, Fahim  and
      Ahia, Orevaoghene  and
      Srivastava, Aarohi  and
      Ahuja, Kabir  and
      Chiang, David  and
      Tsvetkov, Yulia  and
      Anastasopoulos, Antonios",
    editor = "Ku, Lun-Wei  and
      Martins, Andre  and
      Srikumar, Vivek",
    booktitle = "Proceedings of the 62nd Annual Meeting of the Association for Computational Linguistics (Volume 1: Long Papers)",
    month = aug,
    year = "2024",
    address = "Bangkok, Thailand",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2024.acl-long.777",
    doi = "10.18653/v1/2024.acl-long.777",
    pages = "14412--14454",
}
```