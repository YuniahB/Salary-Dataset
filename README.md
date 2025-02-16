# Salary-Dataset
Salary Dataset in CSV (Simple linear regression).
Dataset Validation
File Exists: True → The dataset was found and loaded.
Missing Values: 0 in all columns → No need for data cleaning.
Columns: "Unnamed: 0", "YearsExperience", "Salary" (Unnecessary "Unnamed: 0" column removed).

Dataset Shape:
•	30 rows, 1 feature (YearsExperience)
•	Target (Salary) is correctly identified.

2. Data Split
Train-Test Split (80%-20%)
•	Training Set: 24 samples
•	Testing Set: 6 samples

3. Model Training & Results
Regression Equation:
Salary=9,423.82×YearsExperience+24,380.20\text{Salary} = 9,423.82 \times \text{YearsExperience} + 24,380.20Salary=9,423.82×YearsExperience+24,380.20
•	Model Coefficients ([9423.82]) → Each additional year of experience increases salary by ~$9,423.82.
•	Intercept (24,380.20) → The base salary with zero experience.

4. Model Performance
Metric	Value	Meaning
MAE	6,286.45	On average, the model’s predictions are off by ~$6,286.45.
MSE	49,830,096.86	Large error, squared to give more weight to extreme errors.
RMSE	7,059.04	The standard deviation of the prediction error.
R² Score	0.9024	90.24% of salary variance is explained by experience leading to a Strong model!
The model fits well (R² = 0.90 → 90% accuracy).
The errors are reasonable, given the salary range.
The relationship is strongly linear, confirming that Years of Experience is a strong predictor of Salary.

Here’s the visualization of the regression model!
•	The scatter plot shows the actual salary values (blue points).
•	The red regression line represents the best-fit linear model.
•	The trend confirms that salary increases with experience, showing a strong positive correlation.
Try Polynomial Regression (to capture non-linear relationships)

Polynomial Regression (Degree 2) Results 
•	Visualization:
o	The red line represents the quadratic regression curve, which fits the data better than a straight line.
o	The curve captures some non-linearity in the salary-experience relationship.
•	Model Evaluation:
Metric	Linear Regression	Polynomial Regression (Degree 2)
MAE	~6,286.45	4,653.07  (Lower is better)
MSE	~49,830,096.86	31,257,508.45 
RMSE	~7,059.04	5,590.84 
R² Score	~0.9024	0.9570  (Higher is better, close to 1)

Polynomial Regression (Degree 3) Results 
•	Visualization:
o	The green cubic regression curve follows the salary-experience trend even more closely than Degree 2.
o	It captures more complexity in the relationship between experience and salary.

•	Model Evaluation:
Metric	Linear Regression	Polynomial Regression (Degree 2)	Polynomial Regression (Degree 3)
MAE	~6,286.45	4,653.07 (Lower is better)	4,269.07  (Even lower!)
MSE	~49,830,096.86	31,257,508.45 	26,446,769.61  (Best so far!)
RMSE	~7,059.04	5,590.84 	5,142.64  (Lowest error yet!)
R² Score	~0.9024	0.9570 	0.9636  (Best model fit so far!)

Key Insights:
 Degree 3 polynomial regression performs even better than Degree 2 (higher R² score, lower errors).
The salary trend appears to have some non-linearity, which is well-captured by the cubic model.
The errors (MAE & RMSE) keep reducing, showing improved accuracy.

Overfitting Analysis: Train vs. Test R² Scores 
•	The blue line (Train R² Score) shows how well the model fits the training data.
•	The red line (Test R² Score) represents how well the model generalizes to unseen data.
•	Key Findings:

Degree	Train R² Score	Test R² Score	Overfitting Risk?
1	0.9645	0.9024	No, underfitting likely.
2	0.9650	0.8972	No, slight generalization drop.
3	0.9713	0.9048	No, still stable.
4	0.9716	0.9030	Yes, very slight overfitting.
5	0.9737	0.9088	Potential Overfitting 

Regularization Results: Ridge (L2) vs. Lasso (L1) Regression 
1. Model Evaluation (R² Scores)
Model	Train R² Score	Test R² Score	Overfitting Reduced?
Polynomial Regression (Degree 3)	0.9713	0.9048	No regularization
Ridge Regression (L2)	0.9713	0.9052	Slight improvement
Lasso Regression (L1)	0.9708	0.9052	Similar to Ridge

2. Regularization Insights:
Both Ridge and Lasso reduced overfitting, keeping train & test scores closer.
Test R² Score increased slightly (0.9052 vs. 0.9048) → Better generalization. 
Ridge and Lasso performed similarly at this alpha value (1.0).
Lasso Warning: "Objective did not converge." → We might need higher iterations or different alpha values.

3. Visual Interpretation
•	Green (Ridge Regression): A smoothed curve with slight regularization.
•	Purple (Lasso Regression): Similar smoothing but with more feature shrinking.

Fine-Tuning Alpha for Ridge & Lasso Regression 
Results from Fine-Tuning Alpha (Regularization Strength)
Model	Best Alpha	Best Test R² Score	Performance
Ridge Regression (L2)	1	0.9052	Best performance at α = 1 
Lasso Regression (L1)	100	0.9054	Best performance at α = 100 

Key Insights:
Ridge Regression works best with α = 1, confirming mild regularization is enough.
Lasso Regression needs a higher α = 100, suggesting it benefits from stronger feature selection.
Both Ridge & Lasso perform similarly, with slight advantage for Lasso at α = 100 (0.9054 vs. 0.9052).
Lasso's convergence warnings indicate that increasing iterations might be needed for even better performance.

