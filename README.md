# Real-time Cardiac Output (CO) Estimation via Hybrid Attention-LSTM
> **High-fidelity hemodynamic monitoring using VitalDB Arterial Blood Pressure (ABP) waveforms.**

[![Python 3.12](https://img.shields.io/badge/python-3.12.10-blue.svg)](https://www.python.org/downloads/release/python-3120/)
[![PyTorch](https://img.shields.io/badge/PyTorch-2.4.1-EE4C2C?style=flat&logo=pytorch&logoColor=white)](https://pytorch.org/)
[![CUDA](https://img.shields.io/badge/CUDA-12.4-76B900?style=flat&logo=nvidia&logoColor=white)](https://developer.nvidia.com/cuda-toolkit)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

## 📝 Abstract
This project presents a deep learning-based framework for **Real-time Cardiac Output (CO) Estimation** using non-invasive Arterial Blood Pressure (ABP) waveforms. Continuous CO monitoring is critical for intraoperative hemodynamic stability but often relies on invasive catheters. By leveraging the **VitalDB Open Dataset**, we developed a **Hybrid Attention-LSTM** model that captures complex morphological features from pulse waves. The model achieves laboratory-grade accuracy with ultra-low latency, offering a promising solution for scalable, non-invasive patient monitoring systems.

---

## 🖥️ Environment (Hardware)
This research was conducted on a high-performance workstation optimized for large-scale clinical data processing.

* **CPU** : Intel Core i9-14900K (24 Cores / 32 Threads)
* **RAM** : 128GB DDR5 (High-capacity caching for 100Hz waveform streaming)
* **GPU** : NVIDIA GeForce RTX 4070
* **Software Stack** :
    * Python 3.12.10
    * PyTorch 2.4.1+cu124
    * CUDA 12.4 / cuDNN 9.1.0

---

## 📊 Dataset
The study utilizes high-fidelity intraoperative biosignals from the **VitalDB Open Dataset** (sourced via KHDP).

* **Data Source**: [VitalDB Open Dataset v1.0.0](https://khdp.net/database/data-search-detail/658/vitaldb_open/1.0.0)
* **Input**: Arterial Blood Pressure (ABP) waveforms sampled at **100Hz**.
* **Target**: Continuous Cardiac Output (CO) measurements based on Vigileo/FloTrac.
* **Preprocessing**:
    * Physiological artifact removal (e.g., dampening, motion noise).
    * Patient-wise splitting to ensure clinical generalizability (Train/Val/Test).

---

## 🏗️ Model Architecture
The **Hybrid Attention-LSTM** is designed to extract both local morphological features and long-term temporal dependencies:

1.  **Feature Extraction (1D-CNN)**: A Residual CNN backbone extracts pulse wave characteristics (SBP, DBP, MAP equivalents) from raw waveforms.
2.  **Temporal Modeling (Bi-LSTM)**: A Bidirectional LSTM layer captures hemodynamic trends and context over time.
3.  **Attention Mechanism**: An integrated attention layer assigns importance weights to critical pulse segments (e.g., dicrotic notch).
4.  **Optimization**: Trained with **Weighted MSE Loss** to address the class imbalance in high-CO physiological states.

---

## 📈 Results
### Performance Metrics
| Metric | Baseline (LSTM) | **Attention-LSTM** |
| :--- | :--- | :--- |
| **Correlation ($r$)** | $0.7924$ | **$0.8643$** |
| **Inference Latency** | $1.033\text{ ms}$ | **$1.729\text{ ms}$** |
| **Throughput** | $968\text{ cases/sec}$ | **$578\text{ cases/sec}$** |
| **Clinical Agreement** | Moderate | **Strong (Low Bias)** |

### Visual Analysis
**1. Correlation & Clinical Agreement**
![Performance Metrics](images/Quantitative%20Model%20Performance%20Correlation%20%26%20Clinical%20Agreement.png)
*Figure 1. The model demonstrates a strong linear relationship ($r=0.857$) and minimal bias in Bland-Altman analysis.*

**2. Real-time Inference Scenarios**
![Inference Samples](images/Real-time%20Inference%20Examples%20Waveform%20to%20Cardiac%20Output.png)
*Figure 2. Stable CO estimation across various pressure ranges and waveform morphologies.*

**3. Error Diagnostics**
![Technical Insight](images/Technical%20Insight%20Error%20Analysis%20%26%20Worst-case%20Outlier%20Detection.png)
*Figure 3. Residual analysis used to identify and mitigate errors in extreme physiological states.*

---

## 🔑 Key Features: ASK to EVOLVE
This project follows the **ASK to EVOLVE** analytical framework:

* **Precision** : High correlation ($r > 0.86$) comparable to invasive clinical standards.
* **Speed** : Ultra-low latency ($< 2\text{ ms}$) enabling real-time critical care applications.
* **Robustness** : Effective handling of physiological noise and artifacts via attention mechanisms.
* **Scalability** : Lightweight architecture suitable for deployment in centralized monitoring systems.

---

## 📁 Repository Structure
```bash
├── Real-time cardiac output estimation.ipynb   # End-to-end research workflow
├── images/                                     # Performance visualizations & plots
├── LICENSE                                     # MIT License
└── README.md                                   # Project documentation