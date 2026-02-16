# Real-time Cardiac Output (CO) Estimation via Hybrid Attention-LSTM
> **High-fidelity hemodynamic monitoring using VitalDB Arterial Blood Pressure (ABP) waveforms.**

[![Python 3.12](https://img.shields.io/badge/python-3.12.10-blue.svg)](https://www.python.org/downloads/release/python-3120/)
[![PyTorch](https://img.shields.io/badge/PyTorch-2.4.1-EE4C2C?style=flat&logo=pytorch&logoColor=white)](https://pytorch.org/)
[![CUDA](https://img.shields.io/badge/CUDA-12.4-76B900?style=flat&logo=nvidia&logoColor=white)](https://developer.nvidia.com/cuda-toolkit)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

## 📝 Abstract
This project presents a deep learning-based approach for real-time, non-invasive estimation of **Cardiac Output (CO)**. Using high-fidelity ABP waveforms from the **VitalDB Open Dataset**, we developed a hybrid model that captures complex hemodynamic patterns. By integrating attention mechanisms, the model prioritizes clinically significant pulse morphologies, achieving high correlation and low latency suitable for intraoperative monitoring.

---

## 💡 Analysis Framework: ASK to EVOLVE
Following the **ASK to EVOLVE** framework used in previous hypotension prediction research, this project bridges raw clinical data with actionable AI insights.

* **🔍 ASK**: Can we accurately estimate Cardiac Output (CO) in real-time using only non-invasive ABP waveforms?
* **👀 LOOK**: Analyzed physiological noise and data scarcity in high-flow states within the VitalDB dataset.
* **🔬 INVESTIGATE**: Architected a **Hybrid Attention-LSTM** model to capture temporal morphological features while mitigating bias via **Weighted Loss**.
* **📢 VOICE**: Achieved a Pearson Correlation of **$r = 0.8643$** with an ultra-low inference latency of **$1.729\text{ ms}$**.
* **🚀 EVOLVE**: Enabling continuous, non-invasive hemodynamic monitoring for next-generation patient care.

---

## 🏗️ Model Architecture
The model is optimized to extract robust features from pulsatile pressure data:
1.  **Feature Extraction**: Residual 1D-CNN backbone for pulse wave characteristic extraction.
2.  **Temporal Modeling**: Bi-LSTM layer to understand long-term hemodynamic context.
3.  **Attention Mechanism**: Integrated layer to focus on clinically critical segments like the dicrotic notch.
4.  **Optimization**: Trained with **Weighted MSE Loss** to address high-CO sample scarcity.

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

## 📊 Visual Analysis
![Performance Metrics](images/Quantitative%20Model%20Performance%20Correlation%20%26%20Clinical%20Agreement.png)
*Figure 1. Correlation and Bland-Altman analysis demonstrating high clinical agreement ($r=0.857$).*

---

## 🛠️ Computing Environment
* **CPU** : Intel Core i9-14900K (24 Cores / 32 Threads)
* **RAM** : 128GB DDR5 (High-speed caching for data streaming)
* **GPU** : NVIDIA GeForce RTX 4070
* **Technical Stack** : Python 3.12.10 / PyTorch 2.4.1+cu124 / CUDA 12.4 / cuDNN 9.1.0

---

## 📁 Repository Structure
* `Real-time cardiac output estimation.ipynb`: Comprehensive research workflow (Preprocessing to Evaluation).
* `images/`: High-resolution performance visualizations and technical analysis plots.
* `LICENSE`: MIT License.

---

## 📜 License
This project is licensed under the **MIT License**. See the [LICENSE](LICENSE) file for details.

## 🔗 Data Source
* **VitalDB Open Dataset**: [KHDP VitalDB v1.0.0](https://khdp.net/database/data-search-detail/658/vitaldb_open/1.0.0)