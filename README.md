# AeroSenseNet 🚀

**Physics-Informed Transformer for Predicting Aircraft Maneuvers from Jet Engine Sensor Data**

> A hybrid of Transformer-based sequence modeling and physics-inspired loss functions for interpretable and accurate classification of aircraft maneuver intents using multivariate sensor data from NASA’s C-MAPSS dataset.

---

## 📘 Abstract

This repository contains the code and paper for *AeroSenseNet*, a model that predicts maneuver types : **Cruise**, **Climb**, **Descent**, and **Failure** — using jet engine multivariate time-series. The model combines a Transformer encoder with a **physics-informed loss**, enforcing Newtonian acceleration consistency, and demonstrates improved generalization and interpretability.

---

## 🛠️ Features

- ✅ Transformer-based temporal attention modeling
- ✅ Physics-informed loss using estimated longitudinal acceleration
- ✅ Preprocessed sliding windows over NASA C-MAPSS FD001 dataset
- ✅ Visualization of attention maps and velocity-based labels
- ✅ High classification accuracy: **96.34%**

---

## 📊 Results

| Model          | Accuracy (%) | F1 Score | Precision | Recall  |
|----------------|--------------|----------|-----------|---------|
| Transformer Baseline | 93.21        | 0.914    | 0.920     | 0.911   |
| **AeroSenseNet (Ours)** | **96.34**        | **0.941**    | **0.948**     | **0.938**   |

---

## 🧪 Dataset

- **Name:** [NASA C-MAPSS FD001](https://www.kaggle.com/datasets/behrad3d/nasa-cmaps)
- **Format:** Multivariate time-series of 100 simulated turbofan engines
- **Inputs:** 21 sensor channels + 3 operational settings
- **Labels:** Maneuver intent derived from velocity proxy

---

## 🧠 Model Architecture

- **Input:** Sliding window of 30 timesteps (24 features)
- **Embedding Layer:** Linear + ReLU to 128D
- **Transformer Encoder:** 2 layers, 4 heads, no positional encoding
- **Classifier:** MLP on final timestep
- **Loss:** Cross-entropy + physics-informed regularizer

---

## 📐 Physics-Informed Loss

We estimate a velocity proxy and compute its temporal derivative \( \dot{v} \), then regularize predictions using:

\[
\mathcal{L}_{\text{phys}} = \frac{1}{N} \sum_{i} \left( \dot{v}_{T}^{(i)} - \phi(\hat{y}^{(i)}) \right)^2
\]

Where \( \phi(\hat{y}) \in \{-1, 0, +1\} \) corresponds to descent, cruise, and climb respectively.

---

## 🔧 How to Run

### 🔗 1. Clone this repo:
```bash
git clone https://github.com/satyamcser/AeroSenseNet.git
cd AeroSenseNet
```
---

### 🧪 2. Open the notebook:

Run AeroSenseNet.ipynb in Jupyter or Colab

### 📄 Paper

Accepted at ICTA 2025.

---

### 📝 Review Highlights:

- "Promising and well-executed study"

- "Novel integration of Transformer + Physics constraints"

- "Attention maps reveal temporal maneuver transitions"
---


### 🧑‍💻 Authors

- Sungjoon Cho

- Satyam Mishra

- Vishwanath Bijalwan

- Anchit Bijalwan
---
### 📜 Citation
```bib
@inproceedings{aerosensenet2024,
  title={AeroSenseNet: When Physics Meets Transformers for Predicting Aircraft Maneuvers from Jet Engine Sensors},
  author={Cho, Sungjoon and Mishra, Satyam and Bijalwan, Vishwanath and Bijalwan, Anchit},
  year={2025}
}
```
---
### 🔒 License

Licensed under the MIT License. 
---