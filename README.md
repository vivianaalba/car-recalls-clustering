# car-recalls-clustering
Using unsupervised learning, we clustered 60 years of NHTSA recall data to uncover patterns in vehicle safety severity across manufacturers, components, and time.

# Project Overview
This project analyzes over 60 years (1966–2025) of U.S. vehicle recall data from the National Highway Traffic Safety Administration (NHTSA) to understand how recall severity emerges and varies across manufacturers, defect types, and historical periods. Using unsupervised learning (K-Means) and extensive exploratory analysis, the project identifies meaningful patterns in recall severity that are not visible from simple recall counts alone.

This work highlights systemic safety vulnerabilities, supports improved regulatory oversight, and provides insights that can ultimately help consumers make more informed vehicle purchase decisions.

## Authors
This project was collaboratively developed by: Anastasia Haidar, Viviana Alba, Hyunseo Kim, Charley Wang

## Project Goals
- Cluster vehicle recalls into low, medium, and high severity groups based on the number of potentially affected vehicles
- Examine how severity varies by:
    - Manufacturer
    - Component type
    - Year / temporal trends
- Validate clustering quality using multiple internal metrics
- Identify systemic patterns in automotive safety performance
- Highlight opportunities for future predictive modeling and consumer-facing risk tools

## Tools & Technologies
- Python (pandas, numpy, scikit-learn, seaborn, matplotlib)
- Machine Learning: K-Means, Cluster Validation Metrics
- EDA: Distribution analysis, heatmaps, crosstabs, temporal patterns

## Key Findings
1. Severity is strongly linked to component criticality
    - High-severity recalls most often involve:
    - Electrical system
    - Airbags
    - Fuel system
    - Other safety-critical components
    - Low-severity recalls typically involve equipment or minor structural defects.

2. Manufacturers differ in proportional severity risk
    - Large manufacturers (GM, Ford, Chrysler) lead in absolute recall volume.
    - But Toyota, Hyundai, Honda, and Nissan show higher relative rates of severe recalls.
    - This suggests deeper design or platform-specific vulnerabilities.

3. Severity trends changed over time
    - High-severity recalls rise sharply starting in the 1990s.
    - Trends align with increased vehicle complexity and evolving regulation.

4. Clustering validation confirms meaningful structure

Metrics for k=3 clusters:
- Silhouette Score: 0.266 
- Davies–Bouldin Index: 1.297
- Calinski–Harabasz Index: 10,583.5

These results indicate moderate but meaningful separation—expected for a large, noisy real-world dataset.

## Methods
Data Processing & Cleaning
- Handled missing values via imputation or omission where appropriate
- Dropped non-vehicle recall types (tire, child seat, equipment)
- Extracted year, month, and weekday from recall dates
- Log-transformed skewed count variables
- One-hot encoded manufacturer categories
- Standardized numerical features

Clustering Workflow
- K-Means clustering on:
- Log-transformed affected vehicle count
- Recall year
- Manufacturer (encoded)
- Optimal k=3 chosen using:
- Elbow method
- Silhouette analysis
- CH-index comparison
- Retrained final model on full dataset

Evaluation
- Cluster separation validated using:
- Silhouette Score
- Davies–Bouldin Index
- Calinski–Harabasz Index
- Component-level heatmaps
- Manufacturer severity distribution analysis
- Temporal trend visualization

## Future Work
This project opens several pathways for deeper analysis:
- Integrating production volume data to normalize severity rates
- Applying NLP to defect narratives for automated risk detection
- Building predictive models for high-severity recall risk
- Testing alternative clustering frameworks (DBSCAN, hierarchical)
- Forecasting recall trends using time series models
- Linking recalls to crash/injury data for real-world safety insights
- Developing standardized consumer-facing safety dashboards

## Dataset and References
[1] Automotive Research Center, "What You Need to Know about Vehicle Safety Recalls," AAA – ACE, American Automobile Association, Mar. 4, 2019. [Online]. Available: https://www.ace.aaa.com/automotive/advocacy/automotive-safety-recalls-explained.html. <br>
[2] K. Ahsan, “Trend Analysis of Car Recalls: Evidence from the US Market,” International Journal of Managing Value and Supply Chains, vol. 4, pp. 1–16, December 2013, doi: 10.5121/ijmvsc.2013.4401. <br>
[3] National Highway Traffic Safety Administration, "Recalls Data," U.S. Data.gov, updated Oct. 5, 2025. [Online]. Available: https://catalog.data.gov/dataset/recalls-data. <br>
[4] U.S. Department of Transportation, "A Moment in Time: Highway Safety Breakthrough," FHWA Highway History Website. [Online]. Available: https://highways.dot.gov/highway-history/general-highway-history/moment-time-highway-safety-breakthrough. <br>

## Repository Contents
```bash
├── data/
│   ├── recalls_data.csv          # raw recalls data from Data.gov
│   ├── cleaned_recalls_data.csv  # cleaned recalls data
├── cleaning_eda.ipynb            # Data cleaning and feature engineering
├── clustering.ipynb              # K-Means model / validation, Manufacturer, component, and time analysis
├── technical_report.pdf          # Full written report for the project
└── README.md                     # Project overview and documentation
