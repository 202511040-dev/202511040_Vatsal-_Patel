Name:Patel Vatsal Sureshbhai

Student ID:202511040

Lab:2 Assignment
GloVe Pretrained Embeddings for Movie Text Prediction


## Objective

This project demonstrates the use of pretrained GloVe word embeddings for:

1. Regression: Predicting movie vote_average  
2. Multi-label Classification: Predicting movie genres  

Additionally, text-based analysis was conducted to interpret frequent and genre-indicative words.

---

## Methods

- Text preprocessing (lowercasing, cleaning, tokenization)
- TF-IDF weighted GloVe document embeddings (100D)
- Neural network regression model
- Multi-label neural classification model (BCEWithLogitsLoss)
- Logistic regression for genre-indicative words

---

## Results Summary

### Regression (Rating Prediction)

| Input Text | RMSE |
|------------|------|
| Overview   | 4.09 |
| Tagline    | 4.47 |


Overview provided the best predictive performance.

---

### Multi-Label Genre Classification

| Input Text | Micro-F1 | Macro-F1 | Hamming Loss |
|------------|----------|----------|--------------|
| Overview   | 0.024   | 0.0131   | 0.0250 |
| Keywords   | 0.0269   | 0.0126   | 0.15479 |

Overview significantly outperformed keywords.

---

## Conclusion

Overview text provides richer semantic information for both regression and genre prediction tasks.

---


