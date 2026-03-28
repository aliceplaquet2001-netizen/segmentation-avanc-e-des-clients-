# segmentation-avanc-e-des-clients-
Segmentation Avancée des Clients &amp; Analyse de Rétention
# Segmentation Avancée des Clients & Analyse de Rétention  
**Customer Personality Analysis**

**Niveau : Avancé**  
**Outils : Python (pandas, Plotly, scikit-learn, seaborn)**  
**Dataset : Customer Personality Analysis (Kaggle)**  
**Date : Mars 2026**  
**Auteur : Alice Plaquet**

---

### 📋 Contexte business

Étude d’une base de **2 240 clients** d’une entreprise de produits alimentaires et vins haut de gamme.  
L’objectif est de **segmenter les clients** selon leur comportement d’achat, leur profil démographique et leur réponse aux campagnes marketing afin d’optimiser la rétention, augmenter la valeur vie client (CLV) et cibler plus efficacement les futures campagnes.

---

### 🎯 Objectifs de l’analyse

- Nettoyage et feature engineering complet du dataset
- Analyse exploratoire (EDA) + matrice de corrélations
- Construction d’un scoring RFM (Recency, Frequency, Monetary)
- Segmentation par clustering non supervisé (K-Means)
- Profil détaillé de chaque segment
- Recommandations business actionnables avec estimation d’impact

---

### 🗄️ Données utilisées

- **Source** : [Customer Personality Analysis](https://www.kaggle.com/datasets/imakash3011/customer-personality-analysis)  
- **Fichier** : `marketing_campaign.csv` (2 240 lignes, 29 colonnes)  
- **Volume après nettoyage** : 2 216 clients  
- **Variables clés** : revenu, âge, éducation, situation familiale, dépenses par catégorie, canaux d’achat, campagnes acceptées, etc.

---

### 🛠️ Méthodologie

**Approche** : Ask → Prepare → Process → Analyze → Share → Act

1. **Nettoyage** : suppression des valeurs manquantes (Income), création de features métier  
2. **Feature Engineering** :
   - Âge, Total_Spent, Total_Purchases, Has_Child, Customer_Seniority
   - Scoring RFM (quintiles)
3. **EDA** : distributions, corrélations, visualisations Plotly
4. **Clustering** : K-Means après standardisation (k=4 déterminé par méthode Elbow)
5. **Interprétation** : profils business + recommandations chiffrées

---

### 📈 Analyses & Résultats clés

#### 1. Matrice de corrélations (variables principales)
- `Total_Spent` ↔ `Total_Purchases` : **0.76** (très forte)
- `Income` ↔ `Total_Spent` : **0.67**
- `NumStorePurchases` ↔ `Total_Purchases` : **0.82** (canal dominant chez les gros acheteurs)

#### 2. Segmentation finale – 4 clusters

| Segment                          | % Clients | Recency | Total_Purchases | Total_Spent | Revenu moyen | Âge moyen | % avec enfants | Achats Web | Achats Magasin | Interprétation business                  |
|----------------------------------|-----------|---------|-----------------|-------------|--------------|-----------|----------------|------------|----------------|------------------------------------------|
| **0 – Fidèles Seniors Premium**  | 25,5 %    | 44,9    | **20,9**        | 980 $       | 66 052 $     | **68,7**  | 61 %           | 5,9        | 7,9            | Clients âgés, très fidèles et dépensiers |
| **1 – Familles Modestes Inactives** | 25,5 % | **75,6**| 9,2             | 144 $       | 37 422 $     | 54,7      | **89 %**       | 2,6        | 3,6            | À risque de churn élevé                  |
| **2 – Nouveaux Clients Faible Valeur** | 26,6 % | **24,3**| 8,7             | 127 $       | **35 143 $** | 52,0      | 87 %           | 2,4        | 3,5            | Récent mais non converti                 |
| **3 – Premium Jeunes Haut Revenu** | 22,3 %  | 52,8    | **21,9**        | **1 284 $** | **73 844 $** | **48,5**  | **46 %**       | 5,7        | **8,7**        | **Meilleurs clients** de la base         |

---

### 💡 Insights clés

1. **Les segments Premium (0 + 3)** représentent **47,8 %** des clients mais concentrent l’essentiel des dépenses.
2. **Le segment 3** est le plus rentable : jeunes, hauts revenus, peu d’enfants, très actifs en magasin.
3. **Les segments 1 et 2** sont à risque : faibles dépenses, forte présence d’enfants, soit inactifs soit non convertis.
4. **L’âge et la présence d’enfants** sont les variables les plus discriminantes.
5. **Les achats en magasin** dominent chez les meilleurs clients.

---

### 🚀 Recommandations actionnables

| Recommandation                                           | Segment ciblé     | Impact estimé               | Priorité |
|----------------------------------------------------------|-------------------|-----------------------------|----------|
| Campagnes VIP + événements privés + remises exclusives   | 0 et 3            | +18–25 % de CA              | ★★★★★    |
| Réactivation "famille" avec offres personnalisées        | 1                 | Réduction churn –20–30 %    | ★★★★     |
| Welcome pack + upsell dans les 30 premiers jours         | 2                 | +35–45 % de conversion      | ★★★★★    |
| Bundles famille + promotions web ciblées                 | 1 et 2            | +12–18 % de panier moyen    | ★★★★     |
| Renforcement présence magasin + événements locaux        | 0 et 3            | +10–15 % de CA magasin      | ★★★      |

---

### 📁 Fichiers du repository

- `marketing_campaign.csv` → Dataset original  
- `notebook/` → Notebook Google Colab complet (étapes 1 à 13)  
- `images/` → Captures des graphiques (Elbow, corrélations, profils, etc.)  
- `README.md` → Ce fichier  

**Auteur** : Alice Plaquet  
**Date** : Mars 2026  
**Statut** : Projet de portfolio Data Analyst – Niveau Avancé
