<h1 align="center">
  <img src="assets/RecRM-Bench_icon.png" height="40" style="vertical-align:middle; margin-right:8px;">
  RecRM-Bench: Benchmarking Multidimensional Reward Modeling for Agentic Recommender Systems
</h1>

<p align="center">
  <a href="https://arxiv.org/abs/2605.11874"><img src="https://img.shields.io/badge/arXiv-2605.11874-b31b1b?style=flat&logo=arxiv&logoColor=white" alt="Paper"></a>
  &nbsp;
  <a href="https://github.com/Buycar-arb/RecRM-Bench"><img src="https://img.shields.io/badge/GitHub-RecRM--Bench-black?style=flat&logo=github&logoColor=white" alt="Code"></a>
  &nbsp;
  <a href="https://huggingface.co/datasets/wwzeng/RecRM-Bench"><img src="https://img.shields.io/badge/🤗%20HuggingFace-Dataset-yellow?style=flat" alt="Dataset"></a>
  &nbsp;
  <a href="http://10.146.225.242:8084/index.html"><img src="https://img.shields.io/badge/🌐%20Project-Page-blue?style=flat" alt="Project Page"></a>
</p>


## 📖 Introduction

The integration of LLM agents is transforming recommender systems toward personalized, interactive recommendations, with Reinforcement Learning (RL) providing the optimization framework. However, existing methods rely on **single-dimensional, outcome-based rewards** that overlook critical intermediate capabilities such as instruction following and complex intent understanding, and the field lacks a standardized benchmark to facilitate multi-dimensional reward design.

To bridge this gap, we introduce **RecRM-Bench**, the first comprehensive benchmark specifically engineered for **reward modeling in agentic recommender systems**. It comprises over **1 million** structured entries derived from real-world interaction logs on the Meituan life-services platform, spanning four core evaluation dimensions:

- 📋 **Instruction Following** — syntactic compliance with output formats and operational constraints
- 🔍 **Factual Consistency** — grounding responses in retrieved information and avoiding hallucinations
- 🎯 **Query-Item Relevance** — semantic alignment between user intent and recommended items
- 👤 **User Behavior Prediction** — fine-grained prediction of user engagement and item ranking

By supporting comprehensive assessment from syntactic compliance to complex intent grounding and preference modeling, RecRM-Bench provides a foundational dataset for training sophisticated reward models to power next-generation agentic recommender systems.

## 🔖 Dataset Details

RecRM-Bench is organized into four sub-databases, each targeting a distinct evaluation dimension.

| Sub-database | Entries | Data Source | Annotation Method |
| :--- | :---: | :--- | :--- |
| Instruction Following | 8,422 | 68,096 raw query-response pairs (30,430 users) | LLM-as-judge + targeted synthesis |
| Factual Consistency | 9,391 | Real-world agent responses | Human-in-the-loop LLM distillation |
| Query-Item Relevance | 19,456 | 20,000+ interactions across 6 service categories | Expert annotation + LLM distillation |
| User Behavior — Prediction | 960,862 | Real-world interactions | Real behavioral labels |
| User Behavior — Ranking | 75,648 | Real-world interactions | Real behavioral labels |
| **Total** | **~1,073,779** | | |

## 📊 Benchmark Results

Performance of state-of-the-art models (zero-shot) on RecRM-Bench:

| Models | IF ACC (%) | IF F1 (%) | FC ACC (%) | FC F1 (%) | QIR ACC (%) | QIR F1 (%) | IR ACC (%) | IR AUC (%) | IR HR (%) | UBP ACC (%) | UBP AUC (%) |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| GPT-4.1 | 55.47 | 58.33 | 62.96 | 77.27 | 79.26 | 79.48 | 42.54 | 51.32 | 75.37 | 39.28 | 49.31 |
| LongCat-Flash-Chat | 64.84 | 65.19 | 67.34 | 80.48 | **73.18** | **72.82** | 62.48 | 54.93 | 82.93 | 46.49 | 52.22 |
| LongCat-Flash-Thinking | 43.75 | 48.16 | 64.98 | 78.78 | 75.97 | 76.17 | 34.09 | 57.89 | **70.00** | **31.02** | **45.41** |
| Deepseek-V3.2 (w/o thinking) | 30.47 | 29.94 | 43.43 | 60.56 | 74.60 | 74.76 | 52.32 | 50.57 | 82.53 | 47.80 | 52.10 |
| Deepseek-V3.2 (w/ thinking) | 35.29 | 39.50 | **41.41** | **58.57** | 75.22 | 75.57 | **29.55** | 57.04 | 72.42 | 35.17 | 50.76 |
| Qwen3-Max (w/o thinking) | 36.80 | 40.33 | 53.20 | 69.45 | 76.64 | 77.02 | 50.11 | 50.18 | 77.17 | 42.79 | 52.08 |
| Qwen3-Max (w/ thinking) | **26.67** | **26.64** | 56.57 | 72.26 | 75.89 | 76.16 | 50.16 | **50.01** | 78.42 | 44.47 | 48.50 |
| **Ours (RecRM-RL)** | **72.66** | **72.40** | **70.71** | **82.84** | **89.36** | **89.12** | **86.78** | **86.32** | **83.67** | **77.78** | **81.46** |

> Bold values in the baseline rows indicate the **worst** performing model per column. Bold values in the Ours row indicate **best** overall performance.

## 📝 Citation

If you find this work useful, please cite our paper:

```bibtex
@misc{zeng2026recrmbenchbenchmarkingmultidimensionalreward,
      title={RecRM-Bench: Benchmarking Multidimensional Reward Modeling for Agentic Recommender Systems}, 
      author={Wenwen Zeng and Jinhui Zhang and Hao Chen and Zhaoyu Hu and Yongqi Liang and Jiajun Chai and Dengcan Liu and Zhenfeng Liu and Shurui Yan and Minglong Xue and Xiaohan Wang and Wei Lin and Guojun Yin},
      year={2026},
      eprint={2605.11874},
      archivePrefix={arXiv},
      primaryClass={cs.IR},
      url={https://arxiv.org/abs/2605.11874}, 
}
```
