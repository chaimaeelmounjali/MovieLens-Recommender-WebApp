# 🎬 MovieLens 100k Recommender System — Streamlit Multi-Page Web App

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB.svg?logo=python)](https://www.python.org/)
[![Streamlit](https://img.shields.io/badge/Streamlit-Multi--Page%20App-FF4B4B.svg?logo=streamlit)](https://streamlit.io/)
[![PyTorch](https://img.shields.io/badge/PyTorch-NCF%20%26%20AutoRec-EE4C2C.svg?logo=pytorch)](https://pytorch.org/)
[![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-KNN%20%2F%20SVD%20%2F%20NMF-F7931E.svg?logo=scikit-learn)](https://scikit-learn.org/)
[![Plotly](https://img.shields.io/badge/Plotly-3D%20Visualizations-3F4F75.svg?logo=plotly)](https://plotly.com/)
[![Dataset](https://img.shields.io/badge/Dataset-MovieLens%20100k-yellow.svg)](https://grouplens.org/datasets/movielens/100k/)
[![NCF RMSE](https://img.shields.io/badge/Best%20RMSE-0.9339%20(NCF)-success.svg)](#)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

*Bilingual README: [Français](#-version-française) | [English](#-english-version)*

---

## 🇫🇷 Version Française

### 🎯 Objectif
**MovieLens Recommender** est une application web interactive multi-pages développée avec **Streamlit** pour explorer, comparer et déployer plusieurs familles d'algorithmes de recommandation de films sur le dataset de référence **MovieLens 100k**. Le projet vise à moderniser l'approche classique du filtrage collaboratif en intégrant des modèles de Deep Learning (**NCF** et **AutoRec**) tout en offrant une interface utilisateur riche pour l'exploration, l'explicabilité et la personnalisation des recommandations.

### 🛠️ Stack Technologique
- **Langage & Environnement** : Python 3.10+.
- **Interface Web** : Streamlit (application multi-pages : Exploration, Recommandations, Films Similaires, Comparaison des Modèles, Profil Utilisateur, Analyse Algorithmique).
- **Machine Learning Classique** : Scikit-Learn, SciPy (`TruncatedSVD`, `NMF`, `KNN Item-Based` avec similarité Cosinus).
- **Deep Learning** : PyTorch :
  - **NCF** (*Neural Collaborative Filtering*, He et al. WWW 2017) : architecture NeuMF combinant GMF + MLP.
  - **AutoRec** (*Autoencoder Recommender*, Sedhain et al. WWW 2015) : autoencodeur Item-Based avec *Masked MSE Loss*.
- **Visualisation Interactive** : Plotly Express (graphiques 2D/3D, PCA de l'espace latent, réseaux de similarité).
- **Données & Analyse** : Pandas, NumPy, Scikit-Surprise, LightFM, Matplotlib, Seaborn.
- **Notebooks & Prototypage** : Jupyter Notebook (`notebooks/recommender_system.ipynb`, `recommender_analysis.py`).

### 👩‍💻 Mon Rôle & Contributions
- **Architecture & Pipeline d'Entraînement (`benchmark.py`)** :
  - Conception du pipeline de benchmark automatisé gérant le chargement du dataset MovieLens 100k (100 000 notes, 943 utilisateurs, 1 682 films), le split Train/Test 80/20, l'entraînement de tous les modèles et le calcul standardisé des métriques RMSE, MAE, Precision@10 et Recall@10.
  - Sauvegarde automatique des artefacts du meilleur modèle (`.pkl`, `.pth`).
- **Modèles Deep Learning PyTorch** :
  - Implémentation complète du **NCF** (`models/ncf.py`) avec les deux branches GMF et MLP, entraîné avec l'optimiseur Adam et la MSE Loss.
  - Implémentation de l'**AutoRec** (`models/autorec.py`) avec la stratégie de *Masked MSE* ignorant les notes manquantes lors de la rétropropagation.
- **Application Streamlit Multi-Pages** :
  - Architecture multi-pages modulaire (`pages/`) avec injection de styles CSS personnalisés (`utils/ui.py`).
  - Page d'exploration : statistiques, distribution des notes, nuage de mots, popularité par genre.
  - Page de recommandations : choix dynamique de l'algorithme, simulation par User ID, affichage des affiches via l'API **OMDb**.
  - Page d'analyse algorithmique : carte des films en PCA 2D/3D (SVD), interprétation des facteurs latents (NMF), graphe de similarité inter-films.
- **Recommandation Temps Réel (`utils/recommender.py`)** :
  - Module d'inférence chargé une fois en mémoire, supportant tous les modèles entraînés.

### 📊 Résultats & Métriques du Benchmark

Évaluation sur 20% du dataset MovieLens 100k (test set) :

| Modèle | RMSE ↓ | MAE ↓ | Precision@10 | Recall@10 |
|:---|:---|:---|:---|:---|
| 🥇 **NCF (Neural CF)** | **0.9339** | **0.7353** | — | — |
| 🥈 **AutoRec** | **0.9658** | **0.7663** | — | — |
| 🥉 **KNN (Item-Based)** | **0.9692** | **0.7583** | **0.214** | **0.229** |
| Baseline (Moyenne) | 1.1239 | 0.9420 | 0.000 | 0.000 |
| SVD (Sklearn) | 2.6404 | 2.3711 | 0.257 | 0.270 |
| NMF (Sklearn) | 2.6246 | 2.3564 | 0.247 | 0.256 |

**Conclusion** : NCF atteint le **meilleur RMSE de 0.9339**, confirmant la supériorité des architectures neuronales pour capturer les interactions utilisateur-item non linéaires. AutoRec et KNN restent très compétitifs.

---

## 🇬🇧 English Version

### 🎯 Objective
**MovieLens Recommender** is a production-grade interactive multi-page Streamlit web application built to explore, train, benchmark, and deploy diverse recommendation algorithms on the canonical **MovieLens 100k** dataset. It bridges classical collaborative filtering techniques (SVD, NMF, KNN) with state-of-the-art Deep Learning models (**NCF** and **AutoRec**) and presents results through rich interactive data visualizations and a premium user-facing interface for personalized movie suggestions.

### 🛠️ Tech Stack
- **Language & Runtime**: Python 3.10+.
- **Web Interface**: Streamlit (multi-page: Exploration, Recommendations, Similar Films, Model Comparison, User Profile, Algorithmic Analysis).
- **Classical ML**: Scikit-Learn, SciPy (`TruncatedSVD`, `NMF`, `KNN Item-Based` with Cosine Similarity).
- **Deep Learning**: PyTorch:
  - **NCF** (Neural Collaborative Filtering — He et al. WWW 2017): NeuMF architecture merging GMF and MLP pathways.
  - **AutoRec** (Autoencoder Recommender — Sedhain et al. WWW 2015): Item-based autoencoder with Masked MSE loss.
- **Interactive Visualizations**: Plotly Express (2D/3D scatter, PCA embeddings, similarity networks).
- **Data & Analysis**: Pandas, NumPy, Scikit-Surprise, LightFM, Matplotlib, Seaborn.

### 👩‍💻 My Role & Key Contributions
- **Benchmarking Pipeline Architecture (`benchmark.py`)**:
  - Built an automated end-to-end training and evaluation harness covering data loading (100k ratings), 80/20 train/test splitting, model fitting, RMSE/MAE/P@10/R@10 computation, and artifact persistence.
- **Deep Learning Recommender Implementations**:
  - Engineered the **NCF** model (`models/ncf.py`) combining Generalized Matrix Factorization (GMF) and Multi-Layer Perceptron (MLP) branches.
  - Implemented **AutoRec** (`models/autorec.py`) with a Masked MSE training objective that exclusively backpropagates observed ratings.
- **Multi-Page Streamlit Application**:
  - Designed modular page architecture (`pages/`) with reusable components and custom CSS injection.
  - Integrated real-time poster fetching from the **OMDb API** on the Recommendations page.
  - Built interactive latent space visualizations (PCA 2D/3D) and inter-film similarity graph on the Analytics page.
- **Inference Engine (`utils/recommender.py`)**:
  - Crafted a unified model-serving module loading pre-trained artifacts once at startup for low-latency real-time predictions.

### 📊 Benchmark Results

Evaluated on the MovieLens 100k test set (20% holdout):

| Model | RMSE ↓ | MAE ↓ | Precision@10 | Recall@10 |
|:---|:---|:---|:---|:---|
| 🥇 **NCF (Neural CF)** | **0.9339** | **0.7353** | — | — |
| 🥈 **AutoRec** | **0.9658** | **0.7663** | — | — |
| 🥉 **KNN (Item-Based)** | **0.9692** | **0.7583** | **0.214** | **0.229** |
| Baseline (Global Mean) | 1.1239 | 0.9420 | 0.000 | 0.000 |
| SVD (Sklearn) | 2.6404 | 2.3711 | 0.257 | 0.270 |
| NMF (Sklearn) | 2.6246 | 2.3564 | 0.247 | 0.256 |

**Key Takeaway**: NCF achieves the **best RMSE of 0.9339** — a 16.9% improvement over the baseline — validating that neural architectures capture non-linear user-item interaction dynamics significantly better than classical approaches.

---

### 📂 Project Structure / Structure du Projet
```text
MovieLens-Recommender-WebApp/
├── app.py                          # Streamlit entry point
├── benchmark.py                    # Full training & evaluation pipeline
├── requirements.txt                # Python dependencies
├── run.bat                         # Windows quick-start script
├── models/
│   ├── ncf.py                      # Neural Collaborative Filtering (PyTorch)
│   ├── autorec.py                  # AutoRec Autoencoder (PyTorch)
│   ├── ncf_model.pth               # Trained NCF weights
│   ├── autorec_model.pth           # Trained AutoRec weights
│   ├── metrics.json                # Classical models benchmark results
│   └── model_metrics.json          # Full benchmark metrics
├── pages/
│   ├── 1_Exploration.py            # Dataset statistics & visualizations
│   ├── 2_Recommandations.py        # Personalized recommendations + OMDb posters
│   ├── 3_Films_Similaires.py       # Item-based similarity finder
│   ├── 4_Comparaison_Modeles.py    # Model performance comparison
│   ├── 5_Profil_Utilisateur.py     # User taste profile analysis
│   └── 6_Analyse_Algorithmique.py  # PCA embeddings & similarity graph
├── utils/
│   ├── recommender.py              # Inference engine & data loader
│   ├── ui.py                       # Custom CSS & reusable UI components
│   ├── data_loader.py              # Data pipeline utilities
│   └── visualizations.py          # Plotly chart builders
├── notebooks/
│   ├── recommender_system.ipynb    # Exploratory notebook
│   └── recommender_analysis.py    # Analysis scripts
└── assets/                         # Static assets (images, posters)
```

### 🚀 Quick Start / Démarrage Rapide

```bash
# 1. Clone the repository
git clone git@github.com:chaimaeelmounjali/MovieLens-Recommender-WebApp.git
cd MovieLens-Recommender-WebApp

# 2. Install dependencies
pip install -r requirements.txt

# 3. Train all models (generates artifacts in models/)
python benchmark.py

# 4. Launch the Streamlit web app
streamlit run app.py
# Opens at http://localhost:8501
```

> **Windows shortcut**: Double-click `run.bat` to launch directly.