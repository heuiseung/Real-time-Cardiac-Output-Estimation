# Real-time Cardiac Output (CO) Estimation via Hybrid Attention-LSTM
> **High-fidelity hemodynamic monitoring using VitalDB Arterial Blood Pressure (ABP) waveforms.**

[![Python 3.12](https://img.shields.io/badge/python-3.12-blue.svg)](https://www.python.org/downloads/release/python-3120/)
[![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat&logo=pytorch&logoColor=white)](https://pytorch.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 💡 Analysis Framework: ASK to EVOLVE
This repository implements a deep learning pipeline to estimate Cardiac Output (CO) from non-invasive ABP waveforms, following the **ASK to EVOLVE** analytical framework.

* **🔍 ASK**: 
Can we achieve laboratory-grade CO estimation accuracy using only non-invasive waveform data?
* **👀 LOOK**: 
Analyzed physiological noise and data scarcity in high-flow states within the VitalDB dataset.
* **🔬 INVESTIGATE**: 
Architected a **Hybrid Attention-LSTM** model to capture temporal morphological features of the ABP pulse while mitigating bias via **Weighted Loss**.
* **📢 VOICE**: 
Achieved a Pearson Correlation of **$r = 0.8643$** with an ultra-low inference latency of **$1.729\text{ ms}$**.
* **🚀 EVOLVE**: 
Enabling real-time, continuous hemodynamic monitoring for next-generation patient care systems.

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
* **CPU**: Intel Core i9-14900K (24 Cores / 32 Threads)
* **RAM**: 128GB DDR5 (Optimized for high-speed data streaming)
* **GPU**: NVIDIA GeForce RTX 4070
* **OS**: Windows 11 Pro / CUDA 12.1

---

## 📁 Repository Structure
* `Real-time cardiac output estimation.ipynb`: Full end-to-end research pipeline.
* `images/`: High-resolution performance **visualizations** and analysis **plots**.
* `README.md`: Project documentation and analysis summary.

---

## 📜 Acknowledgement
Data provided by **VitalDB**, an open dataset for clinical research.  
*Reference: Lee, HC., Jung, CW. VitalDB, a high-fidelity multi-parameter vital signs database in surgical patients. Sci Data 5, 180184 (2018).*