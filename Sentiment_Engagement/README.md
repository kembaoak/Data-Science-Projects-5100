# Sentiment Analysis Project 
## Overview
This project explores how sentiment in social media posts relates to user engagement. Using a dataset of 717 labeled posts, a fine-tuned DistilBERT model was used to classify each post into Positive, Neutral, or Negative sentiment. The project also examines how these sentiment categories correspond to engagement metrics, specifically likes and retweets, to determine whether emotional tone influences how users interact with content.

The analysis follows the structure of the report: cleaning and grouping the data, reducing ambiguity in sentiment labels, preparing text for modeling, fine-tuning a Transformer-based classifier, and evaluating engagement patterns through visualization and statistical methods such as ANOVA and OLS regression. Together, these steps help address whether sentiment can be reliably classified and whether it plays a measurable role in audience engagement.

---

## Purpose
The purpose of this project is to understand two central questions:  
1. Whether a fine-tuned Transformer model can accurately classify the sentiment of social media text into Positive, Neutral, and Negative categories.  
2. Whether sentiment has a statistically significant relationship with engagement metrics such as likes and retweets.

By comparing engagement across sentiment categories, the project aims to provide insight into how emotional tone shapes user interaction and whether certain types of sentiment are associated with higher or lower engagement levels.

---
## Project Structure

```
├── data/                 # Raw and processed datasets
├── code/                 # Contains Jupyter notebooks and Python scripts
├── Presentation Deck/    # Presentation Slides             
├── reports/              # Generated reports and visualizations
├── requirements.txt      # Dependencies utilized in this project
└── README.md             # Project documentation
```
---

## Data
The dataset used in this project was sourced from Kaggle (*Sentiment Analysis: Data Processing, Visualization*). It contains 717 social media posts, each including:

- A sentiment label  
- The text of the post  
- Engagement metrics (likes and retweets)

To ensure consistency, sentiment labels were cleaned, standardized, and grouped into three categories: Positive, Neutral, and Negative. Ambiguous labels were removed, and a total engagement score was created for each post by summing likes and retweets.
Link: https://www.kaggle.com/datasets/kashishparmar02/social-media-sentiments-analysis-dataset

---

## Methodology

The methodology followed in this project consists of four major components: preparing the dataset, building a sentiment classification model, conducting exploratory data analysis, and performing statistical modeling to evaluate how sentiment affects engagement.

### 1. Data Preparation
- Cleaned and standardized column names and sentiment labels  
- Grouped all emotion labels into three categories: Positive, Neutral, and Negative  
- Removed ambiguous sentiment entries that did not clearly fit any category  
- Encoded sentiment categories numerically  
- Created a total engagement variable by summing likes and retweets  
- Split the dataset into training, validation, and test sets using stratified sampling to preserve class proportions  

### 2. Sentiment Classification Model
- Tokenized post text using DistilBERT’s tokenizer with padding and truncation  
- Built a classification model with a three-unit output layer corresponding to sentiment categories  
- Applied class weights to address dataset imbalance  
- Trained the model with the AdamW optimizer (learning rate = 2e-5, batch size = 16)  
- Used early stopping to prevent overfitting  
- Selected the model with the lowest validation loss during training  

### 3. Model Evaluation
- Evaluated performance using accuracy, precision, recall, and F1-scores  
- Generated a confusion matrix to identify classification strengths and weaknesses  
- Used predicted sentiment labels as inputs for engagement analysis  

### 4. Exploratory Data Analysis
- Created visualizations showing the distribution of predicted sentiment categories  
- Summarized engagement statistics (likes and retweets) for each sentiment group  
- Produced grouped bar charts for average engagement across categories  
- Generated density curves to examine the distribution of total engagement within each sentiment group  

### 5. Statistical Modeling
- Conducted a one-way ANOVA to test whether mean engagement differs across sentiment categories  
- Built an OLS regression model using total engagement as the dependent variable  
- Created dummy variables for sentiment: Positive and Negative, with Neutral as the baseline  
- Evaluated coefficients, significance levels, and R² to quantify the relationship between sentiment and engagement  

---

## Results

### Sentiment Distribution
The majority of posts were classified as **Positive**, followed by **Negative**, with **Neutral** being the least frequent category. This distribution reflects a tendency for social media posts in the dataset to contain clear emotional tone rather than neutral expression.

### Sentiment Classifier Performance
The fine-tuned DistilBERT model demonstrated strong performance:
- **Accuracy:** 0.91  
- **Weighted F1-score:** 0.91  

The confusion matrix showed that most misclassifications occurred in the Neutral category, which is expected given its smaller size and higher lexical ambiguity. Positive and Negative classes were classified with higher accuracy.

### Engagement Patterns
Summary statistics and visualizations revealed that:
- Positive posts had the highest totals and averages for both likes and retweets 
- Neutral posts showed moderate engagement  
- Negative posts consistently received the lowest engagement values  

Density curves indicated that engagement for Positive posts extends further into higher ranges, whereas Neutral and Negative posts show more concentrated distributions at lower values.

### Statistical Findings
**One-way ANOVA**  
- Confirmed a significant difference in engagement across the three sentiment categories.

**OLS Regression**  
- The model produced an **R² value of 0.110**, indicating that sentiment explains approximately **11% of engagement variation**.  
- The coefficient for **Positive sentiment** was statistically significant (p < .001), showing that positive posts receive about **13 more interactions** on average compared to neutral posts.  
- The coefficient for **Negative sentiment** was not statistically significant, indicating no meaningful difference from neutral posts.

### Overall Conclusion
The results indicate that **positive emotional tone is strongly associated with higher engagement**, while negative sentiment does not reliably increase or decrease interactions. Although sentiment plays a measurable role, most engagement behavior is influenced by factors outside the scope of this model.

---

## Authors

- Jimmy Nam - @Jimmynam0103
- Edwin Okwor - @kembaoak
- Anushka Naidu Maddisetty @anushkanaidu

---

## License

This project is licensed under the MIT License - see the [LICENSE](https://github.com/Jimmynam0103/Hashtag_Engagement/blob/main/License) file for details.

---

## Acknowledgements

This project was completed as part of the coursework for Seattle University’s DATA 5100: Foundations of Data Science. We would like to acknowledge the guidance provided throughout the course, as well as the collaborative support from peers during the development and refinement of this analysis.

**Tools and Libraries Used**
Data Handling & Preprocessing
- Pandas  
- NumPy

Visualization
- Matplotlib  
- Seaborn

Machine Learning/Deep Learning
- HuggingFace Transformers
- PyTorch

Model Evaluation
- Scikit-learn(sklearn)

Statistical Analysis
- Statsmodels  


We also acknowledge the open-source community for providing the tools and frameworks that made this project reproducible. The insights and feedback received during the course were valuable in shaping both the analytical approach and interpretation of the results.

---

## References/Inspiration

These notebooks and projects helped guide parts of our workflow, especially in data preprocessing, visualization ideas, and overall project structure:

- Rafael R. Car — Sentiment Analysis: Data Processing & Visualization
  - https://www.kaggle.com/code/rafaelrcar/sentiment-analysis-data-processing-visualization

- Mohsin Sial — Sentiment Analysis by NLP
  - https://www.kaggle.com/code/mohsinsial/sentiment-analysis-by-nlp

---
