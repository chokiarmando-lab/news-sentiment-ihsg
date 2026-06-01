# News Sentiment Analysis as IHSG Market Signal Using IndoBERT

## Overview
This project analyzes whether news sentiment from Indonesian media (Kompas & Tempo) correlates with IHSG (Jakarta Composite Index) stock market movement during Prabowo's administration using IndoBERT-based NLP.

## Key Findings
- News sentiment shows a statistically significant negative correlation with IHSG (r=-0.1195, p=0.0196)
- The effect strengthens with a 7-day lag (r=-0.1545, p=0.0027), suggesting delayed market reaction to media sentiment
- Negative sentiment does not necessarily lead to IHSG decline — indicating Indonesian market is driven by factors beyond domestic media coverage
- Program "Makan Bergizi Gratis" launch (Jan 7, 2025) generated the most positive coverage, captured accurately by the model

## Dataset
| Source | Articles | Period |
|--------|----------|--------|
| Kompas.com | 4,516 | Jan 2026 – Jun 2026 |
| Tempo.co | 5,553 | Oct 2024 – Jun 2026 |
| **Total** | **10,069** | **Oct 2024 – Jun 2026** |

## Tech Stack
- **Scraping**: Selenium, BeautifulSoup
- **NLP Model**: IndoBERT (w11wo/indonesian-roberta-base-sentiment-classifier)
- **Data Processing**: Pandas, NumPy
- **Analysis**: SciPy, Matplotlib, Seaborn
- **IHSG Data**: yFinance

## Project Structure
news-sentiment-ihsg/
├── data/
│   ├── raw/          # scraped articles per source
│   ├── processed/    # cleaned & sentiment-labeled data
│   └── ihsg/         # IHSG price data
├── notebooks/
│   ├── 01_scraping.ipynb
│   ├── 02_preprocessing.ipynb
│   ├── 03_sentiment_indobert.ipynb
│   ├── 04_ihsg_data.ipynb
│   └── 05_analysis_visualization.ipynb
├── src/
│   ├── scraper.py
│   ├── preprocessor.py
│   └── sentiment.py
├── outputs/figures/  # saved visualizations
└── requirements.txt

## Pipeline
Scraping (Selenium)
↓
Preprocessing & Cleaning
↓
Sentiment Analysis (IndoBERT)
↓
IHSG Data Collection (yFinance)
↓
Correlation & Lag Analysis
↓
Visualization

## Results
| Analysis | Result |
|----------|--------|
| Pearson Correlation | r=-0.1195, p=0.0196 |
| Lag 1 day | r=-0.1310, p=0.0106 |
| Lag 3 days | r=-0.1178, p=0.0220 |
| Lag 7 days | r=-0.1545, p=0.0027 |

## Limitations
- Kompas data only available from January 2026 due to pagination constraints
- Majority of news titles classified as neutral (90%) — inherent characteristic of formal news writing
- Analysis based on headlines only, not full article content

## Future Work
- Scrape full article body for richer sentiment signal
- Include additional media sources (CNN Indonesia, Detik)
- Apply Granger causality test for stronger causal inference
- Extend analysis to individual stocks (LQ45 components)