# 🧬 Predicting Neuroblastoma Clinical Outcomes using RNA-seq Data

This project aims to predict key clinical outcomes of neuroblastoma patients using gene expression data (RNA-seq). The goal of this project is to develop a machine learning model that can predict clinical outcomes in neuroblastoma patients using RNA-Seq gene expression data. Several clinical outcome fields contain missing values. This project aims to train models that can accurately predict those outcomes and use them to impute the missing values.

## Project Aims:

- **Explore and understand** the dataset to identify patterns, distributions, and any preprocessing needs.

- **Select clinical endpoints** as target variables for prediction:
  
  - **Death from Disease:**  
    Occurrence of death from the disease  
    (yes = 1, no = 0)
  
  - **High Risk:**  
    Clinically considered as high-risk neuroblastoma  
    (yes = 1, no = 0)
  
  - **INSS Stage:**  
    Disease stage according to the International Neuroblastoma Staging System  
    (1, 2, 3, 4, or 4S)
  
  - **Progression:**  
    Occurrence of a tumor progression event  
    (yes = 1, no = 0)

- **Build classification models** to predict each selected clinical endpoint using RNA-Seq gene expression data.

- **Evaluate model performance** using appropriate metrics such as accuracy, precision, recall, F1-score, and ROC-AUC.

- **Generate predictions** for the missing clinical outcomes in the test set using the trained models.

## 📊 Model Performance Summary:
| Outcome             | Accuracy | Key Insights                                                 |
| ------------------- | -------- | ------------------------------------------------------------ |
| Death from disease  | 82%      | High recall (0.90) for death cases, some false positives.    |
| High risk           | 94%      | Balanced precision and recall; excellent model performance.  |
| INSS stage          | 42%      | Multiclass setting limits logistic regression effectiveness. |
| Disease progression | 74%      | High recall (0.89) for progression, but moderate precision.  |

## 📌Key Inferences:
- Models for binary outcomes (e.g., death, risk, progression) perform fairly well.
- Multiclass classification for INSS staging is less reliable with logistic regression—suggesting future use of Random Forests or other ensemble methods.
- High recall for death and progression outcomes indicates the model is good at identifying critical cases but may produce some false positives.

## 🧠 Future Work
- Test with more complex models (Random Forest, XGBoost, Neural Nets).
- Address class imbalance using techniques like SMOTE or weighted loss.
- Perform feature selection or dimensionality reduction (e.g., PCA).
- Validate on external datasets.