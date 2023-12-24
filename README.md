# Sentiment Analysis of IMDB Movie Reviews

## Introduction
The Sentiment Analysis project aimed to classify IMDB movie reviews based on their sentiment. The dataset comprised 36,000+ reviews along with movie ratings ranging from 0 to 10. The primary objective was to develop a machine learning model capable of categorizing reviews into three classes: negative, neutral, and positive sentiments.

## Data Collection
The dataset was collected using my web scraping code that retrieved movie reviews and their associated ratings from IMDB.

## Exploratory Data Analysis and Preprocessing
- **Data Cleaning:** Removed null values and irrelevant characters, handled punctuation, and eliminated stop words. The size of data after removing null values were 32505 rows and 2 columns
- **Labeling:** Categorized reviews into sentiment classes based on their ratings (1-3 as negative, 4-6 as neutral, 7-10 as positive).
- **Class Imbalance Check:** Identified an imbalance among sentiment classes, with the negative class having the lowest representation.
- <img src="./Plots/class imbalance.png"  />
- **Tokenization:** Processed the cleaned data and organized it into a structured DataFrame for further analysis.

## Model Building
### 1. Blazing Text
- Utilized Blazing Text for initial classification.
- Encountered challenges due to class imbalance, resulting in an accuracy of approximately 47%.

### 2. Word2Vec Embedding & XGBoost
- Employed Word2Vec for embedding and trained an XGBoost model for classification.
- Experienced a notable increase in accuracy compared to Blazing Text, achieving around 63% accuracy for test data and %77 for training data.
- <img src="./Plots/learning curve xgboost model.png"  />
This plot shows that the model is not either underfit or overfit and it is trained well.
- The confusion matrix for this model is showing below:
- <img src="./Plots/confusion matrix xgboost model.png"  />
To map the classes with the XGBoost model I had to change the class to 0, 1 and 2
- However, faced challenges related to high dimensionality and slower processing speed.

### 3. PCA for Dimensionality Reduction
- Implemented Principal Component Analysis (PCA) to reduce dimensions while maintaining accuracy.
- Significantly improved code efficiency and model building speed without compromising accuracy.


These plots are showing the leaning curve, cost function and confusion matrix for the model.
<img src="./Plots/learning curve xgboost-pca model.png"  />
<img src="./Plots/cost function xgboost pca model.png"  />
<img src="./Plots/confusion matrix xgboost-pca model.png"  />
### 4. Addressing Class Imbalance
- Attempted to enhance accuracy by oversampling the minority class (negative sentiment).
- Despite efforts, the maximum accuracy plateaued around %61.

### 5. SVM with RBF Kernel
- Explored Support Vector Machines (SVM) using an RBF kernel as an alternative model.
- Achieved similar accuracy results (~62%) to XGBoost, reaffirming the consistency of accuracy across models.
These plots are showing the leaning curve, cost function and confusion matrix for the SVM model.
<img src="./Plots/learning curve svm-pca model.png"  />
<img src="./Plots/confusion matrix svm-pca model.png"  />

In order to find the best value for the C to train the SVM I used a vector of random numbders from 0 to 100 and I found 10 is a good number to build the model
<img src="./Plots/svm C parameter choose.png"  />
## Conclusion and Insights
The project highlighted several crucial findings:
- Maximum accuracy plateaued at around 63% due to inherent challenges like class imbalance.
- Consistent accuracy levels observed across different models (XGBoost, SVM) suggested limitations in surpassing the 63% mark.
- Insights gained in handling class imbalances and managing high dimensions using PCA for more efficient modeling.
