# House-price-prediction-using-linear-regression
In this project I built a linear regression algorithm from scratch to predict the price of the houses based on different features

# Preprocessing
In this project I did 3 steps of preprocessing:
## Step 1: Basic Information
1. **Data Types**:
   - Identify the data types present in the dataset (e.g., numerical, categorical, datetime).
2. **Range of Values**:
   - Explore the range of values for numerical columns (mean, max, count, etc.).
3. **Column Names**:
   - List of all column names present in the dataset.
4. **Null Values**:
   - Check for missing or null values in each column.
5. **Duplicate Values**:
   - Identify and handle any duplicate rows or observations.

## Step 2: Encoding Categorical Features
- Convert categorical features to numerical representation for machine learning purposes.

## Step 3: Extracting Insights for Feature Importance
- Perform analysis techniques to identify important features in the dataset.


# Goals
Building a fast, accurate and reliable linear regression model 

## Data
The detailed data was collected through https://www.kaggle.com/datasets/yasserh/housing-prices-dataset.
<br> The original dataset contained 545 records and 13 features including target value. After cleaning and eliminating unnecessary features, the number of records remained unchanged at 545, but the number of features decreased to 8.
<img src="./Assets/relation.png" style="max-width: 540px"/>
These plots demonstrate a clear relationship between price (target value) and 12 other features. Among these features, the strongest correlations exist with area, bedrooms, bathrooms, parking, and stories. Conversely, weaker correlations are observed with guestroom, basement, hotwatering, and furnishing status. Consequently, removing these features with weaker correlations to price might potentially enhance the model accuracy and expedite gradient descent speed.

## Building the Model
Linear regression is an algorithm sensitive to the scale of its features. This sensitivity can affect its performance. Therefore, the initial step in constructing this algorithm involves rescaling the 'area' feature, primarily because its range significantly differs from the other features. Once rescaled, I proceeded to define the cost function and the fit function

  <img src="./Assets/cost_no rescale.png"  />
 
  <img src="./Assets/predict no rescale.png" /> 
<b>These plots depict the cost function (above) and the difference between predicted values and target values (below) for a model where feature scaling was not applied. In this scenario, I found it necessary to define an extremely small learning rate and a high number of learning iterations to train the model. However, Although the accuracy was good, this approach was inefficient.</b>

After rescaling the data, I retrained the model, and this time, there was no need to select an excessively small learning rate or use a high number of iterations. I opted for an alpha of 0.01 and conducted 50 iterations with 5-fold cross-validation. The output of the second model is presented below:
  <img src="./Assets/cost_iterations = 20alpha0.01,fold10.png"  />
 
  <img src="./Assets/predict_iterations = 20 alpha0.01,fold10.png" /> 

This revised model exhibited improved speed; however, the achieved accuracy was unsatisfactory. Consequently, I increased the number of iterations to 1000 in an attempt to enhance the model's performance.
    <img src="./Assets/cost_iterations = 1000alpha0.01,fold10.png"  />
 
  <img src="./Assets/predict_iterations = 1000, alpha0.01,fold5.png" /> 


Despite observing relatively small changes in the cost function after iteration 50, I noticed a subsequent increase in accuracy. The final plot depicting the difference between predicted and actual values indicates an improvement, suggesting that this model is more accurate.
## Conclusion

To conclude, by cleaning the data and selecting important features, I observed that properly scaling features significantly influences a linear regression model's performance. Comparing scaled and unscaled features highlighted the substantial impact of scaling on the accuracy of model predictions. This process demonstrated the crucial role of appropriately preparing the data, particularly by scaling features, in ensuring more reliable predictions when using linear regression or any algorthms which is gradient based.

