# Using Sentiment Dictionaries on Customer Reviews Dataset

## About the Project

This project explores **sentiment dictionaries** applied to a customer review dataset titled *“Women’s E-commerce Clothing Review.”*  
The analysis is divided into three main parts:

1. **Dictionary-based Sentiment Analysis**  
   The first section applies the built-in Quanteda dictionary **“DictionaryGI”** to predict the number of negative and positive terms in each text, represented in a **Document-Term Matrix (DTM)**.  
   The model is further contextualised by incorporating text length, which refines the interpretation of sentiment predictions.  
   To make results more accessible, three types of **universal sentiment scores** were developed to show whether a document leans more positive or negative.

2. **Improving Dictionary Classification**  
   The second part examines the accuracy of dictionary-based classifications by reviewing whether words were correctly assigned to positive or negative sentiment categories.  
   Misclassifications (e.g., neutral words incorrectly classified) were analysed using keyword-in-context inspection to refine the dictionary.

3. **Data Visualisation with `corpustools()`**  
   Finally, the project uses the `corpustools()` library to generate an interactive **text browser** that visualises sentiment within the dataset — highlighting positive words in green and negative words in red.

This project illustrates my confidence and experience in **text analysis**, working with **large, real-world datasets**, and applying **quantitative linguistic methods** in a marketing context.

---

## Retrieving the Data

The dataset used in this analysis is the [**Women’s E-commerce Clothing Review**](https://www.kaggle.com/datasets/nicapotato/womens-ecommerce-clothing-reviews) dataset from Kaggle.  
It is a real-world dataset that has been anonymised by the source.

**Dataset Overview:**
- 23,486 rows  
- 10 feature variables  
- Each row represents a unique customer review

**Variables:**
- **Clothing ID:** Integer categorical variable identifying the reviewed product.  
- **Age:** Reviewer’s age.  
- **Title:** Title of the review.  
- **Review Text:** Body of the review.  
- **Rating:** Product rating from 1 (worst) to 5 (best).  
- **Recommended IND:** Binary indicator for recommendation (1 = recommended, 0 = not).  
- **Positive Feedback Count:** Number of other customers who found the review helpful.  
- **Division Name:** High-level product division.  
- **Department Name:** Product department.  
- **Class Name:** Product class.

---

## Analysis

You can access the full R Markdown file here:  
[**RPubs – Using Sentiment Dictionaries on Customer Reviews Dataset**](https://rpubs.com/annisaptr/customer_reviews)

---

### Part 1: Basic Sentiment Analysis

Using Quanteda’s **“DictionaryGI”**, the dataset was transformed into a **Document-Term Matrix (DTM)** capturing the frequency of positive and negative terms per document.

**Table 1: DTM of Negative and Positive Words**

| Document ID | Frequency of Negative Words | Frequency of Positive Words |
|--------------|-----------------------------|------------------------------|
| 0 | 0 | 2 |
| 1 | 0 | 6 |
| 2 | 2 | 4 |
| 3 | 3 | 6 |
| 4 | 2 | 4 |
| 5 | 1 | 5 |
| 6 | 1 | 2 |
| 7 | 4 | 3 |
| 8 | 1 | 2 |
| 9 | 3 | 4 |

To provide better context, text length was included as a variable. This allows for more nuanced interpretation of sentiment strength.

**Table 2: DTM with Length Column**

| Document ID | Frequency of Negative Words | Frequency of Positive Words | Length |
|--------------|-----------------------------|------------------------------|---------|
| 0 | 0 | 2 | 8 |
| 1 | 0 | 6 | 70 |
| 2 | 2 | 4 | 111 |
| 3 | 3 | 6 | 30 |
| 4 | 2 | 4 | 41 |
| 5 | 1 | 5 | 107 |
| 6 | 1 | 2 | 121 |
| 7 | 4 | 3 | 117 |
| 8 | 1 | 2 | 37 |
| 9 | 3 | 4 | 88 |

Three **universal sentiment metrics** were computed:

```r
# Sentiment 1: Relative difference between positive and negative terms
sentiment1 = (positive - negative) / (positive + negative)

# Sentiment 2: Sentiment adjusted for document length
sentiment2 = (positive - negative) / length

# Subjectivity: Overall emotional content per document
subjectivity = (positive + negative) / length
