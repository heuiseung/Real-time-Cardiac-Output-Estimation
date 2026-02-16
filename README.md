# Real-time Cardiac Output (CO) Estimation via Hybrid Attention-LSTM
> **High-fidelity hemodynamic monitoring using VitalDB Arterial Blood Pressure (ABP) waveforms.**

[![Python 3.12](https://img.shields.io/badge/python-3.12.10-blue.svg)](https://www.python.org/downloads/release/python-3120/)
[![PyTorch](https://img.shields.io/badge/PyTorch-2.4.1-EE4C2C?style=flat&logo=pytorch&logoColor=white)](https://pytorch.org/)
[![CUDA](https://img.shields.io/badge/CUDA-12.4-76B900?style=flat&logo=nvidia&logoColor=white)](https://developer.nvidia.com/cuda-toolkit)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 📝 Abstract
This project presents a deep learning-based approach for real-time, non-invasive estimation of **Cardiac Output (CO)**. Using high-fidelity Arterial Blood Pressure (ABP) waveforms from the **VitalDB Open Dataset**, we developed a hybrid model that captures complex hemodynamic patterns. By integrating attention mechanisms, the model prioritizes clinically significant pulse morphologies, achieving high correlation and low latency suitable for intraoperative monitoring.

---

## 💡 Analysis Framework: ASK to EVOLVE
This project follows the **ASK to EVOLVE** analytical framework to bridge raw clinical data with actionable medical AI insights.

* **🔍 ASK**: Can we accurately estimate Cardiac Output (CO) in real-time using only non-invasive ABP waveforms?
* **👀 LOOK**: Analyzed physiological noise and data scarcity in high-flow states within the VitalDB dataset.
* **🔬 INVESTIGATE**: Architected a **Hybrid Attention-LSTM** model to capture temporal morphological features of the ABP pulse while mitigating bias via **Weighted Loss**.
* **📢 VOICE**: Achieved a Pearson Correlation of **$r = 0.8643$** with an ultra-low inference latency of **$1.729\text{ ms}$**.
* **🚀 EVOLVE**: Enabling real-time, continuous hemodynamic monitoring for next-generation patient care systems.

---

## 📊 Dataset Info
This study utilizes the **VitalDB Open Dataset** sourced from the K-Health Data Platform (KHDP).

* **Data Source**: [VitalDB Open Dataset v1.0.0 (KHDP)](https://khdp.net/database/data-search-detail/658/vitaldb_open/1.0.0)
* **Input**: Arterial Blood Pressure (ABP) waveforms sampled at 100Hz.
* **Target**: Continuous Cardiac Output (CO) measurements.
* **Preprocessing**: Physiological artifact removal and patient-wise splitting for clinical generalizability.

---

## 🏗️ Model Architecture
The proposed model integrates CNN and LSTM networks with an attention mechanism to extract robust hemodynamic features:

1.  **Feature Extraction**: A 1D-CNN backbone (Residual Blocks) captures essential pulse wave characteristics (SBP, DBP, MAP equivalent features).
2.  **Temporal Modeling**: A Bidirectional LSTM (Bi-LSTM) layer processes the sequence to understand the hemodynamic context over time.
3.  **Attention Mechanism**: An integrated Attention layer assigns weights to specific time steps, focusing on the systolic phase and dicrotic notch.
4.  **Optimization**: Trained with **Weighted MSE Loss** to address the scarcity of high-CO samples.

---

## 🚀 Key Performance Metrics
Validated on a high-performance workstation (i9-14900K / 128GB RAM).

| Metric | Baseline (LSTM) | **Attention-LSTM (Ours)** |
| :--- | :--- | :--- |
| **Correlation ($r$)** | $0.7924$ | **$0.8643$** |
| **Inference Latency** | $1.033\text{ ms}$ | **$1.729\text{ ms}$** |
| **Throughput** | $968\text{ cases/sec}$ | **$578\text{ cases/sec}$** |
| **Clinical Agreement** | Moderate | **Strong (Low Bias)** |

---

## 📊 Visual Analysis & Evidence

### 1. Model Validation & Clinical Agreement
![Performance Metrics](images/Quantitative%20Model%20Performance%20Correlation%20%26%20Clinical%20Agreement.png)
*Figure 1. (Left) Correlation Plot showing strong linear alignment ($r=0.857$). (Right) Bland-Altman Plot proving clinical agreement with minimal bias.*

### 2. Real-time Inference Scenarios
![Inference Samples](images/Real-time%20Inference%20Examples%20Waveform%20to%20Cardiac%20Output.png)
*Figure 2. Inference samples demonstrating stable and accurate prediction across various pressure morphologies.*

### 3. Robustness & Error Diagnostics
![Technical Insight](images/Technical%20Insight%20Error%20Analysis%20%26%20Worst-case%20Outlier%20Detection.png)
*Figure 3. Residual distribution and worst-case sample analysis used to drive model refinements and attention layer optimization.*

---

## 🛠️ Computing Environment
Optimized for high-speed clinical data processing and large-scale model training.

* **CPU**: Intel Core i9-14900K (24 Cores / 32 Threads)
* **RAM**: 128GB DDR5 (High-capacity caching for VitalDB streaming)
* **GPU**: NVIDIA GeForce RTX 4070
* **Technical Stack**: 
    * Python : 3.12.10
    * PyTorch : 2.4.1+cu124
    * CUDA : 12.4
    * cuDNN : 9.1.0 (90100)

---

## 📁 Repository Structure
```bash
├── Real-time cardiac output estimation.ipynb   # Comprehensive research workflow
├── images/                                     # High-resolution performance visualizations & plots
└── README.md                                   # Project documentation