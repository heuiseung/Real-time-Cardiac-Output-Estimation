# Real-time Cardiac Output (CO) Estimation via Hybrid Attention-LSTM
> **High-fidelity hemodynamic monitoring using VitalDB Arterial Blood Pressure (ABP) waveforms.**

[![Python 3.12](https://img.shields.io/badge/python-3.12.10-blue.svg)](https://www.python.org/downloads/release/python-3120/)
[![PyTorch](https://img.shields.io/badge/PyTorch-2.4.1-EE4C2C?style=flat&logo=pytorch&logoColor=white)](https://pytorch.org/)
[![CUDA](https://img.shields.io/badge/CUDA-12.4-76B900?style=flat&logo=nvidia&logoColor=white)](https://developer.nvidia.com/cuda-toolkit)

## 📝 Abstract
This project presents a deep learning-based approach for real-time, non-invasive estimation of **Cardiac Output (CO)**. Using high-fidelity Arterial Blood Pressure (ABP) waveforms from the **VitalDB** open dataset, we developed a hybrid model that captures complex hemodynamic patterns. By integrating attention mechanisms, the model prioritizes clinically significant pulse morphologies, achieving high correlation and low latency suitable for intraoperative monitoring.

---

## 💡 Analysis Framework: ASK to EVOLVE
Following the **ASK to EVOLVE** framework, this project bridges raw clinical data with actionable AI insights.

* **🔍 ASK**: Can we accurately estimate Cardiac Output (CO) in real-time using only non-invasive ABP waveforms?
* **👀 LOOK**: Identified data imbalance in high-CO ranges and significant physiological noise in raw clinical recordings.
* **🔬 INVESTIGATE**: Architected a **Hybrid Attention-LSTM** to prioritize systolic phase morphologies and mitigate high-flow bias via **Weighted Loss**.
* **📢 VOICE**: Achieved a Pearson Correlation of **$r = 0.8643$** with an ultra-low inference latency of **$1.729\text{ ms}$**.
* **🚀 EVOLVE**: Proposed lightweight deployment for centralized patient monitoring systems and multi-modal vital sign fusion.

---

## 🏗️ Model Architecture
The model captures both local morphological features and long-term temporal dependencies:
1.  **Feature Extraction**: 1D-CNN backbone for pulse wave characteristic extraction (SBP, DBP, MAP equivalents).
2.  **Temporal Modeling**: Bidirectional LSTM (Bi-LSTM) to capture hemodynamic context over time.
3.  **Attention Mechanism**: Focuses on clinically critical segments like the dicrotic notch for precise CO estimation.
4.  **Optimization**: Weighted MSE Loss to address the scarcity of high-CO samples.

---

## 📊 Visual Analysis & Evidence

### 1. Model Validation & Clinical Agreement
![Performance Metrics](images/Quantitative%20Model%20Performance%20Correlation%20%26%20Clinical%20Agreement.png)
*Figure 1. (Left) Correlation Plot ($r=0.857$). (Right) Bland-Altman Plot demonstrating strong clinical agreement with minimal bias.*

### 2. Real-time Inference Scenarios
![Inference Samples](images/Real-time%20Inference%20Examples%20Waveform%20to%20Cardiac%20Output.png)
*Figure 2. Inference samples demonstrating stable and accurate prediction across various pressure morphologies.*

### 3. Robustness & Error Diagnostics
![Technical Insight](images/Technical%20Insight%20Error%20Analysis%20%26%20Worst-case%20Outlier%20Detection.png)
*Figure 3. Residual distribution and worst-case sample analysis used to drive model refinements and attention layer optimization.*

---

## 🛠️ Computing Environment
* **CPU**: Intel Core i9-14900K (24 Cores / 32 Threads)
* **RAM**: 128GB DDR5 (Optimized for high-speed clinical data processing)
* **GPU**: NVIDIA GeForce RTX 4070
* **Technical Stack**: Python 3.12.10 / PyTorch 2.4.1+cu124 / CUDA 12.4 / cuDNN 9.1.0 (90100)

---

## 📁 Repository Structure
* **`Real-time cardiac output estimation.ipynb`**: Comprehensive research workflow covering data engineering, model training, and clinical performance evaluation.
* **`images/`**: High-resolution performance visualizations and technical analysis plots.
* **`README.md`**: Project documentation and analysis summary.

---

## 📜 Acknowledgement
Data provided by **VitalDB**, an open dataset for clinical research.  
*Reference: Lee, HC., Jung, CW. VitalDB, a high-fidelity multi-parameter vital signs database in surgical patients. Sci Data 5, 180184 (2018).*