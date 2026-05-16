# Part 2: CNN Implementation for Industrial Quality Control

## Project Overview
This project implements a Deep Learning solution for automated quality control. Using a **Convolutional Neural Network (CNN)**, the system identifies and classifies surface defects on components into four categories: **Dent**, **Normal**, **Scratch**, and **Stain**. This replaces inconsistent manual inspection with high-speed, objective AI diagnostics.

## 1. Project Objectives
The primary goal was to transition from basic image classification to a robust industrial-grade model. Key objectives included:
* **Reducing Waste:** Identifying flaws early to prevent further processing of defective parts.
* **Consistency:** Eliminating human fatigue and subjectivity in visual inspection.
* **Scalability:** Enabling 24/7 monitoring of high-speed assembly lines through automated detection.

## 2. Technical Architecture
The model is a Sequential CNN designed to extract complex spatial features from schematic industrial images.

### 2.1 Feature Extraction
* **Input Layer:** 128x128 RGB images.
* **Three Convolutional Blocks:** Using 32, 64, and 128 filters respectively to capture hierarchical patterns (from simple edges to complex textures).
* **MaxPooling:** Used after each convolution to reduce spatial dimensions, making the model robust to the exact position of the defect.

### 2.2 Classification Head
* **Flatten Layer:** Converts the 14x14x128 feature map into a 1D vector of 25,088 units.
* **Dense Layer (128 neurons):** Interprets the extracted features for final decision making.
* **Dropout (0.3):** Regularization to ensure the model generalizes well to new data rather than memorizing training samples.
* **Softmax Output:** 4 neurons providing the final class probability.

## 3. Performance Metrics
The model was optimized using the Adam optimizer with a custom learning rate (0.0005) to ensure stable convergence and prevent mode collapse.

* **Final Validation Accuracy:** ~95.8%
* **Final Validation Loss:** ~0.11
* **Observations:** The model transitioned from random guessing (23%) to high-precision classification within 12 epochs. The alignment of training and validation curves indicates a healthy training process without overfitting.

## 4. Evaluation Results
The results are stored in the `results/` directory for verification:
* **`accuracy_loss_curves.png`**: Visualizes the smooth learning progression and error reduction.
* **`confusion_matrix.png`**: Confirms high precision across all classes, showing a strong diagonal correlation between actual and predicted labels.
* **`prediction_outputs.png`**: Located in `sample_predictions/`, showing a real-world example of the AI correctly identifying a part.

## 5. Folder Structure
* `notebook.ipynb`: Core implementation, data scrambling, and training pipeline.
* `results/`: Performance visualizations (Loss/Accuracy curves and Heatmaps).
* `sample_predictions/`: Individual test cases showing AI inference in action.
* `Part2_Defect_Report.md`: Full documentation of the project logic.

## Conclusion
This CNN demonstrates that automated defect detection is highly feasible for industrial applications. By achieving **~96% accuracy**, the model provides a scalable, digital alternative to manual inspection, directly improving the efficiency and reliability of the quality assurance lifecycle.