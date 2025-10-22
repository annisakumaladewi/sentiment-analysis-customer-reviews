# Using Sentiment Dictionaries on Customer Reviews

## Overview

This project explores the application of **sentiment dictionaries** on a real-world dataset titled *“Women’s E-commerce Clothing Review.”*  
Using the **Quanteda** and **corpustools** packages in R, the project demonstrates how dictionary-based sentiment analysis can classify and visualise customer opinions.  

The work is divided into three parts:
1. **Dictionary-based Sentiment Analysis** – using Quanteda’s `DictionaryGI` to predict positive and negative terms.  
2. **Dictionary Refinement** – examining misclassified words (e.g., “just”) and improving sentiment accuracy.  
3. **Visualisation** – applying `corpustools()` to highlight sentiment in text (positive in green, negative in red).

---

## Dataset

Dataset: [Women’s E-commerce Clothing Reviews – Kaggle](https://www.kaggle.com/datasets/nicapotato/womens-ecommerce-clothing-reviews)  
Contains 23,486 rows and 10 variables including `Review Text`, `Rating`, and `Recommended IND`.

---

## Full Report

**Read the full report:** [reports/sentiment_analysis_report.pdf](/Sentiment%20Analysis%20Report.pdf)

**R Markdown (code):** [scripts/sentiment_analysis.Rmd](https://rpubs.com/annisaptr/customer_reviews)

---

## Key Skills Demonstrated
- Text cleaning and tokenisation  
- Dictionary-based sentiment scoring  
- Exploratory text analysis (Quanteda)  
- Contextual evaluation using KWIC  
- Visualisation of sentiment with corpustools  
- Clear documentation and reproducible workflow
