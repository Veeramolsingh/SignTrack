# SignTrack: Traffic Sign Detection using YOLOv8


## Project Overview

**SignTrack** is a real‑time traffic sign detection system built on the latest YOLOv8 object‑detection framework. It processes images or video streams (e.g., dashcam, CCTV) to accurately identify and annotate traffic signs—enhancing road‑safety applications in autonomous vehicles and urban monitoring systems.&#x20;

---

## Problem Statement & Scope

* **Goal**: Develop a system that detects and recognizes various traffic signs (e.g., speed limits, stop signs, traffic lights) in real time to support autonomous navigation and road‑safety monitoring.
* **Inputs**: Still images or video streams from dashcams, surveillance cameras, or vehicle sensors.
* **Dataset**: 4,969 annotated traffic‑sign samples, split into training, validation, and test sets.
* **Outputs**: Annotated frames with bounding boxes, class labels, and confidence scores.
* **Target Users**:

  * Autonomous Vehicles & ADAS systems
  * Traffic‑monitoring authorities
  * Urban planners and smart‑city developers&#x20;

---

## Dataset & Preprocessing

1. **Primary Dataset**:

   * “Traffic Sign Detection Dataset” (4,969 images), covering 15 classes including speed limits, stop signs, and traffic lights.
2. **Planned Extensions**:

   * GTSRB (German Traffic Sign Benchmark)
   * Indian Traffic Sign Datasets (multiple sources)
3. **Preprocessing Steps**:

   * Image resizing and normalization
   * Data augmentation (random rotations, brightness adjustments, occlusion simulation) to address class imbalance and lighting variation&#x20;

---

## Model Architecture & Training

* **Base Model**: [Ultralytics YOLOv8](https://github.com/ultralytics/ultralytics)
* **Training Framework**: PyTorch 2.0 with GPU acceleration (Tesla T4 ×2, 16 GB VRAM each)
* **Key Hyperparameters**:

  * Batch sizes: 8, 16, 32, 64
  * Epochs: 10, 50, 100
  * Optimizer: SGD/Adam (tuned per experiment)
* **Loss Components**:

  * Box loss, classification loss, distribution focal loss (DFL)
* **Inference Speed**: \~2.4 ms per image (supporting real‑time use cases)&#x20;

---

## Evaluation Metrics & Results

| Metric            | Overall (%) | Top Classes                              |
| ----------------- | ----------- | ---------------------------------------- |
| **Precision**     | 94.2        | Stop Sign: 97.3, Speed Limits: 92–100    |
| **Recall**        | 90.6        | Stop Sign: 98.8, Speed Limits: 94.1–99.1 |
| **mAP\@0.5**      | 95.7        |                                          |
| **mAP\@0.5–0.95** | 82.97       |                                          |
| **Inference**     | 2.4 ms/img  |                                          |

* **Notable Gaps**:

  * Red Light recall: 69.4%
  * Green Light recall: 74.1%
* **Class Imbalance** and **lighting/occlusion** are key challenges highlighted in error analyses.&#x20;

---
