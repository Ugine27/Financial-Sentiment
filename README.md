# Financial-Sentiment

This project compares rule-based sentiment analysis using VADER with transformer-based sentiment analysis using FinBERT on financial news text.

## Dataset

The project uses the Financial PhraseBank dataset, specifically the `Sentences_AllAgree` subset.

This subset contains financial news sentences where all annotators agreed on the sentiment label, making it a high-quality ground truth dataset.

Dataset size: 2,264 financial sentences.

## Models Used

## VADER

VADER is a rule-based sentiment analysis model. It uses a predefined dictionary of positive and negative words to calculate sentiment scores.

VADER is simple and fast, but it does not understand financial context deeply.

## FinBERT

FinBERT is a transformer-based model built on BERT and trained for financial text.

It understands context better than VADER. For example:

> The company avoided losses.

VADER may treat this as negative because of the word `losses`, but FinBERT can understand that `avoided losses` is actually positive.

## Results

| Model | Accuracy |
|---|---:|
| VADER | 57.8% |
| FinBERT | 97.2% |

FinBERT performed significantly better than VADER for financial sentiment classification.

## Sentiment vs Stock Market Return

The project also demonstrates how sentiment scores can be compared with next-day Nifty 50 returns.

| Metric | Value |
|---|---:|
| Pearson Correlation | 0.0414 |
| P-value | 0.2607 |

The result shows a very weak positive correlation, but it is not statistically significant because the p-value is greater than 0.05.

## Key Findings

- FinBERT achieved much higher accuracy than VADER.
- VADER struggles with financial context and sentence meaning.
- FinBERT understands word order and context better.
- The sentiment-return correlation was weak and not statistically significant.
- The price correlation section is a demonstration, not a production-level result.

## Limitations

The Financial PhraseBank dataset contains labelled financial sentences, but it does not contain dates.

Because of this, the sentiment-price correlation was simulated by randomly assigning FinBERT sentiment scores to market dates.

In a production system, this should be improved by using dated financial news headlines from a news API and matching them with stock market returns.

## Technologies Used

- Python
- Google Colab
- Pandas
- NumPy
- Matplotlib
- Seaborn
- HuggingFace Transformers
- FinBERT
- VADER Sentiment
- yFinance
- WordCloud
- Scikit-learn

## Project Files

- `financial_sentiment_analysis.ipynb` - main notebook
- `financial_sentiment_results.csv` - final sentiment predictions
- `model_comparison.png` - VADER vs FinBERT confusion matrices
- `financial_sentiment_insights.png` - final visualization dashboard

## Conclusion

FinBERT is more suitable than VADER for financial sentiment analysis because it understands financial language and context. This makes it more reliable for analyzing financial news compared to simple lexicon-based sentiment methods.
