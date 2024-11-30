
# Pneumothorax Detection with MIMIC-CXR Dataset

This repository showcases the evaluation and analysis of a pre-trained machine learning model for detecting pneumothorax (collapsed lung) using the [MIMIC-CXR](https://physionet.org/content/mimic-cxr/2.0.0/) dataset. The notebook explores the model's performance, identifies potential biases, and tests approaches to improve its fairness and robustness.

---

## **Project Overview**

Pneumothorax detection is a crucial task in medical imaging, and automated tools can significantly enhance diagnosis. This project aims to:
- Evaluate the performance of a pre-trained model on the MIMIC-CXR dataset.
- Investigate biases, such as reliance on specific terms in radiology reports.
- Propose methods to mitigate biases and improve fairness.

The notebook includes:
1. Data loading and preparation.
2. Model evaluation with performance metrics.
3. Error analysis and visualization.
4. Bias detection and mitigation experiments.

---

## **Dataset**

The analysis uses the **MIMIC-CXR** dataset, which contains:
- Chest X-ray images.
- Radiology reports with diagnostic labels.
- Demographic metadata for subgroup analysis.

---

## **Features**

### **1. Data Preparation**
- Downloads and processes the following files:
  - Patient demographic data (`patients.csv`).
  - Radiology metadata (`mimic-cxr-2.0.0-metadata.csv`).
  - Evaluation set (`evaluation_set.csv`).
- Loads and visualizes X-ray images for exploratory analysis.

### **2. Model Evaluation**
- Loads a pre-trained PyTorch model for pneumothorax detection.
- Generates predictions and computes:
  - **AUROC (Area Under the Receiver Operating Characteristic Curve):** Measures classification performance.
  - **Precision and Recall:** Evaluates prediction accuracy and ability to identify true positives.
  - **Confusion Matrix:** Summarizes prediction outcomes.

### **3. Error Analysis**
- Reviews incorrect predictions using:
  - Sample X-ray images and associated radiology reports.
  - Keywords in reports, like "pigtail catheter," that may bias predictions.
- Visualizes model performance for deeper insights into failure cases.

### **4. Bias Mitigation**
- Tests the impact of excluding specific terms (e.g., "catheter") from radiology reports.
- Recomputes performance metrics to assess whether the model overly relies on textual artifacts.

---

## **Usage**

### **Prerequisites**
- Python 3.x
- Required libraries: `numpy`, `pandas`, `matplotlib`, `torch`, `sklearn`, `PIL`, `imageio`
- Google Cloud SDK (`gcloud`) for data retrieval.

### **Steps to Run**
1. Clone the repository:
   ```bash
   git clone <repository_url>
   cd <repository_name>
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Open the Jupyter Notebook:
   ```bash
   jupyter notebook MIMIC_CXR.ipynb
   ```
4. Follow the cells step-by-step to replicate the analysis and visualize results.

---

## **Results**

### **Key Findings**
1. **Model Performance:**
   - High AUROC on the test set indicates good overall classification ability.
   - Precision and recall values demonstrate effectiveness but room for improvement.

2. **Bias Detection:**
   - The model tends to rely on certain keywords in radiology reports (e.g., "pigtail catheter").
   - Demographic analysis reveals variations in performance across subgroups (e.g., gender).

3. **Bias Mitigation:**
   - Removing keywords reduces reliance on spurious correlations, leading to more robust predictions.

### **Visualization Examples**
- X-ray images with associated predictions and reports.
- Performance metrics across demographic groups.

---

## **Future Work**
- Train models with balanced datasets to improve fairness.
- Use advanced natural language processing to preprocess radiology reports.
- Validate findings in a real-world clinical setting.

---

## **Contributing**
Contributions are welcome! Fork this repository, make changes, and submit a pull request.

---

## **License**
This repository is licensed under the MIT License.

---

## **Acknowledgments**
- Dataset: [MIMIC-CXR](https://physionet.org/content/mimic-cxr/2.0.0/) by PhysioNet.
- Pre-trained model and notebook adapted from MIT's **6.871 course materials**.
- Special thanks to collaborators and reviewers for their insights and feedback.
