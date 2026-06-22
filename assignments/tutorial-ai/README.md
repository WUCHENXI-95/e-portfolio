# Assignment 4 — Tutorial: AI Algorithm (CNN Image Classification)

**SECP3843: Special Topic in Data Engineering** | UTM, Semester 2 2025/2026

---

## Overview

| Item | Details |
|------|---------|
| **Format** | Lab Tutorial Report |
| **Topic** | AI — CNN Image Classification on CIFAR-10 |
| **Team** | Nur Firzana, Nuraisyah, Wu Chenxi |
| **Lecturer** | Dr. Aryati Binti Bakri |
| **Environment** | Google Colab (Python, TensorFlow/Keras) |

[📄 View Full Report (PDF)](./tutorial-ai-report.pdf)

---

## Project Summary

**Goal:** Build and compare image classification models on the CIFAR-10 dataset — starting with an ANN baseline, then an original CNN, and finally an enhanced CNN with optimisation techniques.

**Dataset:** CIFAR-10 — 60,000 colour images (32x32 pixels) across 10 classes (airplane, automobile, bird, cat, deer, dog, frog, horse, ship, truck). 50,000 training + 10,000 test images.

### What is Image Classification?

A computer vision task where a model predicts which class an image belongs to. Applications include medical imaging, self-driving cars, and facial recognition.

### What is CNN?

A Convolutional Neural Network uses convolution layers to learn spatial features (edges, shapes, textures) and pooling layers to reduce dimensions while retaining important information. CNN outperforms traditional ANN for image data because it preserves spatial structure.

### Implementation Steps

| Step | Description |
|------|-------------|
| 1 | Import libraries (TensorFlow, Keras, NumPy, Matplotlib, Seaborn, sklearn) |
| 2 | Load and explore CIFAR-10 dataset |
| 3 | Visualise sample images |
| 4 | Normalise pixel values from [0,255] to [0.0, 1.0] |
| 5 | Build ANN baseline (2 dense layers, ~49% accuracy) |
| 6 | Build original CNN (2 Conv blocks, 10 epochs) |
| 7 | Evaluate original CNN (~45% accuracy — underperformed) |
| 8 | Visualise predictions |

### Model Comparison

| Feature | Original CNN | Enhanced CNN |
|---------|-------------|-------------|
| Conv Blocks | 2 | 3 |
| Filter Progression | 32 → 64 | 32 → 64 → 128 |
| Batch Normalization | Not used | Applied after every Conv layer |
| Dropout | Not used | 0.25 after pooling, 0.5 before output |
| Data Augmentation | Not applied | Rotation, flip, shift (ImageDataGenerator) |
| Dense Layer Size | 64 | 256 |
| Training Epochs | 10 | 20 |
| **Test Accuracy** | **45%** | **82%** |

### Enhancements Applied to new_CNN

1. **Data Augmentation** — Rotation (15°), horizontal/vertical shift (10%), random horizontal flip to increase training diversity
2. **Deeper Architecture** — 3 Conv blocks with 128 filters and 'same' padding to preserve spatial resolution
3. **Batch Normalization** — After every Conv2D layer to accelerate convergence and stabilise learning
4. **Dropout** — 0.25 after pooling layers, 0.5 before output to prevent overfitting
5. **Extended Training** — 20 epochs with augmented data for better generalisation

### Key Findings

- The original CNN suffered from **overfitting** due to no Dropout and no Data Augmentation
- Without Batch Normalization, learning was **unstable and slow to converge**
- The enhanced model raised accuracy from **45% to 82%** through architectural and training strategy improvements
- Per-class metrics (precision, recall, F1-score) provide deeper insight than overall accuracy alone

---

## Reflection

### What I Learned

This tutorial gave me valuable hands-on experience in building and optimising convolutional neural networks for image classification. I started with a basic ANN that ignored spatial structure and achieved only around 49% accuracy, which helped me understand why CNN layers are essential for image data. When the original CNN reached only 45% accuracy, I had to critically analyse what went wrong — limited depth, no regularisation, and training on static images only. Applying enhancements like Batch Normalization, Dropout, and Data Augmentation pushed the accuracy to 82%, which showed me that model performance depends not just on architecture design but equally on effective training strategies. I also learned to look beyond overall accuracy and interpret per-class metrics like precision, recall, and F1-score, since they reveal where the model struggles with specific categories.

### Areas for Improvement

- I should experiment with **more epochs and learning rate schedules** to see if the enhanced model can improve further beyond 82%.
- I relied heavily on following the tutorial steps and need to spend more time **understanding why each layer and parameter was chosen**, not just how to implement it.
- I could explore **transfer learning** with pre-trained models like ResNet or VGG to compare against our custom CNN architecture.

### Personal Takeaway

Building a deep learning model is an iterative process — the first attempt rarely works well. What matters is the ability to diagnose weaknesses, apply targeted fixes, and evaluate results critically. This tutorial taught me that making the training environment harder (through Dropout and Augmentation) actually forces the model to become smarter and more adaptable, which is a principle I will carry forward into future machine learning projects.

---

[⬅ Back to Home](../../index.md)
