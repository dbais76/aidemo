---
pretty_name: Emotions
license: cc-by-sa-4.0
language:
  - en
size_categories:
  - 10K<n<100K
task_categories:
  - text-classification
task_ids:
  - multi-class-classification
tags:
  - emotion-classification
dataset_info:
  - config_name: split
    features:
      - name: text
        dtype: string
      - name: label
        dtype:
          class_label:
            names:
              "0": sadness
              "1": joy
              "2": love
              "3": anger
              "4": fear
              "5": surprise
    splits:
      - name: train
        num_bytes: 1741597
        num_examples: 16000
      - name: validation
        num_bytes: 214703
        num_examples: 2000
      - name: test
        num_bytes: 217181
        num_examples: 2000
    download_size: 740883
    dataset_size: 2173481
  - config_name: unsplit
    features:
      - name: text
        dtype: string
      - name: label
        dtype:
          class_label:
            names:
              "0": sadness
              "1": joy
              "2": love
              "3": anger
              "4": fear
              "5": surprise
    splits:
      - name: train
        num_bytes: 45445685
        num_examples: 416809
    download_size: 15388281
    dataset_size: 45445685
train-eval-index:
  - config: default
    task: text-classification
    task_id: multi_class_classification
    splits:
      train_split: train
      eval_split: test
    col_mapping:
      text: text
      label: target
    metrics:
      - type: accuracy
        name: Accuracy
      - type: f1
        name: F1 macro
        args:
          average: macro
      - type: f1
        name: F1 micro
        args:
          average: micro
      - type: f1
        name: F1 weighted
        args:
          average: weighted
      - type: precision
        name: Precision macro
        args:
          average: macro
      - type: precision
        name: Precision micro
        args:
          average: micro
      - type: precision
        name: Precision weighted
        args:
          average: weighted
      - type: recall
        name: Recall macro
        args:
          average: macro
      - type: recall
        name: Recall micro
        args:
          average: micro
      - type: recall
        name: Recall weighted
        args:
          average: weighted
---

# Dataset Card for "emotions"

## Table of Contents

- [Dataset Description](#dataset-description)
  - [Dataset Summary](#dataset-summary)
- [Dataset Structure](#dataset-structure)
  - [Data Instances](#data-instances)
  - [Data Fields](#data-fields)
  - [Data Splits](#data-splits)
- [Additional Information](#additional-information)
  - [Licensing Information](#licensing-information)
  - [Citation Information](#citation-information)

## Dataset Description

- **Paper:** [CARER: Contextualized Affect Representations for Emotion Recognition](https://aclanthology.org/D18-1404/)
- **Size of downloaded dataset files:** 16.13 MB
- **Size of the generated dataset:** 47.62 MB
- **Total amount of disk used:** 63.75 MB

### Dataset Summary

Emotions is a dataset of English Twitter messages with six basic emotions: anger, fear, joy, love, sadness, and surprise. For more detailed information please refer to the paper. Note that the paper does contain a larger data set with eight emotions being considered.

## Dataset Structure

### Data Instances

An example bit of data looks like this:

```
{
  "text": "im feeling quite sad and sorry for myself but ill snap out of it soon",
  "label": 0
}
```

### Data Fields

The data fields are:

- `text`: a `string` feature.
- `label`: a classification label, with possible values including `sadness` (0), `joy` (1), `love` (2), `anger` (3), `fear` (4), `surprise` (5).

### Data Splits

The dataset has two configurations.

- split: with a total of 20,000 examples split into train, validation and test.
- unsplit: with a total of 416,809 examples in a single train split.

| name    |  train | validation | test |
| ------- | -----: | ---------: | ---: |
| split   |  16000 |       2000 | 2000 |
| unsplit | 416809 |        n/a |  n/a |

## Additional Information

### Licensing Information

The dataset should be used for educational and research purposes only. It is licensed under Attribution-ShareAlike 4.0 International (CC BY-SA 4.0).

### Citation Information

If you use this dataset, please cite:

```
@inproceedings{saravia-etal-2018-carer,
    title = "{CARER}: Contextualized Affect Representations for Emotion Recognition",
    author = "Saravia, Elvis  and
      Liu, Hsien-Chi Toby  and
      Huang, Yen-Hao  and
      Wu, Junlin  and
      Chen, Yi-Shin",
    booktitle = "Proceedings of the 2018 Conference on Empirical Methods in Natural Language Processing",
    month = oct # "-" # nov,
    year = "2018",
    address = "Brussels, Belgium",
    publisher = "Association for Computational Linguistics",
    url = "https://www.aclweb.org/anthology/D18-1404",
    doi = "10.18653/v1/D18-1404",
    pages = "3687--3697",
    abstract = "Emotions are expressed in nuanced ways, which varies by collective or individual experiences, knowledge, and beliefs. Therefore, to understand emotion, as conveyed through text, a robust mechanism capable of capturing and modeling different linguistic nuances and phenomena is needed. We propose a semi-supervised, graph-based algorithm to produce rich structural descriptors which serve as the building blocks for constructing contextualized affect representations from text. The pattern-based representations are further enriched with word embeddings and evaluated through several emotion recognition tasks. Our experimental results demonstrate that the proposed method outperforms state-of-the-art techniques on emotion recognition tasks.",
}
```
