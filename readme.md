Admission Feature Analysis
Welcome to the Admission Feature Analysis repository! This project analyzes factors influencing undergraduate admission outcomes in Bangladesh, predicting whether students are admitted to public or private universities. The analysis is performed in a Jupyter notebook (admission.ipynb) using a survey dataset and advanced machine learning techniques like Random Forest and XGBoost.

📊 Dataset
The dataset, Undergraduate Admission Test Survey in Bangladesh.csv, contains 505 unique samples (after preprocessing) with the following features:

Academic Features:
SSC_GPA: Secondary School Certificate GPA (out of 5.0)
HSC_GPA: Higher Secondary Certificate GPA (out of 5.0)


Socioeconomic Features:
Family_Economy: Family economic status (1-5 scale)
Residence: Urban (1) or rural (0)
Family_Education: Family education level (categorical)


Lifestyle Features:
Politics: Political involvement (0 or 1)
Social_Media_Engagement: Time spent on social media (1-5 scale)
Residence_with_Family: Living with family (0 or 1)
Bad_Habits: Presence of bad habits (0 or 1)
Relationship: In a relationship (0 or 1)
External_Factors: Influence of external factors (0 or 1)


Educational Context:
Duration_of_Study: Years spent preparing for admission
College_Location: Urban (1) or rural (0)
School_Location: Urban (1) or rural (0)


Target:
University: Public (1) or private (0) university admission



Engineered Features:

Weighted_GPA: Weighted combination of SSC and HSC GPA
GPA_Difference: Difference between SSC and HSC GPA
GPA_Difference_Abs: Absolute GPA difference
GPA_Difference_Norm: Normalized GPA difference
Study_Social_Ratio: Ratio of study duration to social media engagement
Distraction_Score: Composite score of distractions (e.g., bad habits, relationships)
GPA_Social_Interaction: Interaction between Weighted_GPA and Study_Social_Ratio


📂 Project Structure

admission.ipynb: Core Jupyter notebook with data preprocessing, EDA, feature engineering, modeling, and evaluation.
Undergraduate Admission Test Survey in Bangladesh.csv: Dataset (not included; users must provide their own).
README.md: This file, your guide to the project.


🛠 Prerequisites
To run the notebook, ensure you have:

Python 3.6+
Required libraries:pip install pandas numpy scikit-learn xgboost imbalanced-learn matplotlib seaborn statsmodels




🔍 Analysis Overview
The notebook is structured as follows:
1. Data Preprocessing

Duplicates: Removed 95 duplicates, resulting in 505 samples.
Missing Values: Imputed 3 missing HSC_GPA values with the median.
Outliers: Winsorized one SSC_GPA outlier (< 3.0) to 3.0.
Multicollinearity: Identified high VIF for SSC_GPA (182.56) and HSC_GPA (159.83).

2. Exploratory Data Analysis (EDA)

Visualized GPA_Difference distribution by university type using histograms with KDE.
Confirmed balanced classes: 256 public vs. 249 private university admissions.

3. Feature Engineering

Created interaction and normalized features to capture complex relationships.
Examples: Weighted_GPA, GPA_Difference_Abs, GPA_Social_Interaction.

4. Modeling

Baseline Random Forest:
F1-score: 0.653 ± 0.148


XGBoost with SMOTEENN:
Initial F1-score: 0.654 ± 0.087
Tuned F1-score (GridSearchCV): 0.790
Best parameters:{
    'n_estimators': 200,
    'max_depth': 3,
    'learning_rate': 0.1,
    'subsample': 0.7,
    'colsample_bytree': 0.7,
    'min_child_weight': 5,
    'gamma': 0
}




Metrics: F1-score, precision, and recall via 5-fold cross-validation.

5. Feature Importance (Tuned XGBoost)

Top features:
Weighted_GPA: 0.569
GPA_Difference_Abs: 0.200
GPA_Difference: 0.198


Negligible features: Residence_with_Family, Distraction_Score, GPA_Difference_Norm.


🎯 Results

The tuned XGBoost model outperforms the baseline Random Forest, improving the F1-score from 0.653 to 0.790.
Academic performance (e.g., Weighted_GPA, GPA differences) drives admission outcomes.
High multicollinearity between SSC_GPA and HSC_GPA suggests opportunities for dimensionality reduction.


🚀 How to Run

Clone the repository:git clone https://github.com/your-username/admission-feature-analysis.git


Add the dataset: Place Undergraduate Admission Test Survey in Bangladesh.csv in the root directory.
Install dependencies:pip install pandas numpy scikit-learn xgboost imbalanced-learn matplotlib seaborn statsmodels


Run the notebook:jupyter notebook admission.ipynb




🌱 Future Work

Reduce Multicollinearity: Apply PCA or feature selection to handle high VIF features like SSC_GPA and HSC_GPA.
Explore New Models: Test LightGBM, CatBoost, or ensemble methods.
Feature Selection: Use techniques like Recursive Feature Elimination (RFE).
New Features: Experiment with additional interactions or nonlinear transformations.


🤝 Contributing
We welcome contributions! To contribute:

Fork the repository.
Create a feature branch (git checkout -b feature/your-feature).
Commit changes (git commit -m 'Add your feature').
Push to the branch (git push origin feature/your-feature).
Open a pull request.

Please report bugs or suggest improvements via GitHub Issues.

📜 License
This project is licensed under the MIT License. See the LICENSE file for details.

🙌 Acknowledgments

Thanks to the contributors of the open-source libraries used in this project.
Inspired by the need to understand factors driving university admissions in Bangladesh.

