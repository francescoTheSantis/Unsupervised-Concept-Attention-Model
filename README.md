# Learnable Concept-Based Model

This repository contains the official implementation to reproduce the experiments in the paper: [Towards Better Generalization and Interpretability in Unsupervised Concept-Based Models](https://arxiv.org/abs/2506.02092)
Published at **ECML PKDD 2025 (Research Track)**.

---

## 📄 Paper Summary

We introduce **LCBM (Learnable Concept-Based Model)**, a novel **unsupervised concept-based model** for image classification that improves both **accuracy** and **interpretability**.

Unlike prior approaches, LCBM learns a compact set of concepts represented as Bernoulli latent variables, each associated with an embedding to overcome the trade-off between performance and interpretability. LCBM achieves strong performance across multiple datasets and supports interpretable predictions through linear combinations of concept activations.

### 🔍 Key Features
- **Improved generalization**: Matches or exceeds prior unsupervised CBMs and approaches black-box performance.
- **Human-aligned concepts**: Concepts are more intuitive and better aligned, as shown through F1 scores, CAS, and a user study.
- **Faithful explanations**: Supports concept interventions and visual dictionaries for transparent decision-making.

We evaluated the model on both toy and real datasets: MNIST Even/Odd, MNIST Addition, CIFAR-10, CIFAR100, Tiny ImageNet, Skin Lesions and CUB-200.

## Reproducibility Instructions

Follow the steps below to reproduce the results reported in the paper.

### 1. Environment Setup

Make sure you have [conda](https://docs.conda.io/en/latest/) installed.

```bash
conda env create -f environment.yaml
conda activate lcbm
```

### 2. Training Models
To train and save all models used in the paper:

- LCBM (ours):
```bash
bash bash_scripts/run_LCBM.sh
```

Baselines:
- BlackBox:
```bash
bash bash_scripts/run_E2E.sh
```
- Label-Free CBM:
```bash
bash bash_scripts/run_LF_CBM.sh
```
For this baseline, the concepts have been extracted from GPT-4o for each dataset and are reported into the `concept_list` folder.

⚠️ For other baselines (SENN, BotCL, etc.), we used the official repositories. We recommend doing the same for faithful reproduction.

### 3. Evaluation & Explanations
To compute all the metrics and generate explanations:
```bash
bash bash_scripts/compute_concept_metrics.sh
bash bash_scripts/run_explanations.sh
```

These scripts cover concept alignment, interpretability metrics, and qualitative visualizations such as concept dictionaries and Grad-CAMs.

## Citation
<pre>@article{de2025towards,
  title={Towards Better Generalization and Interpretability in Unsupervised Concept-Based Models},
  author={De Santis, Francesco and Bich, Philippe and Ciravegna, Gabriele and Barbiero, Pietro and Giordano, Danilo and Cerquitelli, Tania},
  journal={arXiv preprint arXiv:2506.02092},
  year={2025}
}</pre>
