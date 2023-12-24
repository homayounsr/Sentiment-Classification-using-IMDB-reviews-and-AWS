# Sentiment Analysis of IMDB Movie Reviews

## Introduction
For this project, I aimed to perform sentiment analysis on IMDB movie reviews. My dataset consisted of over 36,000 reviews, each accompanied by movie ratings ranging from 0 to 10. The primary objective was to construct a machine learning model capable of categorizing reviews into three sentiment classes: negative, neutral, and positive.

## Data Collection
I collected the dataset using my web scraping code, extracting movie reviews and their corresponding ratings from IMDB.

## Exploratory Data Analysis and Preprocessing
- **Data Cleaning:** After removing null values and eliminating irrelevant characters, punctuation, and stop words, my dataset was reduced to 32,505 rows and 2 columns.
- **Labeling:** I categorized reviews into sentiment classes based on their ratings (1-3 as negative, 4-6 as neutral, 7-10 as positive).
- **Class Imbalance Check:** I observed an imbalance among sentiment classes, particularly with the negative class having the lowest representation. To address this, I could gather more data, synthesize additional data, perform oversampling, or employ an algorithm designed to handle data imbalances, like XGBoost.
- **Tokenization:** Following data cleaning, I tokenized and structured the cleaned data into a formatted DataFrame for further analysis.
- The plot below displays the representation of each class within the dataset.
<img src="./Plots/class imbalance.png"  />



## Model Building
### 1. Blazing Text
- I initially employed BlazingText using AWS for classification but encountered accuracy issues (~47%) due to class imbalance.

### 2. Word2Vec Embedding & XGBoost
Implementing Word2Vec for embedding, I trained an XGBoost model achieving around 63% accuracy for test data and 77% for training data.
<img src="./Plots/learning curve xgboost model.png"  />
<img src="./Plots/confusion matrix xgboost model.png"  />

**However, high dimensionality and slower processing speed were challenges faced.**

- Evaluation metrics for XGBoost model
  
| Accuracy on the training dataset | Accuracy on the test dataset | Precision | Recall |
| -------- | -------- | -------- | -------- |
| 0.77   | 0.63   | 0.62   | 0.63   |


### 3. PCA for Dimensionality Reduction
- To reduce dimensions while maintaining accuracy, I implemented Principal Component Analysis (PCA).
- This significantly improved code efficiency and model building speed without compromising accuracy.
 
- Learning curve for XGBoost model combined with PCA

   <img src="./Plots/learning curve xgboost-pca model.png"  />
- Cost function for XGBoost model combined with PCA

  <img src="./Plots/cost function xgboost pca model.png"  />
- Confusion matrix for XGBoost model combined with PCA

<img src="./Plots/confusion matrix xgboost-pca model.png"  />


- Evaluation metrics for XGBoost-PCA model
  
| Accuracy on the training dataset | Accuracy on the test dataset | Precision | Recall |
| -------- | -------- | -------- | -------- |
| 0.88   | 0.62   | 0.61   | 0.62   |

### 4. Addressing Class Imbalance
- In this model I oversampled the data. However, despite efforts, Although oversampling the minority class (negative sentiment) increased the power of model in predicting class 0, only yielded a maximum accuracy of around 61% and increasing in training time. 
  
- Confusion matrix for XGBoost model trained with oversampled data with PCA

<img src="./Plots/confusion matrix xgboost-oversample model.png"  />

- Evaluation metrics for XGBoost-oversampled model
  
| Accuracy on the training dataset | Accuracy on the test dataset | Precision | Recall |
| -------- | -------- | -------- | -------- |
| 0.83  | 0.61  | 0.62   | 0.61   |

### 5. SVM with RBF Kernel
- Exploring Support Vector Machines (SVM) with an RBF kernel, I achieved similar accuracy (~61%) to XGBoost.
<img src="./Plots/learning curve svm-pca model.png"  />
<img src="./Plots/confusion matrix svm-pca model.png"  />
To determine the best value for the C parameter in SVM, I used a vector of random numbers from 0 to 100, finding 10 as the optimal value.
<img src="./Plots/svm C parameter choose.png"  />

- Evaluation metrics for SVM-PCA model
  
| Accuracy on the training dataset | Accuracy on the test dataset | Precision | Recall |
| -------- | -------- | -------- | -------- |
| 0.80   | 0.60  | 0.59   | 0.60  |

## Conclusion and Insights
Through this project, I made several key findings:
- BlazingText cannot deal with class imbalance
- The lack of change in the accuracy of the XGBoost model after oversampling illustrates that the issue with low accuracy may not solely be due to class imbalance. Consequently, the hypothesis regarding the inadequacy of data became more pronounced after observing the accuracy of this model.
- Consistency in accuracy across different models (XGBoost, SVM) indicated limitations in surpassing the 63% mark.
- Insights gained in handling class imbalances and using PCA for more efficient modeling.
- The best model is XGBoost paired with PCA. It's fast and delivers acceptable accuracy due to the number of data.
