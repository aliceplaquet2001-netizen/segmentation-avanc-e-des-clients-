# Segmentation Avancée des Clients & Analyse de Rétention  
**Customer Personality Analysis + Clustering + CLV**

**Outils :** Python (pandas, scikit-learn, Plotly, seaborn, scipy)  
**Dataset :** Customer Personality Analysis (Kaggle)  
**Date :** Mars 2026  
**Auteur :** Alice Plaquet

---

### 📋 Contexte business

Analyse complète de **2 240 clients** d’une entreprise de produits premium (vins & alimentation).  
Objectif : segmenter les clients, calculer leur **Customer Lifetime Value (CLV)** et proposer des actions marketing ciblées pour maximiser la rétention et le CA.

---

### 🎯 Objectifs

- Feature engineering + scoring RFM  
- Clustering non supervisé (K-Means + validation)  
- Visualisation PCA + comparaison Hierarchical Clustering  
- Calcul de CLV par segment  
- Recommandations business chiffrées

---

### 🗄️ Données

- **Source :** [Kaggle – Customer Personality Analysis](https://www.kaggle.com/datasets/imakash3011/customer-personality-analysis)  
- **Volume :** 2 216 clients après nettoyage  
- **Features créées :** Age, Total_Spent, Total_Purchases, Has_Child, Customer_Seniority, RFM Score, CLV_3ans

---

### 🛠️ Méthodologie

1. Nettoyage & Feature Engineering  
2. EDA + Matrice de corrélations  
3. RFM Scoring  
4. **K-Means (k=4 validé par Elbow)**  
5. **Validation :** Silhouette Score + Davies-Bouldin Index  
6. **PCA 2D** pour visualiser la séparation  
7. **CLV** calculée sur 3 ans  
8. Comparaison Hierarchical Clustering (dendrogramme)

---

### 📈 Résultats clés

#### Validation des clusters
- **Silhouette Score :** 0.238 (modéré – typique des données clients réelles)  
- **Davies-Bouldin Index :** 1.532  
→ Les clusters sont acceptables et **business-cohérents** (confirmé par PCA et profils).

#### Visualisation PCA 2D des clusters
Les 4 segments montrent une séparation visible malgré un léger chevauchement (cluster 0 jaune vs cluster 3 turquoise particulièrement distincts).

#### Profil final des segments + CLV

| Segment                          | % Clients | Recency | Total_Purchases | Total_Spent | Revenu   | Âge | CLV_3ans | % enfants | Interprétation                  |
|----------------------------------|-----------|---------|-----------------|-------------|----------|-----|----------|-----------|---------------------------------|
| **0 – Fidèles Seniors Premium**  | 25,5 %    | 45      | 20,9            | 980 $       | 66k $    | 69  | **250 $**| 61 %      | Clients âgés, très fidèles      |
| **1 – Familles Modestes Inactives** | 25,5 % | **76**  | 9,2             | 144 $       | 37k $    | 55  | **37 $** | **89 %**  | Risque churn élevé              |
| **2 – Nouveaux Faible Valeur**   | 26,6 %    | **24**  | 8,7             | 127 $       | 35k $    | 52  | **32 $** | 87 %      | Récent mais non converti        |
| **3 – Premium Jeunes Haut Revenu** | 22,3 %  | 53      | **21,9**        | **1 284 $** | **74k $**| **49** | **326 $**| **46 %**  | **Meilleurs clients**           |

---

### 💡 Insights clés

1. Les segments **0 + 3** (47,8 % des clients) génèrent **la quasi-totalité du CA** (CLV 250 $ et 326 $).  
2. Le **segment 3** est le plus rentable : jeunes, hauts revenus, très actifs.  
3. Les segments **1 et 2** ont une CLV très faible et un fort risque de churn.  
4. La PCA confirme que le revenu et les dépenses sont les principaux drivers de séparation.

---

### 🚀 Recommandations actionnables (avec CLV)

| Recommandation                                      | Ciblage     | Impact estimé sur CLV / CA          | Priorité |
|-----------------------------------------------------|-------------|-------------------------------------|----------|
| Programme VIP + remises exclusives + événements    | 0 + 3       | +20–30 % CLV                        | ★★★★★    |
| Réactivation "famille" (offres bundles enfants)    | 1           | +40–60 % CLV (de 37 $ → 55 $+)      | ★★★★     |
| Welcome + upsell automatisé (30 premiers jours)    | 2           | +50–70 % CLV (de 32 $ → 50 $+)      | ★★★★★    |
| Campagnes web + promotions ciblées                 | 1 + 2       | +15–25 % panier moyen               | ★★★★     |
| Événements magasin locaux                          | 0 + 3       | +12–18 % CA magasin                 | ★★★      |

---

### 📁 Repository

- `marketing_campaign.csv`  
- `notebook/` → Colab complet (17 cellules)  
- `images/` → PCA, Elbow, Corrélations, Dendrogramme, Profils  
- `README.md`

**Auteur :** Alice Plaquet
