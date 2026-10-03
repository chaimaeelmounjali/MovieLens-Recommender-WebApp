# 🎬 MovieLens 100K Recommender System & Analytics WebApp

[![Python](https://img.shields.io/badge/Python-3.9+-3776AB.svg?logo=python)](https://www.python.org/)
[![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-Recommenders-F7931E.svg?logo=scikit-learn)](https://scikit-learn.org/)
[![Surprise](https://img.shields.io/badge/Surprise-SVD%20%2F%20KNN-blue.svg)](http://surpriselib.com/)
[![Streamlit](https://img.shields.io/badge/Streamlit-Interactive%20App-FF4B4B.svg?logo=streamlit)](https://streamlit.io/)
[![Dataset](https://img.shields.io/badge/Dataset-MovieLens%20100k-yellow.svg)](https://grouplens.org/datasets/movielens/100k/)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

*Bilingual README: [Français](#-version-française) | [English](#-english-version)*

---

## 🇫🇷 Version Française

### 🎯 Objectif
Le projet **MovieLens Recommender WebApp** est une plateforme analytique et interactive de système de recommandation cinématographique exploitant le jeu de données de référence **MovieLens 100k** (GroupLens Research). L'objectif est de comparer expérimentalement plusieurs familles d'algorithmes de filtrage (collaboratif, basé sur le contenu, et factorisation matricielle) et de mettre à disposition une application web permettant aux utilisateurs d'obtenir des recommandations personnalisées en temps réel selon leurs préférences.

### 🛠️ Stack Technologique
- **Langage & Environnement** : Python 3.9+, Jupyter Notebook.
- **Traitement & Analyse de Données** : Pandas, NumPy, Scipy.
- **Algorithmes de Recommandation & ML** :
  - *Surprise library* (`SVD`, `NMF`, `KNNBasic`, `KNNWithMeans`).
  - *Scikit-Learn* (Similarité Cosinus, TF-IDF pour les genres, décomposition matricielle).
- **Interface Web Interactive** : Streamlit / FastAPI pour la restitution dynamique des recommandations et des métadonnées (affiches, notes moyennes, genres).
- **Visualisation & Diagnostic** : Matplotlib, Seaborn, Plotly (analyse de la sparsité de la matrice utilisateurs/films, distribution des notes).

### 👩‍💻 Mon Rôle & Contributions
- **Ingestion & Exploration des Données (MovieLens 100k)** :
  - Parsing et structuration des fichiers `u.data`, `u.item`, `u.user` (100 000 notes attribuées par 943 utilisateurs sur 1 682 films).
  - Analyse exploratoire de la distribution des notes (biais de popularité, dispersion et taux de sparsité > 93%).
- **Implémentation des Moteurs de Recommandation** :
  - **Filtrage Collaboratif Utilisateur-Utilisateur & Item-Item** : calcul des matrices de similarité cosinus avec normalisation des biais de notation.
  - **Factorisation Matricielle (SVD / Funk SVD)** : réduction de dimensionnalité pour extraire les facteurs latents d'affinité.
  - **Filtrage Basé sur le Contenu** : vectorisation des genres et métadonnées textuelles par TF-IDF.
  - Stratégies de gestion du *Cold Start* (nouveaux utilisateurs sans historique) basées sur la popularité pondérée par score bayésien.
- **Évaluation & Benchmarking Hors-Ligne** :
  - Mise en place d'une validation croisée 5-Fold.
  - Mesure comparative des performances : RMSE, MAE, et métriques de ranking (Precision@K, Recall@K).
- **Conception de l'Application Web** :
  - Développement d'une interface utilisateur fluide avec sélection interactive de films favoris et génération instantanée du Top-N personnalisé.

### 📊 Résultats & Métriques Clés
- **Performance prédictive optimale** : Réduction de la RMSE sous la barre des 0.93 grâce à l'algorithme SVD régularisé.
- **Recommandations diversifiées** : Équilibre maîtrisé entre pertinence prédictive et sérendipité (découverte de nouveaux films pertinents hors blockbusters).
- **Latence d'inférence < 50 ms** : Précalcul et indexation des matrices de similarité pour un temps de réponse instantané dans l'interface web.

---

## 🇬🇧 English Version

### 🎯 Objective
The **MovieLens Recommender WebApp** is an interactive machine-learning-driven analytics toolkit and movie recommendation engine built on the benchmark **MovieLens 100k** dataset (GroupLens Research). It provides a rigorous comparative benchmark of fundamental recommender paradigms (Collaborative Filtering, Content-Based Filtering, and Matrix Factorization) paired with a responsive web interface delivering real-time, personalized movie suggestions.

### 🛠️ Tech Stack
- **Language & Runtime**: Python 3.9+, Jupyter Notebooks.
- **Data Engineering**: Pandas, NumPy, Scipy (sparse matrices).
- **Machine Learning & Recommenders**:
  - *Surprise library* (SVD, NMF, KNNWithMeans, Item-Item & User-User Collaborative Filtering).
  - *Scikit-Learn* (Cosine similarity, TF-IDF vectorization, PCA).
- **Web Interface**: Streamlit / FastAPI for interactive scoring and Top-N delivery.
- **Visualization**: Matplotlib, Seaborn, Plotly (matrix sparsity analysis, rating distributions).

### 👩‍💻 My Role & Key Contributions
- **Data Pipeline & Exploratory Analysis**:
  - Processed and merged 100,000 ratings across 943 users and 1,682 titles (`u.data`, `u.item`, `u.user`).
  - Diagnosed data distribution challenges: long-tail popularity curve and a matrix sparsity factor exceeding 93%.
- **Recommendation Engine Architecture**:
  - Implemented memory-based User-User and Item-Item Collaborative Filtering models.
  - Built latent factor models using Singular Value Decomposition (SVD) with stochastic gradient descent (SGD).
  - Engineered a Content-Based recommendation module leveraging movie genre TF-IDF embeddings.
  - Implemented Cold-Start fallback mechanisms using Bayesian-weighted average ratings.
- **Experimental Validation & Benchmarks**:
  - Designed a 5-Fold cross-validation benchmark protocol.
  - Computed offline evaluation metrics: RMSE, MAE, alongside ranking-specific Precision@K and Recall@K.
- **Interactive Web Application**:
  - Crafted an intuitive UI enabling users to rate seed movies and instantly receive dynamically calculated Top-N recommendations.

### 📊 Key Results & Impact
- **Superior Predictive Accuracy**: Achieved test-set RMSE < 0.93 utilizing regularized SVD matrix factorization.
- **Balanced Exploration & Exploitation**: Mitigated popularity bias to provide novel yet relevant cinematic suggestions.
- **Sub-50ms Recommendation Latency**: Leveraged vectorized sparse representations for real-time recommendation querying.

---

### 🚀 Quick Start / Démarrage Rapide

```bash
# Clone the repository
git clone git@github.com:chaimaeelmounjali/MovieLens-Recommender-WebApp.git
cd MovieLens-Recommender-WebApp

# Set up virtual environment
python -m venv .venv
# Windows:
.venv\Scripts\activate
# Linux/macOS:
# source .venv/bin/activate

# Install requirements
pip install numpy pandas scikit-learn scikit-surprise streamlit matplotlib

# Launch the Streamlit application
streamlit run app.py
```
