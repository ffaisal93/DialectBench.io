---
layout: home
title: DIALECTBENCH
description: An NLP Benchmark for Dialects, Varieties, and Closely-Related Languages.
permalink: /
toc: true
---



DIALECTBENCH is the first-ever large-scale benchmark for NLP on varieties, which aggregates an extensive set of task-varied variety datasets (10 text-level tasks covering 281 varieties).

{:.clearfix .mx-auto}
![alt text](assets/theme/images/dialectbench_framework.png){:.rounded .float-end .col-md-5}
**Variety Selection:** We looked through papers published in the ACL Anthology from the last 10 years to find usable language resources, as well as commonly used online data repositories. We selected languages that
have well-established, high-resourced varieties. Varieties may vary by location, ethnicity, or other factors.
**Cluster-Variety Mapping** We construct several language clusters comprising of both high-resourced dialects and their low-resourced counterparts. We use the Glottolog language database to define clusters and assign varieties.

### Tasks

![alt text](assets/theme/images/tasks.png)
_The tasks and data sources of DIALECTBENCH_

### Language Clusters and Varieties

![alt text](assets/theme/images/dialect_count.png)
_DIALECTBENCH language clusters with their variety counts per task._

### Task specific result summarys

![alt text](assets/theme/images/result_summary.png)
_Task specific result summary using Maximum Obtainable Score. The varieties with the minimum scores exhibit a noticeable lag in performance across various tasks when compared to the average task performance._


### Bibtex

```
@article{dialectbench,
	title={ DialectBench: An NLP Benchmark for Dialects, Varieties, and Closely-Related Languages},
	author={Fahim Faisal and Orevaoghene Ahia and Aarohi Srivastava and Kabir Ahuja and David Chiang and Yulia Tsvetkov and Antonios Anastasopoulos},
      year={2024},
}
```