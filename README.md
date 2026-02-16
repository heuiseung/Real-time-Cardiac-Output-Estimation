# Real-time Cardiac Output (CO) Estimation via Hybrid Attention-LSTM
> **Non-invasive hemodynamic monitoring using VitalDB Arterial Blood Pressure (ABP) waveforms.**

[![Python 3.12](https://img.shields.io/badge/python-3.12-blue.svg)](https://www.python.org/downloads/release/python-3120/)
[![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat&logo=pytorch&logoColor=white)](https://pytorch.org/)

## 💡 Analysis Framework: ASK to EVOLVE

* **🔍 ASK**: Can we accurately estimate Cardiac Output (CO) in real-time using only non-invasive ABP waveforms?
* **👀 LOOK**: Observed data imbalance in high-CO ranges and motion artifacts in raw clinical data.
* **🔬 INVESTIGATE**: Implemented a Hybrid Attention-LSTM to prioritize significant pulse segments and mitigate high-flow bias.
* **📢 VOICE**: Achieved a Pearson Correlation of **$r = 0.8643$** with an ultra-low latency of **$1.729\text{ ms}$**.
* **🚀 EVOLVE**: Expanding toward multi-modal vital sign fusion for centralized monitoring systems.

---

## 🚀 Model Performance & Validation

### 1. Quantitative Metrics
![Performance Metrics](images/Quantitative%20Model%20Performance%20Correlation%20%26%20Clinical%20Agreement.png)
*Figure 1. Performance Validation Report. (Left) Correlation Plot ($r=0.857$). (Right) Bland-Altman Plot demonstrating strong clinical agreement with a mean difference of 0.11 L/min.*

### 2. Real-time Inference Results
![Inference Samples](images/Real-time%20Inference%20Examples%20Waveform%20to%20Cardiac%20Output.png)
*Figure 2. Sample-wise inference showcasing stable CO prediction across diverse ABP morphologies.*

---

## 🛡️ Robustness & Error Analysis

### 1. Signal Robustness against Clinical Artifacts
![Robustness](images/Signal%20Robustness%20Analysis%20Artifacts%20in%20Clinical%20Data.png)
*Figure 3. Validation of model stability against physiological spikes and motion artifacts within VitalDB recordings.*

### 2. Deep Dive: Outlier Analysis
![Technical Insight](images/Technical%20Insight%20Error%20Analysis%20%26%20Worst-case%20Outlier%20Detection.png)
*Figure 4. Identifying performance bottlenecks through residual analysis and investigation of the worst-performing samples (Error: 49.13).*

---

## 🛠️ Computing Environment & Troubleshooting
* **CPU**: Intel Core i9-14900K (24 Cores)
* **RAM**: 128GB DDR5 (Optimized for Large-scale Data Streaming)
* **GPU**: NVIDIA GeForce RTX 4070

### Deployment Logs
![Git Logs](images/Git%20Repository%20Initialization%20%26%20Remote%20Configuration%20Logs.png)
*Figure 5. Systematic resolution of repository initialization and remote configuration challenges.*

---

## 📁 Repository Structure
* `Real-time cardiac output estimation.ipynb`: Full end-to-end pipeline.
* `images/`: High-resolution performance and analysis reports.