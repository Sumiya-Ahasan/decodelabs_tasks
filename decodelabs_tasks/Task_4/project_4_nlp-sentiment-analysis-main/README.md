# NLP & Sentiment Analysis

## DecodeLabs Data Science Project 4

This project implements a Natural Language Processing (NLP) pipeline
for classifying movie reviews as Positive or Negative.

## Objective

The objective is to process unstructured text, convert it into
numerical features using TF-IDF, and train a machine learning
classifier for binary sentiment classification.

## Dataset

The project uses the IMDb Large Movie Review Dataset.

The dataset contains movie reviews with two sentiment classes:

- 0 = Negative
- 1 = Positive

Separate training and testing datasets are used.

## NLP Pipeline

Raw Review
↓
HTML Removal
↓
Lowercase Conversion
↓
Punctuation Removal
↓
Tokenization
↓
Stop-word Removal
↓
Lemmatization
↓
TF-IDF
↓
Linear SVM
↓
Positive / Negative Prediction

## Technologies

- Python
- Pandas
- NumPy
- NLTK
- Scikit-learn
- Matplotlib
- Seaborn
- Joblib
- Google Colab

## NLP Techniques

### Tokenization

Tokenization divides text into individual words or tokens.

### Stop-word Removal

Common words with limited usefulness for classification are removed,
while important negation words are preserved.

### Lemmatization

Lemmatization converts words into their base or dictionary form.

## TF-IDF

TF-IDF converts textual documents into numerical feature vectors
that can be processed by machine learning algorithms.

## Machine Learning Model

A Linear Support Vector Machine (SVM) is used for binary sentiment
classification.

## Evaluation

The model is evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- Confusion Matrix

## Repository Structure

nlp-sentiment-analysis/
│
├── README.md
├── requirements.txt
├── .gitignore
├── notebooks/
├── models/
└── images/

## How to Run

1. Open the notebook in Google Colab.
2. Install the required libraries.
3. Load the IMDb dataset.
4. Perform text preprocessing.
5. Apply TF-IDF vectorization.
6. Train the Linear SVM classifier.
7. Evaluate the model.
8. Test new reviews.

## Conclusion

This project demonstrates a complete NLP sentiment analysis workflow,
from processing unstructured human language to numerical
representation using TF-IDF and sentiment classification using
Linear SVM.
