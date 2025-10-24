# ⚽🩺 PySpark Data Management

Un projet complet d’analyse de données et de machine learning utilisant **Apache Spark** et **PySpark**, comprenant :

- L’analyse de données de matchs de football  
- La prédiction de maladies cardiovasculaires  

---

## 📋 Table des matières

1. [À propos du projet](#-à-propos-du-projet)
2. [Structure du projet](#-structure-du-projet)
3. [Technologies utilisées](#-technologies-utilisées)
4. [Installation](#-installation)
5. [Utilisation](#-utilisation)
6. [Cas d’usage](#-cas-dusage)
7. [Résultats](#-résultats)
8. [Contributeurs](#-contributeurs)
9. [Notes techniques](#-notes-techniques)
10. [Améliorations futures](#-améliorations-futures)
11. [Licence](#-licence)

---

## 🎯 À propos du projet

Ce projet démontre l’utilisation de PySpark pour deux cas d’usage distincts :

1️⃣ **Analyse de données de football**
- Bundesliga (2000-2015)
- Ranking des meilleures équipes par saison

2️⃣ **Prédiction de maladies cardiovasculaires**
- Modèle de machine learning
- Classification binaire des risques cardiaques

---

## 📁 Structure du projet
PySpark-Data-Management/
│
├── PySparkDataAnalysis.ipynb       # Analyse des données de football
├── PySparkMachineLearning.ipynb    # Prédiction maladies cardiovasculaires
├── data/
│   ├── football_matches.csv        # Données des matchs de football
│   └── heart_disease.csv           # Données médicales
└── README.md

---

## 🛠️ Technologies utilisées

- **Apache Spark 3.4.1**
- **PySpark**
- **Python 3.10**
- Pandas
- Spark MLlib

📌 Modules ML utilisés :
- Logistic Regression
- Pipelines
- StringIndexer, VectorAssembler
- MulticlassClassificationEvaluator

---

## 📦 Installation

### ✅ Prérequis

- Python 3.10+
- pip installé
- Google Colab (✅ recommandé) ou Jupyter Notebook

### 💻 Installation des dépendances

```bash
pip install pyspark

### Analyse de données de football
from pyspark.sql import SparkSession, Window
from pyspark.sql.functions import *

spark = SparkSession.builder.appName("DataAnalysis").getOrCreate()
df_matches = spark.read.format('csv').options(header='True').load('data/football_matches.csv')

#### Fonctionnalités :
	•	Nettoyage et transformation
	•	Statistiques par équipe (victoires, défaites, nuls)
	•	Buts marqués & encaissés
	•	Classement avec Window Functions
	•	Identification des champions par saison

#### Prédiction de maladies cardiovasculaires

from pyspark.ml.classification import LogisticRegression
from pyspark.ml import Pipeline
from pyspark.ml.feature import StringIndexer, VectorAssembler

spark = SparkSession.builder.appName("MachineLearning").getOrCreate()
data = spark.read.format('csv').options(header='True', inferSchema=True).load('data/heart_disease.csv')
### Fonctionnalités
	•	Nettoyage des données
	•	Encodage des variables catégorielles
	•	Pipeline ML complet
	•	Régression logistique
	•	Matrice de confusion & précision
 Analyse Football
### Cas d'usage
Dataset : 24 625 matchs (Bundesliga, Premier League…)

📌 Résultats clés :
	•	Classement par saison (rank)
	•	Pourcentage de victoires
	•	Différentiel de buts (GoalDifference)

### Prédiction des maladies cardiovasculaires

Dataset : 297 patients — 14 features médicales

📌 Performance du modèle :
	•	✅ Précision : 83.91%
	•	Train/Test : 70% / 30%
	•	Algo : Logistic Regression

                Prédiction
              Sain | Malade
Réalité
Sain          36   |   7
Malade        7    |   37

📈 Résultats

✅ Analyse Football :
	•	Identification claire des équipes dominantes
	•	Window Functions performantes

✅ Machine Learning :
	•	Bonne capacité de généralisation
	•	Pipeline réutilisable facilement

⸻

### Auteur

Cherif Amanatoulha SY
Data Engineer

📝 Notes techniques

📌 Optimisations PySpark :
	•	Window.partitionBy() pour Group Ranking
	•	Caching des DataFrames
	•	Pipelines ML modulaires

📌 Bonnes pratiques :
	•	cast() pour les types
	•	Encodage catégoriel avec StringIndexer
	•	train_test_split reproductible (seed)

📄 Licence

📌 Projet destiné à mon Portfolio.

