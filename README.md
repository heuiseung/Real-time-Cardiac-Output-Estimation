# Real-time Cardiac Output (CO) Estimation via Hybrid Attention-LSTM
> **High-fidelity hemodynamic monitoring using VitalDB Arterial Blood Pressure (ABP) waveforms.**

[![Python 3.12](https://img.shields.io/badge/python-3.12.10-blue.svg)](https://www.python.org/downloads/release/python-3120/)
[![PyTorch](https://img.shields.io/badge/PyTorch-2.4.1-EE4C2C?style=flat&logo=pytorch&logoColor=white)](https://pytorch.org/)
[![CUDA](https://img.shields.io/badge/CUDA-12.4-76B900?style=flat&logo=nvidia&logoColor=white)](https://developer.nvidia.com/cuda-toolkit)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](#license)

## 📝 Abstract & Clinical Significance
Continuous **Cardiac Output (CO)** monitoring is vital for hemodynamic stability in surgical patients. Conventional methods are often invasive or intermittent. This project presents a deep learning-based approach to estimate CO in real-time using only non-invasive **ABP waveforms**. Leveraging the **VitalDB Open Dataset**, our Hybrid Attention-LSTM model achieves laboratory-grade accuracy, enabling safer and more responsive intraoperative care.

---

## 💡 Analysis Framework: ASK to EVOLVE
Following the **ASK to EVOLVE** framework, this project bridges the gap between raw clinical data and actionable AI insights.

* **🔍 ASK**: Can we achieve precise CO estimation using non-invasive waveforms with ultra-low latency?
* **👀 LOOK**: Analyzed physiological noise and identified data scarcity in high-flow states within the VitalDB dataset.
* **🔬 INVESTIGATE**: Architected a **Hybrid Attention-LSTM** model to prioritize systolic phase morphologies and mitigate bias via **Weighted Loss**.
* **📢 VOICE**: Achieved a Pearson Correlation of **$r = 0.8643$** with an ultra-low inference latency of **$1.729\text{ ms}$**.
* **🚀 EVOLVE**: Enabling continuous, non-invasive hemodynamic monitoring for next-generation digital healthcare.

---

## 🏗️ Model Architecture & Methodology
Optimized to extract robust features from pulsatile pressure data:

1.  **Feature Extraction**: Residual 1D-CNN backbone for deep morphological feature extraction.
2.  **Temporal Modeling**: Bi-LSTM layer to capture long-term hemodynamic context and trends.
3.  **Attention Mechanism**: Integrated attention layers focusing on critical pulse segments (e.g., dicrotic notch).
4.  **Loss Function**: Optimized with **Weighted MSE Loss** to address the class imbalance in high-CO physiological states.

---

## 🚀 Key Performance Metrics
Validated on high-performance infrastructure (i9-14900K / 128GB RAM).

| Metric | Baseline (LSTM) | **Attention-LSTM (Ours)** |
| :--- | :--- | :--- |
| **Correlation ($r$)** | $0.7924$ | **$0.8643$** |
| **Inference Latency** | $1.033\text{ ms}$ | **$1.729\text{ ms}$** |
| **Throughput** | $968\text{ cases/sec}$ | **$578\text{ cases/sec}$** |
| **Clinical Agreement** | Moderate | **Strong (Low Bias)** |

---

## 📊 Visual Analysis & Evidence
![Performance Metrics](images/Quantitative%20Model%20Performance%20Correlation%20%26%20Clinical%20Agreement.png)
*Figure 1. Correlation and Bland-Altman analysis demonstrating high clinical agreement ($r=0.857$).*

![Technical Insight](images/Technical%20Insight%20Error%20Analysis%20%26%20Worst-case%20Outlier%20Detection.png)
*Figure 2. Error diagnostics and worst-case sample analysis used to drive model refinements.*

---

## 🛠️ Installation & Requirements
### Prerequisites
* **Hardware**: High-performance GPU (Recommended: RTX 4070 or higher)
* **Stack**: Python 3.12.10 / PyTorch 2.4.1+cu124 / CUDA 12.4 / cuDNN 9.1.0