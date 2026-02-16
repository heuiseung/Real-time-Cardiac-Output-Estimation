# Real-time Cardiac Output (CO) Estimation via Hybrid Attention-LSTM
> **Non-invasive hemodynamic monitoring using VitalDB Arterial Blood Pressure (ABP) waveforms.**

본 프로젝트는 VitalDB 임상 데이터를 활용하여, 동맥압(ABP) 파형으로부터 실시간으로 심박출량을 추정하는 고성능 딥러닝 모델을 구축한 연구입니다.

---

## 💡 Analysis Framework: ASK to EVOLVE

* **🔍 ASK**: ABP 파형만으로 실시간 심박출량을 정확하게 추정할 수 있는가?
* **👀 LOOK**: 데이터 내 노이즈와 고출력 구간($\text{CO} > 40$)의 불균형을 확인했습니다.
* **🔬 INVESTIGATE**: Attention Mechanism과 Weighted Loss로 노이즈 강건성 및 편향을 해결했습니다.
* **📢 VOICE**: 상관계수 $r = 0.8643$ 및 $1.729\text{ ms}$의 초저지연 성능을 달성했습니다.
* **🚀 EVOLVE**: 향후 중앙 집중식 관제 시스템으로의 확장 및 모델 경량화를 제안합니다.

---

## 🚀 Key Metrics & Environment

| Metric | Value | Context |
| :--- | :--- | :--- |
| **Correlation ($r$)** | **$0.8643$** | Patient-wise 5-Fold Validation |
| **Inference Latency** | **$1.729\text{ ms}$** | Real-time ready (on RTX 4070) |
| **CPU / RAM** | **i9-14900K / 128GB** | High-performance Caching |

---

## 📁 Repository Structure
* `Real-time cardiac output estimation.ipynb`: 전체 분석 파이프라인
* `images/`: 상관계수, Attention Heatmap 등 시각화 리포트