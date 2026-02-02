# HVI-Diff: Physically Decoupled Interactive Diffusion for Low-Light Image Enhancement

This repository contains the official PyTorch implementation of the paper: **"HVI-Diff: Physically Decoupled Interactive Diffusion for Low-Light Image Enhancement"**.

## 📖 Introduction

Low-light image enhancement (LLIE) is challenging due to the complex entanglement of illumination degradation and chromatic distortion. While diffusion models excel at generation, they often struggle with color shifts and structural hallucinations in the RGB space.

**HVI-Diff** is a novel framework that integrates physical priors with diffusion models. By introducing the **HVI color space**, we explicitly decouple the input into **Intensity** and **Chromaticity** components. Our method features:

* **Parallel Convolutional Coarse Module (PCCM)**: Provides deterministic physical anchors for stable restoration.
* **Physically Decoupled Interactive Diffusion (PDID)**: A dual-stream diffusion module for stochastic refinement of details.
* **Interaction Factor (IF)**: A mechanism to dynamically bridge the two streams, ensuring structural and chromatic consistency.

*Figure: The overall architecture of HVI-Diff.*

## ⚡ Quick Start

### 1. Installation

Clone this repository and install the dependencies:

```bash
git clone https://github.com/HVI-Diff-Project/HVI-Diff.git
cd HVI-Diff
pip install -r requirements.txt

```

**Requirements:**

* Python >= 3.8
* PyTorch >= 1.10
* NVIDIA GPU + CUDA

### 2. Data Preparation

Download the datasets (LOLv1, LOLv2-Real, etc.) and organize them as follows:

```
data/
  LOLv1/
    train/
      low/
      high/
    test/
      low/
      high/
  ...

```

### 3. Training

To train the model on the LOLv1 dataset:

```bash
python train.py --config configs/train_lolv1.yaml

```

### 4. Inference / Testing

To evaluate on the test set using a pre-trained model:

```bash
python test.py --input_dir data/LOLv1/test/low --weights checkpoints/hvi_diff_best.pth

```

## 📊 Results

HVI-Diff achieves state-of-the-art performance on multiple benchmarks.

| Method | LOLv1 (PSNR/SSIM) | LOLv2-Real (PSNR/SSIM) |
| --- | --- | --- |
| Retinexformer | 27.14 / 0.85 | 22.79 / 0.84 |
| Diff-Retinex++ | 24.67 / 0.87 | 23.41 / 0.87 |
| **HVI-Diff (Ours)** | **27.26 / 0.87** | **23.80 / 0.86** |


## 📧 Contact

For any questions, please open an issue or contact shaoyangchp@gmail.com.
