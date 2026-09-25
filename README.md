# Sparse Conversation Structure Modeling for Early Rumor Verification

This repository accompanies the manuscript **“Sparse Conversation Structure Modeling for Early Rumor Verification.”** It contains the implementation of **Sparse Structural Evidence Enhancement (SSEE)**, a framework designed to model incomplete conversation structures during early rumor verification.

## Method

SSEE uses RoBERTa to encode the source post and observed replies, followed by a two-layer Graph Attention Network (GAT). It then refines the node representations through three components:

* **Structural Evidence Mining (SEM):** weights the contribution of observed local interactions.
* **Adaptive Global Context Compensation (AGCC):** introduces conversation-level context through node-specific gates.
* **Adaptive Structural Enhancement (ASE):** applies a structure-aware residual refinement.

The enhanced node representations are pooled to predict the veracity label.

## Datasets

The experiments use two publicly available datasets. Download them from their original sources:

* **DRWeibo:** https://github.com/CcQunResearch/DRWeibo
* **PHEME — Rumour Detection and Veracity Classification:** https://figshare.com/articles/dataset/PHEME_dataset_for_Rumour_Detection_and_Veracity_Classification/6392078

The original datasets are not redistributed in this repository.

## Evaluation

On **DRWeibo**, models are evaluated at five observation windows: **10, 30, 60, 120, and 240 minutes**. On **PHEME**, cross-event generalization is evaluated using **leave-one-event-out** testing.

The manuscript compares SSEE with a semantic-only model, vanilla GAT, BiGCN, and RAGCL. It also reports component ablations, parameter sensitivity, computational cost, and case studies.

SSEE obtains the highest average Macro-F1 in four of the five DRWeibo windows. Its advantage is not uniform across windows: vanilla GAT performs better at 60 minutes. On PHEME, SSEE has the highest overall average Macro-F1 among the evaluated models, but its paired difference from vanilla GAT is **not statistically significant**.

## Reproduction

Installation instructions, dataset preprocessing steps, training commands, evaluation commands, configuration files, and random seeds will be documented here when the corresponding code is uploaded.

## Citation

Citation information will be added when the manuscript is publicly available.
