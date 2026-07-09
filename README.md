# Customer Segmentation with Clustering

Unsupervised learning project that segments 68,300 e-commerce customers into five actionable profiles using K-Means, hierarchical clustering, PCA and t-SNE.

## Business context

A transnational e-commerce company (customers across 47 countries, 5 continents) needed to understand its customer base to improve marketing efficiency. The raw dataset contained 951,668 order-level rows with no ready-to-use customer-level features, so the first step was building a customer-level view from scratch.

## Approach

1. **Data cleaning** — handled missing values, removed duplicates, standardised currency fields.
2. **Feature engineering** — aggregated order-level data into one row per customer and built five behavioural/demographic metrics: **Frequency**, **Recency**, **Customer Lifetime Value (CLV)**, **Average Unit Cost**, and **Age**.
3. **Scaling & pipeline** — `StandardScaler` + `scikit-learn` `Pipeline` to keep preprocessing and modelling reproducible.
4. **Choosing k** — compared the Elbow method, Silhouette score, and Davies-Bouldin Index; all three converged on **k = 5**.
5. **Clustering** — K-Means (k=5) as the primary model, validated independently with hierarchical clustering (Ward linkage) and a dendrogram.
6. **Dimensionality reduction** — PCA (65.25% variance explained) and t-SNE for 2D visualisation of the five segments.

## Results — five customer segments

| Segment | Size | Profile |
|---|---|---|
| VIP / Champion Customers | 11,226 | Highest frequency (33 orders), lowest recency (120 days), highest CLV ($4,914). Top retention priority. |
| Young Active Customers | 22,565 | Youngest segment (mean age 28), moderate frequency, recent purchases. Best fit for digital/social marketing. |
| Older Loyal Customers | 20,191 | Moderate activity, oldest segment (mean age 60). Needs age-appropriate loyalty campaigns. |
| Churned Customers | 10,582 | Lowest frequency and CLV, ~3 years since last purchase (1,116 days). Target for win-back campaigns. |
| Premium Infrequent Buyers | 3,736 | Buys rarely but spends the most per item ($181 avg). Target for premium/high-margin promotions. |

Full methodology, visualisations and business recommendations are in [`report.pdf`](report.pdf) and the notebook.

## Tech stack

Python · pandas · NumPy · scikit-learn (KMeans, PCA, t-SNE, Pipeline) · SciPy (hierarchical clustering) · matplotlib · seaborn

## Repository contents

- `customer_segmentation_clustering.ipynb` — full analysis, from raw data to final segments
- `report.pdf` — written report with key findings and stakeholder recommendations

## Data source

E-commerce dataset provided by SAS (2024) as part of the Cambridge Data Science Career Accelerator programme. Business context is fictitious; the dataset itself is real-world.
