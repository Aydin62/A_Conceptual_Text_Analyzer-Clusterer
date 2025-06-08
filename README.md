# **A CONCEPTUAL TEXT ANALYZER-CLUSTERER**

### Aydin Manzouri, 2025

---

# **SUMMARY**

<br>

This notebook provides a demo toolbox for conceptual analysis and clustering of text data.

<br>

## **Objective**

*To analyze and cluster texts based on their conceptual loads, via a hybrid concept-aggregate approach*

<br>

## **Contents**

It offers the following:

### (A) General

a.1.   Utilizes `spaCy` for NLP <br><br>
a.2.   Works with a hard-coded sample `concept_lexicon`, which is an aggregate-concept dictionary with entries:
```
"aggregate": ['concept_1', 'concept_2', ...]
```
<br>

a.3. Is capable of working with both single docs and batches <br><br>

### (B) Working with single documents

b.1. Function `analyze_txt` integrates the pipeline for *single* docs as: <br>

`filepath` → `read_txt` → `nlp` → `token_ext` → `concept_matcher` → `concept_aggregator`
<br><br>
b.2. `concept_aggregator` gives a tuple `(detailed, aggregated)` of data <br><br>
b.3. Functions `json_saver` and `json_loader` enable saving and loading the above data tuple in `JSON` format, resp. <br><br>
b.4. Function `aggreg_visu` generates and saves a bar chart from `aggregated` <br><br>
b.5. And function `concept_heatmap` generates and saves a heatmap from `detailed` <br><br>

### (C) Working with multiple documents

c.1. Function `batch_preprocess` loads multiple text files and prepares the data for the next steps <br><br>
c.2. Function `batch_plot` generates a batch of a couple of both plot types <br><br>
c.3. Functions `batch_json_saver` and `batch_json_loader` are batch-process analogs of their respective single-process functions <br><br>
c.4. Function `vectorizer` converts batch-preprocessed data into vectorized format to be used in ML operations. It combines detailed and aggregated data into a single `DataFrame` <br><br>
c.5. Finally, function `cluster` performs unsupervised learning, in the form of `KMeans` clustering. It:


*   receives data in vectorized format,
*   performs clustering,
*   applies PCA to high-dimensional data,
*   generates and saves the resulting 2D plot,
*   and returns a tuple `(df_combo, cluster_labels)`



---
<br><br>
