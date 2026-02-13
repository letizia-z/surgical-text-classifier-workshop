![Jupyter Notebook](https://img.shields.io/badge/uses-Jupyter%20Notebook-orange?logo=jupyter)
![fastText](https://img.shields.io/badge/library-fastText-darkgreen)
![Python](https://img.shields.io/badge/python-3.10-blue?style=flat&logo=python&logoColor=white)
![NumPy](https://img.shields.io/badge/numpy-%3C%202.0-cyan?style=flat&logo=numpy&logoColor=white)
![Pandas](https://img.shields.io/badge/pandas-%3C%202.2.0-darkblue?style=flat&logo=pandas&logoColor=white)


# Surgical Procedural Knowledge Classifier

### **🎓 Project Context**

This project represents my **first experience with machine learning and text classification**. It was developed as part of the **Advanced Digital Humanities Workshop** (Academic Year 2024/2025) during my Bachelor's degree.

The goal was to transition from theoretical concepts to a practical application: building a **Procedural Knowledge Classifier** to distinguish between descriptive text and operational actions within surgical reports.


## 1. Project Overview

The objective is to identify "procedural actions" in surgical texts. This distinction is vital for organizing clinical knowledge and making it more accessible for medical research and training.

The workflow follows four main phases:
1. **Preprocessing:** Structuring training data for binary classification.
2. **Training:** Implementing a supervised model using the **fastText** library.
3. **Performance Evaluation:** Assessing accuracy, precision, and recall.
4. **Comparative Analysis:** Exploring how dataset size and distribution affect model stability.


## 2. Environment & Compatibility

To ensure the code remains functional exactly as designed, this notebook **simulates a 2024 development environment**.

> **⚠️ Note on Installations:**
> 
> The initial `!pip` cell installs specific legacy versions of NumPy and Pandas. This is a deliberate choice for **reproducibility**. While this triggers dependency warnings in modern environments, it is necessary to maintain the integrity of the indexing logic used for prediction scores, which would otherwise fail under current library updates.


## 3. Dataset & Privacy

This project utilizes the **IJCARS dataset** (Bombieri et al., 2021), focused on robotic-assisted surgical texts.

> **🔒 Data Privacy Notice:**
>
> The surgical dataset used is restricted and available only upon request to the original authors. To maintain clinical confidentiality, the raw data and trained model weights are not hosted in this repository. The notebook serves as a **methodological showcase**, displaying only table headers and representative samples (`df.head()`) to illustrate the pipeline.


## 4. Methodology & Key Findings

- **Data Curation:** To prevent **numerical instability** (NaN errors), the dataset was reduced to target columns and sanitized using regular expressions to strip newlines and tabs.
- **Class Imbalance:** We utilized **stratified sampling** (80/20 split) to preserve the proportion of labels in both training and test sets.
- **The "NaN" Breakthrough:** During testing with a smaller dataset of maintenance manuals, the model initially failed to converge (`RuntimeError: Encountered NaN`).
- **Stochastic Nature:** We discovered that on smaller datasets, success often depends on the **stochastic nature of weight initialization**. The error was resolved not by changing the code, but by re-executing the training until the model successfully converged.


## 5. Performance Results

*Note that, due to the stochastic nature of the training process and the random shuffling of data during the split, these metrics represent a snapshot of a single successful execution.*

| Label | Precision | Recall | F1-Score |
| --- | --- | --- | --- |
| **Non-Procedural** | 0.79 | 0.54 | 0.64 |
| **Procedural** | 0.77 | 0.91 | 0.84 |
