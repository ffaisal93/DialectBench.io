---
permalink: /results/
toc: true
---



<h2 style="text-align: center;">Dialectal Gap Across Language Clusters</h2>
<p style="text-align: center;">Here we plot the zero-shot dialectal gap across all tasks. On the x-axis, we plot aggregated cluster-level gap compared to English, while on the y-axis, we plot the aggregated cluster-level gap compared to the representative variety (standard variety). In an ideal scenario, both of these gap values would be close to zero. </p>

<div style="width: 100%; display: flex; justify-content: center;">
    <figure style="display: inline-block; text-align: center; margin-right: 20px;">
        <img src="../assets/theme/images/dep-gap.png" style="width: 100%; height: auto;">
        <figcaption style="width: 100%;">Dependency Parsing</figcaption>
    </figure>
    <figure style="display: inline-block; text-align: center; margin-right: 20px;">
        <img src="../assets/theme/images/pos-gap.png" style="width: 100%; height: auto;">
        <figcaption style="width: 100%;">POS Tagging</figcaption>
    </figure>
    <figure style="display: inline-block; text-align: center;">
        <img src="../assets/theme/images/topic-gap.png" style="width: 100%; height: auto;">
        <figcaption style="width: 100%;">Topic Classification</figcaption>
    </figure>
</div>

<p style="text-align: center;">As expected, we oberve that low-resource clusters have genrally have higher dialectal gaps when compared to English and even when compared to the standard variety within the cluster. High-resource Germanic and Sinitic language clusters consistently exhibit low dialectal gaps. </p>

<div style="width: 100%; display: flex; justify-content: center;">
    <figure style="display: inline-block; text-align: center; margin-right: 20px;">
        <img src="../assets/theme/images/nli-gap.png" style="width: 100%; height: auto;">
        <figcaption style="width: 100%;">Natural Language Inference</figcaption>
    </figure>
    <figure style="display: inline-block; text-align: center; margin-right: 20px;">
        <img src="../assets/theme/images/sdqa-test-gap.png" style="width: 100%; height: auto;">
        <figcaption style="width: 100%;">Extractive Question Answering</figcaption>
    </figure>
    <figure style="display: inline-block; text-align: center;">
        <img src="../assets/theme/images/ner-gap.png" style="width: 100%; height: auto;">
        <figcaption style="width: 100%;">Named Entity Recognition</figcaption>
    </figure>
</div>

<h2 style="text-align: center;">Task Specific Scores</h2>

<h3 style="text-align: center;">Structured Prediction</h3>
<p style="text-align: center;">Across all structured prediction tasks, we observe higher performance in higher-resourced Indo-European languages compared to low-resource varieties from  indigenous South American and  Uralic language clusters. </p>

<figure style="display: block; margin: 0 auto; text-align: center;">
    <img src="../assets/theme/images/dep.png" style="width: 100%; height: auto;">
    <figcaption style="width: 100%;">Dependency Parsing</figcaption>
</figure>

<figure style="display: block; margin: 0 auto; text-align: center;">
    <img src="../assets/theme/images/pos.png" style="width: 100%; height: auto;">
    <figcaption style="width: 100%;">POS Tagging</figcaption>
</figure>

<figure style="display: block; margin: 0 auto; text-align: center;">
    <img src="../assets/theme/images/ner.png" style="width: 100%; height: auto;">
    <figcaption style="width: 100%;">Named Entity Recognition</figcaption>
</figure>


<h3 style="text-align: center;">Sequence Classification</h3>

<figure style="display: block; margin: 0 auto; text-align: center;">
    <img src="../assets/theme/images/topic.png" style="width: 100%; height: auto;">
    <figcaption style="width: 100%;">Topic Classification</figcaption>
</figure>

<figure style="display: block; margin: 0 auto; text-align: center;">
    <img src="../assets/theme/images/nli.png" style="width: 100%; height: auto;">
    <figcaption style="width: 100%;">Natural Language Inference</figcaption>
</figure>

<figure style="display: block; margin: 0 auto; text-align: center;">
    <img src="../assets/theme/images/di.png" style="width: 100%; height: auto;">
    <figcaption style="width: 100%;">Dialect Identification</figcaption>
</figure>

<figure style="display: block; margin: 0 auto; text-align: center;">
    <img src="../assets/theme/images/sc.png" style="width: 100%; height: auto;">
    <figcaption style="width: 100%;">Sentiment Analysis</figcaption>
</figure>


<h3 style="text-align: center;">Question Answering</h3>

<figure style="display: block; margin: 0 auto; text-align: center;">
    <img src="../assets/theme/images/rcmc.png" style="width: 100%; height: auto;">
    <figcaption style="width: 100%;">Multiple Choice Machine Reading Comprehension</figcaption>
</figure>

<figure style="display: block; margin: 0 auto; text-align: center;">
    <img src="../assets/theme/images/sdqa-test.png" style="width: 100%; height: auto;">
    <figcaption style="width: 100%;">Extractive Question Answering</figcaption>
</figure>


<h3 style="text-align: center;">Machine Translation</h3>

<figure style="display: block; margin: 0 auto; text-align: center;">
    <img src="../assets/theme/images/mt-dialect.png" style="width: 100%; height: auto;">
    <figcaption style="width: 100%;">Variety level aggregation</figcaption>
</figure>

<figure style="display: block; margin: 0 auto; text-align: center;">
    <img src="../assets/theme/images/mt-region.png" style="width: 100%; height: auto;">
    <figcaption style="width: 100%;">Region level aggregation for Swiss German and Italian</figcaption>
</figure>


<h2 style="text-align: center;">Regional Maps</h2>
