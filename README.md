# 🌍 Anticipation des Besoins en Consommation de Bâtiments  

**Projet de modélisation prédictive des consommations énergétiques et émissions de CO₂ des bâtiments non résidentiels de Seattle.**  
Objectif : contribuer à la stratégie de neutralité carbone 2050 de la ville.

---

## 🎯 Objectif du projet  
Ce projet s’inscrit dans la démarche de **neutralité carbone à l’horizon 2050** portée par la ville de **Seattle**.  
L’enjeu est de **prédire les émissions de CO₂** (`TotalGHGEmissions`) et la **consommation totale d’énergie** (`SiteEnergyUseWN(kBtu)`) des bâtiments non résidentiels, à partir des données structurelles disponibles dans la base **Building Energy Benchmarking 2016**.

---

## 🧩 Contenu du projet  

Le dépôt contient :  
- **Trois notebooks Jupyter** :  
  1. **Analyse exploratoire & Feature Engineering**  
     - Nettoyage du dataset (46 colonnes → 18 pertinentes)  
     - Sélection des bâtiments non résidentiels (`BuildingType`)  
     - Création de nouvelles variables (`Electricity(%)`, `NaturalGas(%)`, `SteamUse(%)`, `Age`)  
     - Détection et traitement des valeurs aberrantes  
  2. **Modélisation de la variable TotalGHGEmissions**  
     - Comparaison de modèles : Linear, Lasso, Ridge, Random Forest, Gradient Boosting, SVM  
     - Meilleur modèle : **Gradient Boosting Regression**  
       - R² = 0.60  
       - MAE = 86.54  
       - RMSE = 216.81  
  3. **Modélisation de la variable SiteEnergyUseWN(kBtu)**  
     - Meilleur modèle : **Gradient Boosting Regression**  
       - R² = 0.71  
       - MAE = 3.86×10⁶  
       - RMSE = 7.22×10⁶  
- **Présentation PowerPoint** : synthèse visuelle des résultats et analyses de la *feature importance* (globale & locale).

---

## 🔍 Méthodologie  

1. **Préparation et nettoyage des données**  
   - Filtrage des bâtiments non résidentiels  
   - Suppression des valeurs non conformes ou par défaut  
   - Vérification métier :  
     `PropertyGFATotal = PropertyGFABuilding(s) + PropertyGFAParking`  

2. **Feature Engineering**  
   - Création de variables dérivées et ratios énergétiques  
   - Transformation pour éviter le *data leakage*  
   - Normalisation des valeurs  

3. **Modélisation**  
   - Comparaison de plusieurs algorithmes :  
     Linear, Lasso, Ridge, Random Forest, Gradient Boosting, Bagging, SVM  
   - Validation croisée (KFold)  
   - Sélection finale du **Gradient Boosting Regression**

4. **Analyse post-modélisation**  
   - *Feature importance* globale et locale  
   - Étude de l’influence du `ENERGYSTARScore` sur les performances :  
     - Impact modéré mais positif sur la précision des prédictions.

---

## 📊 Résultats synthétiques  

| Variable cible | Meilleur modèle | R² | MAE | RMSE |
|----------------|----------------|----|-----|------|
| `TotalGHGEmissions` | Gradient Boosting Regression | 0.60 | 86.54 | 216.81 |
| `SiteEnergyUseWN(kBtu)` | Gradient Boosting Regression | 0.71 | 3.86×10⁶ | 7.22×10⁶ |

---

## 🛠️ Technologies utilisées  

- **Python** : Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn  
- **Modèles** : Linear, Ridge, Lasso, RandomForest, GradientBoosting, SVM  
- **Validation** : GridSearchCV, KFold, MAE/RMSE  
- **Visualisation** : Feature Importance, Boxplots, Heatmaps  

---

## 📂 Structure du dépôt  

```text
anticipation_besoins_consommation
│
├── Notebook_1_Exploration_Feature_Engineering.ipynb
├── Notebook_2_Modelisation_TotalGHGEmissions.ipynb
├── Notebook_3_Modelisation_SiteEnergyUseWN.ipynb
├── Martineau_Alexandre_4_presentation_05204.pdf
└── README.md
```
