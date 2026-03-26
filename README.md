# Airbnb Price Tier Classification: ML Analysis
Predicting Budget, Standard, and Premium listings in Melbourne, Australia

## 🎯 Project Overview
This project investigates the key differentiators between Budget, Standard, and Premium Airbnb listings in Melbourne. By analyzing 18,316 listings across 91 features, we developed five machine learning models to predict price tiers with up to 78% accuracy.
### Why This Matters:
1. *For Hosts*: Identify specific property upgrades that justify premium pricing.
2. *For Travelers*: Quantify "value-for-money" across 18,000+ listings.
3. *For Policymakers*: Gain data-driven insights into short-term rental market trends and housing affordability.

## 🏆 Key Findings1. 
Model Performance
### The "Premium" Blueprint
Our analysis revealed that Property Features dominate pricing (81% importance), while Host Experience (tenure/Superhost status) contributes only 5%.
1. *The Big Three*: Room Type (Entire Home), Accommodates (Capacity), and Bedrooms.
2. *The "Free Upgrade"*: Description length is a significant predictor of tier—longer, detailed descriptions correlate with higher tiers.
3. *Thresholds*: Premium listings typically feature an entire home, capacity for 4+ guests, and 11+ amenities.

## 📊 Dataset & PipelineSource: 
Inside Airbnb (Melbourne, Dec 2018)Volume: 18,316 observations | 91 Final Features
### Data Preprocessing Pipeline
1. *Leakage Prevention*: Removed 52 features (direct price, reviews, availability).
2. *Feature Engineering*: * Extracted 40 binary amenity features from raw text.Calculated capacity ratios (e.g., bathrooms-per-guest).Engineered text-derived features (description lengths).
3. *Target Classification*: * Budget: Lowest 27%Standard: Middle 36.4%Premium: Top 36.6%

## 🤖 Models Implemented
1. *Random Forest (ranger)*: Best overall discriminator (91% ROC AUC). Ideal for feature importance.
2. *XGBoost*: High-speed performance, excellent for production-ready deployment.
3. *SVM + PCA*: Achieved highest raw accuracy (78%) by reducing 91 features to 38 principal components.
4. *Logistic Regression*: Provided interpretable coefficients for stakeholder reporting.
5. *k-Nearest Neighbors*: Used as a baseline for instance-based similarity.

## 📁 Project StructureBash├── data/
│   ├── raw/                # Original dataset
│   └── processed/          # Cleaned training/test sets
├── notebooks/
│   ├── 01_EDA.Rmd          # Exploratory analysis
│   ├── 02_preprocessing.Rmd # Data cleaning pipeline
│   └── 03_07_models.Rmd    # Individual model implementations
├── src/                    # Modular R scripts for functions
├── results/                # Visualizations and saved .rds models
└── requirements.R          # Dependency list

## 🚀 Installation & Usage
### Prerequisites
1. R (≥ 4.0.0)
2. Required libraries: tidymodels, tidyverse, ranger, xgboost, e1071

### Setup
#### Clone the repository
git clone https://github.com/Kibisuvictor/airbnb-price-classification.git

#### Install dependencies in R
Rscript requirements.R

#### Reproduce Results
To run the full pipeline from cleaning to model comparison:
rmarkdown::render("notebooks/02_data_preprocessing.Rmd")
rmarkdown::render("notebooks/08_model_comparison.Rmd")

### 🤝 Contributors: 
1. Victor Kibisu - Lead Data Scientist (Problem definition, Preprocessing, RF and slides prep and presentation)
2. Calvin - Feature Engineering & k-NN
3. Gavin - Logistic Regression
4. Subhamay - XGBoost
5. Joel - SVM + PCA & Evaluation and EDA

## 📄 License
This project is licensed under the MIT License - see the LICENSE file for details.
