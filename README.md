# H1N1 Vaccination Prediction Project

## 1. Project Overview
This project predicts whether individuals received the H1N1 flu vaccine using the **National 2009 H1N1 Flu Survey** data.  
The goal is to build a **binary classification model** that estimates the likelihood of vaccination based on demographics, health behaviors, and public perceptions.

## 2. Business Understanding
Vaccination is a key public health tool, but uptake is often affected by **hesitancy, misinformation, and socioeconomic barriers**.

- **Problem Statement:** Identify people likely or unlikely to get the H1N1 vaccine to improve planning and delivery of vaccination programs.  
- **Stakeholders:** Public health organizations, government policymakers, healthcare providers.  
- **Key Question:** Which factors (e.g., doctor recommendations, perceived risk, demographics) best predict vaccine uptake?

## 3. Data Description
- **Records:** 26,707  
- **Features:** 38  

**Target Variable:** `h1n1_vaccine` (0 = No, 1 = Yes)  

**Feature Types:**  
- **Behavioral:** Hand washing, face mask usage, social distancing  
- **Perceptions:** Vaccine effectiveness, perceived risk  
- **Demographics:** Age, education, race, sex, income  

**Data Challenges:**  
Some features had high missing values (e.g., `health_insurance` ~46%, `employment_industry` ~50%), which were handled using imputation.

## 4. Methodology
1. **Data Cleaning:** Imputed missing values and encoded categorical variables.  
2. **Exploratory Data Analysis (EDA):** Studied correlations between behaviors and vaccination status.  
3. **Class Imbalance:** Applied **SMOTE** to balance vaccinated vs. non-vaccinated classes.  
4. **Modeling:** Trained and compared:  
   - Logistic Regression  
   - Decision Tree Classifier  
5. **Hyperparameter Tuning:** Used **GridSearchCV** to optimize the Decision Tree for higher AUC.

## 5. Key Results
- **Base Decision Tree:** AUC = 0.649  
- **Tuned Decision Tree:** AUC = 0.804  
- **Logistic Regression (tuned):** AUC = 0.821  

Tuned models outperform the baseline and show strong ability to separate vaccinated from non-vaccinated individuals. Logistic Regression slightly outperforms the Decision Tree.

## 6. Conclusions & Recommendations

**Conclusion:**  
- Hyperparameter tuning improved the Decision Tree by **over 15% in AUC**, making it much better at identifying people likely to vaccinate.  
- Logistic Regression achieved the highest AUC (0.821), confirming its strong predictive performance.  
- Top predictors include **doctor recommendations** and **perceived vaccine effectiveness**, showing these factors strongly influence vaccination decisions.

**Recommendations (based on model results):**  
1. **Leverage Top Predictors:** Use insights from the models to guide outreach. Focus on doctor recommendations and perceptions of vaccine effectiveness to increase uptake.  
2. **Target Low-Probability Groups:** The models identify individuals with low likelihood of vaccination. Public health campaigns should prioritize these groups with tailored messaging.  
3. **Use Tuned Models for Planning:** Deploy the tuned Decision Tree (AUC = 0.804) and Logistic Regression (AUC = 0.821) to allocate vaccines and educational resources efficiently.  
4. **Monitor and Update:** Retrain models periodically with new survey data to maintain accuracy as public perceptions and behaviors change.  
5. **Improve Data Quality:** Reduce missing values in critical variables like health insurance and employment information to strengthen model predictions in the future.

## 7. How to Run the Notebook
- **Prerequisites:** Python 3.x, Jupyter Notebook  
- **Libraries:** pandas, numpy, matplotlib, seaborn, scikit-learn, imblearn  
- **Execution:** Open `index.ipynb` and run all cells to reproduce data cleaning, modeling, and evaluation steps.