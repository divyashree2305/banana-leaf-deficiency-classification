# Nutrient Deficiency Detection in Banana Plants Using Deep Learning

## Project Overview
This project presents a deep learning–based approach for detecting nutrient deficiencies in banana plant leaves using image classification techniques. Multiple pretrained Convolutional Neural Network (CNN) architectures were fine-tuned and evaluated, and an ensemble learning strategy was employed to improve robustness and generalization under real-world agricultural conditions such as varying illumination, background noise, and image quality.

The system classifies banana leaf images into nine categories (eight nutrient deficiencies and one healthy class) and provides interpretable outputs including symptom descriptions and recommended corrective actions.

---

## Objectives
- Detect nutrient deficiencies from banana leaf images  
- Improve generalization using ensemble prediction strategies  
- Handle real-world variations in agricultural imagery  
- Provide actionable agronomic insights along with predictions  

---

## Models Used
The following pretrained CNN architectures were used and fine-tuned using TensorFlow and Keras:

- MobileNetV2  
- ResNet50V2  
- InceptionV3  

Each model was trained independently before being incorporated into the ensemble prediction pipeline.

---

## Dataset
- **Dataset Name:** Images of Nutrient Deficient Banana Plant Leaves  
- **Total Images:** 7,000+  
- **Number of Classes:** 9  
  - Boron deficiency  
  - Calcium deficiency  
  - Iron deficiency  
  - Magnesium deficiency  
  - Manganese deficiency  
  - Potassium deficiency  
  - Sulphur deficiency  
  - Zinc deficiency  
  - Healthy  

**Dataset Source:**  
https://www.sciencedirect.com/science/article/pii/S2352340923002743

---

## Data Preprocessing
The preprocessing pipeline implemented in the training notebook includes:

- Dataset splitting into training, validation, and test sets  
- Detection and removal of corrupted images  
- Image format standardization (conversion to JPG)  
- Image resizing with model-specific interpolation strategies  
- Normalization and preprocessing using architecture-specific functions  
- Data augmentation techniques such as rotation, shifting, zooming, and flipping  

These steps ensure consistent and high-quality input data across all models.

---

## Model Training
- **Framework:** TensorFlow / Keras  
- **Loss Function:** Categorical Cross-Entropy  
- **Optimizer:** Adam  
- **Evaluation Metric:** Accuracy  
- **Training Strategy:** Transfer learning with partial layer freezing  
- **Callbacks Used:**  
  - Early Stopping  
  - Reduce Learning Rate on Plateau  

Each model was trained independently, and the trained weights were saved in `.h5` format for inference and ensemble learning.

---

## Model Performance

**Table 1. Performance Metrics of Individual Models**

| Model        | Training Accuracy | Training Loss | Validation Accuracy | Validation Loss |
|-------------|------------------|---------------|---------------------|-----------------|
| ResNet50V2  | 80.07%           | 0.5525        | 66.70%              | 1.0832          |
| MobileNetV2 | 79.71%           | 0.5571        | 75.13%              | 0.7942          |
| InceptionV3 | 70.90%           | 0.8016        | 68.83%              | 0.8697          |

MobileNetV2 achieved the highest validation accuracy among the individual models, while the ensemble approach further improved robustness and consistency on unseen data.

---

## Ensemble Learning Strategy
To improve real-world performance, predictions from multiple CNN models were combined using a weighted averaging approach:

Final Prediction = 0.4 × MobileNetV2 + 0.3 × ResNet50V2 + 0.3 × InceptionV3


This ensemble strategy reduces model-specific bias, improves generalization, and enhances robustness under varying field conditions.

---

## Inference and Decision Support
For each input banana leaf image, the system produces:
- Predicted nutrient deficiency (or healthy class)  
- Confidence score of the prediction  
- Description of visible symptoms  
- Recommended corrective actions, including fertilizer and soil management suggestions  

This transforms the system from a pure classifier into a practical decision-support tool for precision agriculture.

---

## User Interface
A Gradio-based interface is implemented to allow users to:
- Upload banana leaf images  
- Receive predicted nutrient deficiency results  
- View symptoms and recommended corrective actions interactively  

---

## Technology Stack
- **Programming Language:** Python  
- **Deep Learning Framework:** TensorFlow, Keras  
- **CNN Architectures:** MobileNetV2, ResNet50V2, InceptionV3  
- **Supporting Libraries:** NumPy, PIL, Matplotlib, Scikit-learn  
- **Web Interface:** Gradio  

---

## Important Note
**The provided notebooks are not directly runnable out-of-the-box.**  
Dataset paths, model paths, and certain local variables must be manually configured according to the user’s local file system and execution environment before training or inference.