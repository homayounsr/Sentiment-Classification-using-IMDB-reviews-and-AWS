# Sentiment Analysis of IMDB Movie Reviews

## Introduction
The Sentiment Analysis project aimed to classify IMDB movie reviews based on their sentiment. The dataset comprised 36,000+ reviews along with movie ratings ranging from 0 to 10. The primary objective was to develop a machine learning model capable of categorizing reviews into three classes: negative, neutral, and positive sentiments.

## Data Collection
The dataset was collected using my web scraping code that retrieved movie reviews and their associated ratings from IMDB.

## Exploratory Data Analysis and Preprocessing
- **Data Cleaning:** Removed null values and irrelevant characters, handled punctuation, and eliminated stop words. The size of data after removing null values were 32505 rows and 2 columns
- **Labeling:** Categorized reviews into sentiment classes based on their ratings (1-3 as negative, 4-6 as neutral, 7-10 as positive).
- **Class Imbalance Check:** Identified an imbalance among sentiment classes, with the negative class having the lowest representation.
- ![Alt text](plots/class imbalance.png)
- **Tokenization:** Processed the cleaned data and organized it into a structured DataFrame for further analysis.

## Model Building
### 1. Blazing Text
- Utilized Blazing Text for initial classification.
- Encountered challenges due to class imbalance, resulting in an accuracy of approximately 47%.

### 2. Word2Vec Embedding & XGBoost
- Employed Word2Vec for embedding and trained an XGBoost model for classification.
- Experienced a notable increase in accuracy (~23%) compared to Blazing Text, achieving around 62% accuracy.
- However, faced challenges related to high dimensionality and slower processing speed.

### 3. PCA for Dimensionality Reduction
- Implemented Principal Component Analysis (PCA) to reduce dimensions while maintaining accuracy.
- Significantly improved code efficiency and model building speed without compromising accuracy.

### 4. Addressing Class Imbalance
- Attempted to enhance accuracy by oversampling the minority class (negative sentiment).
- Despite efforts, the maximum accuracy plateaued around 63%.

### 5. SVM with RBF Kernel
- Explored Support Vector Machines (SVM) using an RBF kernel as an alternative model.
- Achieved similar accuracy results (~62%) to XGBoost, reaffirming the consistency of accuracy across models.

## Conclusion and Insights
The project highlighted several crucial findings:
- Maximum accuracy plateaued at around 63% due to inherent challenges like class imbalance.
- Consistent accuracy levels observed across different models (XGBoost, SVM) suggested limitations in surpassing the 63% mark.
- Insights gained in handling class imbalances and managing high dimensions using PCA for more efficient modeling.
