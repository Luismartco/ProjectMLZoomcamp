### ProjectMLZoomcamp

The following project is the submission for Capstone 2 in the Machine Learning Zoomcamp 2024.

### Data Analysis for Cost Prediction
This project uses a decision tree model to predict cost categorization based on different variables present in a medical dataset. The model classifies costs into three categories and evaluates the relative importance of dataset features for this task.

### Project Structure

#### 1. Data Loading and Exploration
   - A CSV file containing the data is loaded.
   - An initial exploration is performed to understand the columns and data types.

#### 2. Data Preprocessing
   - Rows with missing values are removed.
   - Categorical variables are converted into dummy variables (one-hot encoding).
   - A new column `Costo_categorico` is created to classify costs into three categories using `pd.qcut`.

#### 3. Dataset Splitting
   - The data is split into training (80%) and testing (20%) sets.

#### 4. Model Training
   - A decision tree with a maximum depth of 5 is used.
   - The model is trained on the training set.

#### 5. Model Evaluation
   - Accuracy is calculated, and a classification report is generated for the test set.
   - The decision tree structure is displayed to understand the decision-making process.

#### 6. Feature Importance Analysis
   - A plot of the top 10 features influencing model predictions is generated.

### Results

#### Model Accuracy
- The model achieved an accuracy of **40.00%** on the test set.

#### Feature Importance
The five most important features for predicting costs are:

| Feature                         | Importance |
|---------------------------------|------------|
| Specialty_Neurology             | 0.238697   |
| Specialty_Pulmonology           | 0.224282   |
| Province_Los Guandules          | 0.205819   |
| Specialty_Ophthalmology         | 0.174229   |
| Province_Bayahibe               | 0.156972   |

#### Feature Visualization
![Feature Importance Chart](/media/img.png)

#### Decision Tree Structure
A textual representation of the tree is provided to understand the rules generated during training.

```
|--- Specialty_Neurology <= 0.50
|   |--- Province_Los Guandules <= 0.50
|   |   |--- Specialty_Pulmonology <= 0.50
|   |   |   |--- Province_Bayahibe <= 0.50
|   |   |   |   |--- Specialty_Ophthalmology <= 0.50
|   |   |   |   |   |--- class: 2
|   |   |   |   |--- Specialty_Ophthalmology >  0.50
|   |   |   |   |   |--- class: 0
|   |   |   |--- Province_Bayahibe >  0.50
|   |   |   |   |--- class: 1
|   |   |--- Specialty_Pulmonology >  0.50
|   |   |   |--- class: 2
|   |--- Province_Los Guandules >  0.50
|   |   |--- class: 0
|--- Specialty_Neurology >  0.50
|   |--- class: 1
```

### Requirements
- Python 3.x
- Libraries: `pandas`, `numpy`, `scikit-learn`, `matplotlib`, `seaborn`

### Project Execution
1. Ensure the required libraries are installed.
2. Place the data file (`Pacientes.csv`) in the same directory as the script.
3. Run the Python script.
4. Observe the generated results and visualizations.

### Conclusions
1. Medical specialties and provinces have a significant influence on cost prediction.
2. Although the model's accuracy is not high, it provides valuable insights into key variables.
3. This analysis can guide future improvements in the model and data collection.