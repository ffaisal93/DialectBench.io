---
title: Markdown
description: >
  You write your content in [Markdown](assets/theme/images/solid-color-image.png).
  This page shows how it is rendered by Petridish.
<!-- background:
  img: assets/theme/images/solid-color-image.png
  by: Krzysztof Niewolny -->
  href: https://unsplash.com/photos/pTfcnk9WZHA
permalink: /readme/
toc: true
---

{:.alert .alert-warning}
The source file for this page is [`pages/docs/markdown.md`](https://raw.githubusercontent.com/peterdesmet/petridish/main/pages/docs/markdown.md). There you can see the raw Markdown.


## Download Data
- Download all data available `[except mt  and the ones loadable through huggingface]`
  ```bash
  bash download_data.sh --task all
  ```
- Download Turkish dialectal machine translations
  ```bash
  bash download_data.sh --task machine_translation_turkish
  ```

## Package Installation 
-  `Dependency parsing:` Install Adapter Package
```bash
bash install.sh --task install_adapter
```
- `Extractive Question Answering [SDQA]:` Install Transformers 3.4.0
```bash
bash install.sh --task install_transformers_qa
```
- `Other Structured Prediction, QA and Classification tasks:` Transformers 4.21.1
```bash
bash install.sh --task install_transformers
```

## Task Specific Training and Evaluation

### Dependency Parsing

###### Training

- Finetune all available language-specific models on both pretrained mBERT and XLMR at once
  ```
  ./all_commands.sh --action train_udp --execute bash
  ```
- Finetune one single available language-specific model
  ```
  bash install.sh --task train_udp --lang UD_English-EWT --MODEL_NAME mbert
  ```

###### Prediction
- Prediction on all finetuned model (for both pretrained mBERT and XLMR) and if no training data available for a specific language variety, do zeroshot from English variety `"UD_English-EWT"`
  ```bash
  ./all_commands.sh --action predict_udp --execute bash
  ```
- Do zero-shot prediction from a specific language variety (e.g. `UD_English-EWT`) and on all available variety defined in `--lang_config metadata/udp_metadata.json`
  ```bash
  bash install.sh --task predict_udp_zeroshot_all --lang UD_English-EWT --MODEL_NAME mbert
  ```
- Do test data prediction on a single finetuned language variety (e.g. `UD_English-EWT`)
  ```bash
  bash install.sh --task predict_udp_single --lang UD_English-EWT --MODEL_NAME mbert
  ```

### Parts of Speech (POS) Tagging 

###### Training

- Finetune all available language-specific models on both pretrained mBERT and XLMR at once
  ```
  ./all_commands.sh --action train_pos --execute bash
  ```

###### Prediction
- Prediction on all finetuned model (for both pretrained mBERT and XLMR) and if no training data available for a specific language variety, do zeroshot from English variety `"UD_English-EWT"`
  ```bash
  ./all_commands.sh --action predict_pos --execute bash
  ```

### Named Entity Recognition (NER)

###### Training

- Performing in-variety Finetuning on all available language varieties on both pretrained mBERT and XLMR at one go.
  ```bash
  ./all_commands.sh --action train_pos --execute bash
  ```
- or, If you want to performing in-variety finetuning for a single language only, try the following:
  ```bash
  bash install.sh --task train_ner --lang bokmaal --MODEL_NAME bert --dataset wikiann
  ```
- We have two datasets supported in DialectBench at this point. `wikiann` and `norwegian_ner`.
  - `wikiann`: language varieties `("ar" "az" "ku" "tr" "hsb" "nl" "fr" "zh" "en" "mhr" "it" "de" "pa" "es" "hr" "lv" "hi" "ro" "el" "bn")`. Use `--dataset wikiann` to finetune varieties from this dataset.

  - `norwegian_ner`: language varieties ("bokmaal" "nynorsk" "samnorsk"). Use `--dataset scripts/ner/norwegian_ner.py` to finetune varieties from this dataset.

###### Prediction
- Prediction using all in-variety finetuned models (for both pretrained mBERT and XLMR) as well as performing zeroshot prediction using English variety `en` on the varieties available in `--lang_config metadata/metadata/ner_metadata.json` at one go.
  ```bash
  ./all_commands.sh --action predict_ner --execute bash
  ```


### Topic Classification (TC)

###### Training

- Performing In-cluster finetuning (on both pretrained mbert and xlm-r) on selected varieties from different language cluster.
```bash
./all_commands.sh --action train_topic_classification_lm --execute bash
```
- Add or remove specific variety for finetuning from SIB-200 dataset here in `command-bash.sh` file.
  
  ```bash
      if [[ "$task" = "train_topic_classification_lm" || "$task" = "predict_topic_classification_lm" ]]; then

        export ALL_LANGS=("eng_Latn" "ita_Latn" "azj_Latn" "ckb_Arab" "nob_Latn" "nld_Latn" "lvs_Latn" 
          "arb_Arab" "lij_Latn" "zho_Hans" "spa_Latn" "nso_Latn")

  ``` 

###### Prediction
- Performing inference on all available varieties across different language clusters (as defined in `--lang_config metadata/topic_metadata.json`) and on top of different pretrained models (mbert, xlmr)
```bash
./all_commands.sh --action predict_topic_classification_lm --execute bash
```

### Natural language inference (NLI)

###### Training

- Performing zero-shot finetuning from English (on top of both pretrained mbert and xlm-r) on selected varieties from different language cluster.
```bash
./all_commands.sh --action train_nli --execute bash
```
- Add or remove specific variety for finetuning from translate-test `dialect_nli` dataset here in `command-bash.sh` file.
  
  ```bash
    if [[ "$task" = "train_nli" || "$task" = "predict_nli" ]]; then

      # export ALL_LANGS=("eng_Latn" "ita_Latn" "azj_Latn" "ckb_Arab" "nob_Latn" "nld_Latn" "lvs_Latn" "arb_Arab" "lij_Latn" "zho_Hans" "spa_Latn" "nso_Latn" "ben_Beng")
      export ALL_LANGS=("eng_Latn")
      for lang in "${ALL_LANGS[@]}"; do
        echo ${base_model}
        echo ${lang}
        echo ${dataset}
        bash install.sh --task ${task} --lang ${lang} --MODEL_NAME ${base_model}
      done

    fi
  ``` 
- `dialect_nli` dataset loading script: `--dataset_script scripts/nli/dialect_nli.py`

###### Prediction
- Performing inference on all available varieties across different language clusters (as defined in `--lang_config metadata/nli_metadata.json`) and on top of different pretrained models (mbert, xlmr).
```bash
./all_commands.sh --action predict_nli --execute bash
```


### Santiment Analysis (SA)

###### Training
- At this point, DialectBench support arabic dialectal sentiment analysis. To finetune variety-specific models:
```bash
./all_commands.sh --action train_sa --execute bash
```

###### Prediction
- To evaluate, each variety-specific model at one go:
```bash
./all_commands.sh --action predict_sa --execute bash
```
- Add or remove specific variety for finetuning in `command-bash.sh` file.
  
  ```bash
    if [[ "$task" = "train_sa" || "$task" = "predict_sa" ]]; then

      export ALL_LANGS=("aeb_Arab" "aeb_Latn" "arb_arab" "ar-lb" "arq_arab" "ary_arab" "arz_arab" "jor_arab" "sau_arab")
      for lang in "${ALL_LANGS[@]}"; do
        echo ${base_model}
        echo ${lang}
        echo ${dataset}
        bash install.sh --task ${task} --lang ${lang} --lang2 arabic --MODEL_NAME ${base_model}
      done

    fi
  ``` 

#### Dialect Identification (DId)

###### Training

###### Prediction

#### Machine Reading Comprehension (MRC)

###### Training

###### Prediction

#### Extractive Question Answering

###### Training

###### Prediction

### installation
comment-out `module load python/3.8.6-ff` inside `install.sh` [specific to cluster]
- Install Adapter Package `[for dependency parsing]`
  ```
  bash install.sh --task install_adapter
  ```
- Install Transformers 3.4.0 `[for QA]`
  ```
  bash install.sh --task install_transformers_qa
  ```
- Install Transformers 4.21.1 `[for all other tasks]`
  ```
  bash install.sh --task install_transformers
  ```
## Tasks
Basically, start running `all_commands.sh` that calls either `command-bash.sh` or `command-slurm.sh` (through `--execute`; options: [`bash`/`slurm`]) depending on whether you are running bash-script or slurm jobs. Then `command-bash.sh` loops over all the data/model and call `install.sh` to run the training/prediction code snippet.

### Topic-Classification
- get the sib-200 data:
  ```
  bash install --task create_sib_topic_classification
  ```
- Training:
  ```
  ./all_commands.sh --action train_topic_classification --execute bash
  ```
- Prediction:
  ```
  ./all_commands.sh --action predict_topic_classification --execute bash
  ```




## Styling content

Petridish uses [kramdown](https://kramdown.gettalong.org/) as Markdown processor. This processor allows you to add attributes, such as CSS classes to your content (see this [blog post](https://digitaldrummerj.me/styling-jekyll-markdown/)). By sticking to [Bootstrap](https://getbootstrap.com/docs/5.1/) classes, you can easily style your content. If that doesn't fit your needs, you can always write html in your Markdown.

For example, the paragraph at the top of this page is styled as a [Bootstrap alert](https://getbootstrap.com/docs/5.1/components/alerts/) because it has `{:.alert .alert-warning}` right before it. Block elements like paragraphs need their class on the line above it.

Inline elements on the other hand, need a class right after it. For example, to style a link as a button, use `[Don't click](http://example.com){:.btn .btn-danger}`:

[Don't click](http://example.com){:.btn .btn-danger}

Note that kramdown does not process bare URL like GitHub does (they need to be written as `<url>`). If you want your content to [match the results you see on GitHub](https://docs.github.com/en/enterprise-server@3.5/pages/setting-up-a-github-pages-site-with-jekyll/setting-a-markdown-processor-for-your-github-pages-site-using-jekyll) without the option to style, change the markdown parser in `_config.bash` to:

```bash
markdown: gfm # GitHub Flavoured Markdown
```

## Headings

# Heading h1

h1 headings are reserved for page titles and are hidden from content. Start your headings at h2.

## Heading h2
### Heading h3
#### Heading h4
##### Heading h5
###### Heading h6
###### Heading with custom id {#custom_id}

## Table of content

Add `toc: true` to your page/post front matter. See [configuration]({{ '/docs/configuration/' | relative_url }}#pages).

## Paragraphs

Set i won't void spirit all. Had after called us It wherein Tree in deep abundantly also midst Seed. Beast. Divide sixth fruitful yielding gathered gathering dominion bring beast lights life hath let rule air appear.

Bring let rule creature. Very open hath to years. In second kind. Divide land night. Earth bearing tree lesser likeness likeness won't. Likeness creature light.

## Line breaks

This is the first line.  
And this is the second line.

## Emphasis

This is **bold text**

This is _italicized text_

This is **_bold italicized text_**

This is ~~strikethrough text~~

## Blockquotes

> Gathering brought him green. Creeping very after hath a, from likeness dry tree moved dry fowl. Our let forth, male dry won't god. Kind a thing, dominion lights midst him gathering waters fruitful greater god have dry land deep abundantly.

## Lists

Unordered list:

- Item 1
- Item 2
- Item 3
  - Subitem 1
  - Subitem 2

Ordered list:

1. Item 1
2. Item 2
3. Item 3
    1. Subitem 1
    2. Subitem 2

Task list:

- [x] Item 1
- [ ] Item 2
- [ ] Item 3

Definition list:

term 1
: definition 1.1
: definition 1.2

term 2
: definition 2

## Code

Inline `code`

Code block by indenting code with 4 spaces:

    part_of_team = True
    if part_of_team:
      print("Everything is awesome!") # If you're part of a team

Code block by fencing code in backticks. This method allows supports syntax highlighting by adding the language, e.g. <code>```python</code>:

```python
part_of_team = True
if part_of_team:
  print("Everything is awesome!") # If you're part of a team
```

## Horizontal rules

---

## Links

[link with url](http://www.example.com)

[link with title](http://www.example.com "title text")

[1]: http://www.example.com

[link with reference][1]

url: <http://www.example.com>

See the [Jekyll documentation](https://jekyllrb.com/docs/liquid/tags/#link) to create internal links. There are several approaches, but in my opinion the safest option is using root-relative permalinks (starting with `/`) and the `relative_url` filter:

- For pages: [{% raw %}`[link text]({{ '/about/' | relative_url }})`{% endraw %}]({{ '/about/' | relative_url }})
- For posts: [{% raw %}`[link text]({{ '/permalink_of_post/' | relative_url }})`{% endraw %}]({{ '/blog/2019/welcome-to-jekyll/' | relative_url }})
- For images and documents: [{% raw %}`[link text]({{ '/assets/images/name-of-image.jpg' | relative_url }})`{% endraw %}]({{ '/assets/theme/images/chuttersnap-146799-unsplash.jpg' | relative_url }})

You can simplify links if your site lives at a custom root domain (e.g. `https://example.com`, no `baseurl` set in `_config.bash`) or when Jekyll 4.0+ is used. Neither are the case for a default GitHub Pages, so the links below are likely broken:

- For pages: [`[link text](/about/)`](/about/)
- For posts: [`[link text](/permalink_of_post/)`](/blog/2019/welcome-to-jekyll/)
- For images and documents: [`[link text](/assets/images/name-of-image.jpg)`]('/assets/theme/images/chuttersnap-146799-unsplash.jpg)

If you want links that work on your site _and_ in your GitHub repository, use relative links to the Markdown files (e.g. `[about]{% raw %}(../about.md){% endraw %}`). These are automatically converted to permalinks by the [jekyll-relative-links](https://github.com/benbalter/jekyll-relative-links) plugin (enabled by default on GitHub Pages), but will break if you move pages around.

## Tables

Header 1 | Header 2
--- | ---
Row 1 col 1 | Row 1 col 2
Row 2 col 1 | Row 2 col 2 very_long_word_that_does_not_wrap_but_should_trigger_horizontal_scroll

Aligned columns:

Center aligned | Right aligned
:---: | :---
Row 1 col 1 | Row 1 col 2
Row 2 col 1 | Row 2 col 2 very_long_word_that_does_not_wrap_but_should_trigger_horizontal_scroll

HTML table with Bootstrap classes:

<table class="table table-dark table-striped">
  <thead>
    <th>Header 1</th>
    <th>Header 2</th>
  </thead>
  <tbody>
    <tr><td>Row 1 col 1</td><td>Row 1 col 2</td></tr>
    <tr><td>Row 2 col 1</td><td>Row 2 col 2 very_long_word_that_does_not_wrap_but_should_trigger_horizontal_scroll</td></tr>
  </tbody>
</table>

Petridish will automatically wrap tables in a div with class [`table-responsive`](https://getbootstrap.com/docs/5.0/content/tables/#responsive-tables) to avoid tables getting wider than their parent container. It will also automatically convert `<table>` to `<table class="table">` to enable Bootstrap layout, unless you already defined class(es) for your table.

## Footnotes

Here's a sentence with a footnote. [^1]

[^1]: This is the footnote.

## Images

![alt text](https://images.unsplash.com/photo-1486825586573-7131f7991bdd?w=1000&h=200&fit=crop)
_You can add an image caption by including an `_emphasized sentence_` directly below the image without inserting a new line. This will wrap both image and caption in a paragraph._

See the [the links section](#links) to learn how to reference your own images and documents.

By default, images will be centered horizontally and use the full width if they can. But you can change **image alignment** by using [Bootstrap classes](https://getbootstrap.com/docs/5.1/content/images/#aligning-images).

For example, the image below is wrapped in a paragraph with `{:.col-md-8 .mx-auto}` to contain it (and its caption) to 8/12 of the width on medium and larger screens. On small screens the full width will be used. Controlling the width of an image is especially useful for portrait images.

{:.col-md-8 .mx-auto}
![alt text](https://images.unsplash.com/photo-1486825586573-7131f7991bdd?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1000&q=80)
_Image caption for this image should nicely wrap to the width of the container._

{:.clearfix}
![alt text](https://images.unsplash.com/photo-1486825586573-7131f7991bdd?w=150&h=150&fit=crop){:.rounded .float-start} The image to the left is styled with `{:.rounded .float-start}` to give it round corners and position it at the start (i.e. left), with text wrapping around it. Note that in [Bootstrap v5](https://getbootstrap.com/docs/5.1/migration/#utilities) `.float-left` was renamed to `.float-start` and `.float-right` to `.float-end`, but the old class names are still supported in Petridish.

The image does not wrap around this paragraph, because the previous paragraph also has a [`{:.clearfix}`](https://getbootstrap.com/docs/5.1/helpers/clearfix/) class, which contains wrapping to that paragraph only.
