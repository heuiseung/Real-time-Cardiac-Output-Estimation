# Real-time Cardiac Output (CO) Estimation via Hybrid Attention-LSTM
> **Non-invasive hemodynamic monitoring using VitalDB Arterial Blood Pressure (ABP) waveforms.**

[![Python 3.12](https://img.shields.io/badge/python-3.12-blue.svg)](https://www.python.org/downloads/release/python-3120/)
[![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat&logo=pytorch&logoColor=white)](https://pytorch.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 💡 Analysis Framework: ASK to EVOLVE
This project follows the **ASK to EVOLVE** framework to bridge the gap between raw clinical data and actionable medical AI insights.

* **🔍 ASK**: Can we accurately estimate Cardiac Output (CO) in real-time using only non-invasive Arterial Blood Pressure (ABP) waveforms?
* **👀 LOOK**: Identified data imbalance in high-CO ranges ($>40$) and significant motion artifacts in raw VitalDB clinical recordings.
* **🔬 INVESTIGATE**: Developed a Hybrid Attention-LSTM architecture. Integrated **Attention Mechanisms** to prioritize morphologically significant pulse segments and **Weighted Loss** to mitigate bias in high-flow states.
* **📢 VOICE**: Achieved a Pearson Correlation Coefficient of **$r = 0.8643$** and an ultra-low inference latency of **$1.729\text{ ms}$**.
* **🚀 EVOLVE**: Proposed a lightweight model deployment for centralized patient monitoring systems and future expansion to multi-modal vital sign fusion.

---

## 🚀 Key Performance Metrics

| Metric | Baseline (LSTM) | **Attention-LSTM (Ours)** |
| :--- | :--- | :--- |
| **Correlation ($r$)** | $0.7924$ | **$0.8643$** |
| **Inference Latency** | $1.033\text{ ms}$ | **$1.729\text{ ms}$** |
| **Throughput** | $968\text{ cases/sec}$ | **$578\text{ cases/sec}$** |
| **Clinical Agreement** | Moderate | **Strong (Low Bias)** |

---

## 📊 Visual Evidence

### 1. Model Validation & Clinical Agreement
![Performance Metrics](images/performance_validation.png)
*Figure 1. (Left) Correlation Plot demonstrating a strong linear relationship ($r=0.857$). (Right) Bland-Altman Plot showing clinical agreement within acceptable limits.*

### 2. Real-time Inference Samples
![Inference Samples](images/inference_samples.png)
*Figure 2. Stable CO estimation across various ABP waveform morphologies and pressure ranges.*

### 3. Error Analysis & Outlier Detection
![Error Analysis](images/error_insights.png)
*Figure 3. Residual analysis used to identify performance bottlenecks in extreme physiological states, driving the implementation of Attention layers.*

---

## 🛠️ Computing Environment
Optimized for high-speed clinical data processing and large-scale model training.
* **CPU**: Intel Core i9-14900K (24 Cores / 32 Threads)
* **RAM**: 128GB DDR5 (High-capacity caching for VitalDB streaming)
* **GPU**: NVIDIA GeForce RTX 4070
* **OS**: Windows 11 Pro / CUDA 12.1

---

## 📁 Repository Structure
* `Real-time cardiac output estimation.ipynb`: Full end-to-end pipeline (Preprocessing to Evaluation).
* `images/`: Performance visualization and error analysis reports.
* `README.md`: Project documentation and analysis summary.

---

## 📜 Acknowledgement
Data provided by **VitalDB**, an open dataset for clinical research.  
*Reference: Lee, HC., Jung, CW. VitalDB, a high-fidelity multi-parameter vital signs database in surgical patients. Sci Data 5, 180184 (2018).*