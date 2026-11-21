# Country Development Clustering using K-means and DBSCAN

**Team Nexus Innovators** | CSE 12th Batch, CCN University of Science & Technology
Beginner Machine Learning Project (unsupervised learning / clustering)

## Overview
This project groups 167 countries by level of development using nine socio-economic and health indicators: child mortality, exports, health spending, imports, income, inflation, life expectancy, total fertility and GDP per capita. Two clustering algorithms are applied and compared: **K-means** and **DBSCAN**.

## Key Results
| Method | Setting | Result | Silhouette |
|---|---|---|---|
| K-means | k = 3 | Low / middle / high development groups of 47 / 84 / 36 countries | 0.283 |
| DBSCAN | eps = 1.5, min_samples = 3 | Clusters of 139 and 3 countries, plus 25 noise points | 0.226 (non-noise points only) |

- K-means produced interpretable development tiers, with mean life expectancy of 59.2, 72.8 and 80.1 years across the three groups.
- DBSCAN mainly isolated extreme countries (very wealthy economies and countries with extreme child mortality or inflation) and placed most countries in one dense cluster.
- Silhouette scores are modest, so the groups describe a continuum rather than sharp categories.

## Repository Structure
```
data/          Country-data.csv, data-dictionary.csv
notebooks/     Country_Clustering_KMeans_DBSCAN.ipynb
figures/       Generated figures
results/       Cluster labels, DBSCAN parameter grid, metrics (JSON)
paper/         Project paper (PDF, IEEE style)
```

## Methodology
1. Inspect the data (no missing values, no duplicates in 167 rows).
2. Standardise all features with z-scores (required for distance-based methods).
3. K-means: test k = 2 to 10 using inertia, silhouette score and Davies-Bouldin index; final model k = 3 with k-means++ initialisation.
4. DBSCAN: use the 5th-nearest-neighbour distance plot and a grid search over eps (0.8 to 3.0) and min_samples (3 to 10). The final setting is the highest-silhouette configuration with at least 2 clusters and at most 15% noise.
5. Visualise clusters in two dimensions with PCA and profile each cluster in original units.

## How to Run
**Option 1: Google Colab (recommended)**
1. Open `notebooks/Country_Clustering_KMeans_DBSCAN_Colab.ipynb` in Google Colab (File, Upload notebook).
2. Click Runtime, then Run all.
3. Upload `data/Country-data.csv` when the data-loading cell asks.

Run from the repository root. The script reads `data/Country-data.csv` and writes figures to `figures/` and results to `results/`. The random state is fixed at 42.

## Dataset
Country Development ("Unsupervised Learning on Country Data"), Kaggle:
Run from the repository root. The script reads `data/Country-data.csv` and writes figures to `figures/` and results to `results/`. The random state is fixed at 42.

## Dataset
Country Development ("Unsupervised Learning on Country Data"), Kaggle:
https://www.kaggle.com/datasets/rohan0301/unsupervised-learning-on-country-data

## Limitations
Small sample (167 countries), unstated reference year for the data, strongly correlated and skewed indicators, a partly subjective choice of k = 3 (silhouette scores for k = 2 to 5 are nearly flat), and no external validation.

## Team
- Niloy Kumar Shil(ID:111223051)
- Sanij Hossen Joy(ID:111223023)
