# Drug-Target Interaction Prediction: Deep Machine Learning Analysis

## Overview
This repository contains a comprehensive analysis of Drug-Target Interaction (DTI) prediction using various machine learning and deep learning models. The goal is to predict the binding affinity (KIBA scores) between drugs (small molecules) and protein targets based on their chemical structures (SMILES) and amino acid sequences.

The notebook walks through the entire machine learning pipeline, from data loading and exploratory data analysis (EDA) to feature engineering, model training, evaluation, and comparison of multiple models.

## Dataset
**Davis-KIBA Dataset**: The analysis utilizes the Davis-KIBA dataset, a classic and concise DTI dataset containing experimentally determined binding affinities (KIBA scores) for various drug-target pairs. Each entry includes:
- **Drug ID**: Unique identifier for the drug.
- **Protein ID**: Unique identifier for the protein target.
- **SMILES**: Simplified Molecular-Input Line-Entry System representation of the drug's chemical structure.
- **Sequence**: Amino acid sequence of the protein target.
- **Score**: Experimental binding affinity (KIBA score).

**Source**: [Davis-KIBA Kaggle Dataset](https://www.kaggle.com/datasets/christang0002/davis-and-kiba/data?select=kiba.txt)

## Models Explored
The following machine learning and deep learning models were implemented and evaluated for DTI prediction:
1.  **Artificial Neural Network (ANN)**: A basic feed-forward neural network to establish a baseline.
2.  **Convolutional Neural Network (CNN)**: A specialized neural network architecture capable of learning hierarchical features from both drug (Morgan fingerprints) and protein (embedded sequences) representations.
3.  **Linear Regression**: A simple statistical model for regression, serving as another baseline.
4.  **Random Forest Regressor**: An ensemble learning method based on decision trees.
5.  **XGBoost Regressor**: An optimized distributed gradient boosting library designed for speed and performance.
6.  **Graph Convolutional Network (GCN) + CNN Hybrid**: A more advanced deep learning model that leverages graph neural networks to process drug molecular graphs and a CNN to process protein sequences, merging their outputs for prediction.

## Feature Engineering
-   **Drug Representation**: Morgan fingerprints (binary vectors) are generated from SMILES strings to capture structural information of the drugs. For the GCN model, drugs are represented as molecular graphs (node features and adjacency matrices).
-   **Protein Representation**: Amino acid sequences are integer-encoded, converting each amino acid into a numerical index. These sequences are then padded to a uniform length.

## Key Findings & Model Comparison
The notebook includes a detailed comparison of all trained models based on metrics such as Mean Squared Error (MSE), Mean Absolute Error (MAE), Root Mean Squared Error (RMSE), R-squared (R2), Pearson correlation, and Spearman correlation. Visualizations are provided to illustrate the performance differences.

Preliminary results indicate that **XGBoost** and the **CNN** models achieved the best performance among the evaluated models, demonstrating superior predictive power for drug-target binding affinities.

## How to Run the Notebook
1.  **Clone the repository**:
    ```bash
    git clone <repository_url>
    cd <repository_name>
    ```
2.  **Download the dataset**: Obtain `kiba.txt` from the [Kaggle dataset link](https://www.kaggle.com/datasets/christang0002/davis-and-kiba/data?select=kiba.txt) and place it in the specified path within your Colab environment or update the `kiba_path` variable in the notebook.
3.  **Open in Google Colab**: Upload the `.ipynb` notebook to Google Colab.
4.  **Install dependencies**: Run the `!pip install` commands at the beginning of the notebook to install necessary libraries like `rdkit` and `xgboost`.
5.  **Run all cells**: Execute all cells in the notebook sequentially.

