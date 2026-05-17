# Spotify-Track-Popularity-Analysis
Spotify Track Popularity Analysis: Genre-Driven Audio Insights
This repository contains a data mining project focused on analysing and predicting the popularity of Spotify tracks. By leveraging audio features and genre metadata, the project uncovers what makes a song popular and groups tracks by their sonic characteristics.

This was a group project completed for the module CS4168: Data Mining at the University of Limerick.

Project Overview
Music streaming platforms host millions of tracks, yet popularity is concentrated among a small subset. Understanding which audio features drive listener engagement — across different genres — is valuable for artists, producers, and playlist curators alike. This project applies the full data mining pipeline (exploratory analysis → regression → classification → clustering) to a curated Spotify dataset of 2,000 tracks spanning five genres.

Key Features
Data Cleaning: Identified and corrected a physically impossible loudness outlier (a value of ~800,000 dB, which is not possible — loudness is always negative), removed exact duplicate rows, and handled missing values using median imputation.
Feature Engineering: Constructed a binary popularity target (popularity_binary) by splitting tracks at the median popularity score; label-encoded the track_genre column for use in supervised models.
Exploratory Data Analysis (EDA): Visualised distributions of all 17 features, examined missing value patterns, analysed genre frequency, and explored correlations between audio features and popularity.
Predictive Modelling (Regression): Predicted exact popularity scores (0–100) and compared Linear Regression, Ridge Regression, Decision Tree, Random Forest, and Gradient Boosting regressors using MAE, RMSE, and R².
Predictive Modelling (Classification): Predicted whether a track is popular or not using Logistic Regression, Decision Tree, Random Forest, KNN, SVM, and Gradient Boosting classifiers with 5-fold cross-validation, hyperparameter tuning, and evaluation via accuracy, F1, and ROC-AUC.
Clustering (Descriptive Analytics): Grouped tracks by their nine core audio features (without genre labels) using K-Means and DBSCAN, evaluated cluster quality with silhouette score and Davies–Bouldin index, and used PCA for 2D visualisation.
Dataset
The dataset (tracks2026.xls) contains 2,000 Spotify tracks across five genres: hip-hop, indie-pop, pop, r-n-b, and synth-pop.

Feature	Description
track_id	Unique Spotify track identifier
popularity	Spotify popularity score (0–100)
duration_ms	Track duration in milliseconds
explicit	Whether the track contains explicit content
danceability	How suitable a track is for dancing (0–1)
energy	Perceptual intensity and activity (0–1)
key	Musical key (integer code 0–11)
loudness	Overall loudness in dB (typically −60 to 0)
mode	Major (1) or minor (0)
speechiness	Presence of spoken words (0–1)
acousticness	Confidence the track is acoustic (0–1)
instrumentalness	Likelihood of no vocals (0–1)
liveness	Probability of a live audience (0–1)
valence	Musical positiveness (0–1)
tempo	Estimated tempo in BPM
time_signature	Estimated beats per bar
track_genre	Genre label
Tech Stack
Language: Python
Environment: Jupyter Notebook / Google Colab
Libraries:
Pandas & NumPy — Data manipulation
Matplotlib & Seaborn — Visualisation
Scikit-Learn — Data mining algorithms (pipelines, cross-validation, all models)
📂 Repository Structure
├── eda.ipynb               # Exploratory Data Analysis: distributions, outliers, missing values, genre counts
├── regression.ipynb        # Regression: predicting exact popularity score (0–100)
├── classification.ipynb    # Classification: predicting popular vs. not popular (binary)
├── clustering.ipynb        # Clustering: unsupervised grouping by audio features (K-Means & DBSCAN)
└── tracks2026.xls          # Dataset: 2,000 Spotify tracks across 5 genres, 17 features
Workflow
tracks2026.xls
      │
      ▼
 eda.ipynb                  ← Start here: understand the data
      │
      ├──▶ regression.ipynb        ← Predict popularity as a continuous score
      ├──▶ classification.ipynb    ← Predict popular vs. not popular (binary)
      └──▶ clustering.ipynb        ← Group tracks by audio similarity (unsupervised)
Each notebook is self-contained — it loads and cleans the data independently, so notebooks can be run in any order after the EDA.

Models & Evaluation
Regression
Model	Metric
Linear Regression	MAE, RMSE, R²
Ridge Regression	MAE, RMSE, R²
Decision Tree Regressor	MAE, RMSE, R²
Random Forest Regressor (tuned)	MAE, RMSE, R²
Gradient Boosting Regressor (tuned)	MAE, RMSE, R²
Classification
Model	Metric
Logistic Regression	Accuracy, F1, ROC-AUC
Decision Tree	Accuracy, F1, ROC-AUC
Random Forest (tuned)	Accuracy, F1, ROC-AUC
K-Nearest Neighbours	Accuracy, F1, ROC-AUC
SVM	Accuracy, F1, ROC-AUC
Gradient Boosting (tuned)	Accuracy, F1, ROC-AUC
Selection process: 5-fold cross-validation on all candidates → top performers tuned with GridSearchCV / RandomizedSearchCV → final evaluation on held-out test set.

Clustering
Algorithm	Evaluation
K-Means	Elbow method, Silhouette score, Davies–Bouldin index
DBSCAN	k-distance plot (for ε selection), Silhouette score, Davies–Bouldin index
Clustering uses only the 9 core audio features: danceability, energy, loudness, speechiness, acousticness, instrumentalness, liveness, valence, tempo. Genre labels are excluded during training and used only post-hoc to evaluate alignment.

Getting Started
Clone the repository and open the notebooks in Jupyter or Google Colab.
Ensure tracks2026.xls is in the same directory as the notebooks (or update the file path in each notebook).
Install dependencies:
pip install pandas numpy matplotlib seaborn scikit-learn
Run notebooks in the recommended order: eda.ipynb → then any of the three modelling notebooks.
