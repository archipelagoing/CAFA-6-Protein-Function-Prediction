# CAFA-6-Protein-Function-Prediction
-------
## **Executive Summary**

This solution employs a **hierarchical multilabel classification** framework to predict protein functions from amino acid sequences. The model integrates learned sequence representations with engineered biological features to generate accurate **Gene Ontology (GO) annotations** across **Molecular Function, Biological Process,** and **Cellular Component** categories. Performance was evaluated on a held-out validation set using CAFA-appropriate metrics.

The final model achieved a strong **validation accuracy of 93.27%**, providing a reliable tool for targeted marketing and inventory management.

-----
## **1. Problem Statement**

The goal of this project is to build a machine learning model capable of predicting the biological function of a protein from its amino acid sequence. Proteins are fundamental biological molecules whose functions govern most cellular processes, yet many proteins remain poorly characterized. By learning patterns directly from sequence data, this model seeks to assist in annotating protein functions at scale, reducing reliance on costly laboratory experiments.

The primary challenges include learning meaningful representations of protein sequences, handling a large and imbalanced set of functional classes, and bridging the gap between computational modeling and biological interpretation.

For me, the main challenge was learning a bit more about molecular biology on the fly, as I have no previous experience with it. 

Proteins are large molecules that are responsible for many activities in our cells, tissues, organs, and bodies and they also play a central role in the structure and function of cells. Proteins are composed of 20 types of smaller molecules known as amino acids, which are ordered in a long chain known as the protein amino acid sequence. Each protein has its own sequence that determines its structure and its function. 

---
## **2. Data  Preprocessing & Advanced Feature Engineering**

-   **Data Source:** E-commerce dataset containing over **33,000 records** of customer interactions, product details, and purchasing outcomes.
    
-   **Data Cleaning:** Initial preprocessing involved cleaning and handling missing values in key columns like `ratings` and `no_of_ratings` (filling with the **median**).
    
-   **Currency Standardization:** To ensure consistent pricing data, all local currency values were converted to a uniform **USD format** using external conversion rates.

---- 

The model's strong performance was driven by creating three high-value, predictive features from the raw data:

**Feature** | **Description** | **Technical Rationale**

**`discount_percent`**

- The relative percentage saved from the actual price.

- Directly captures the attractiveness of the deal.

**`discount_amount`**

- The absolute dollar amount saved.

- Captures the tangible cost reduction, regardless of the original price.

**`weighted_rating`**

- A composite score to quantify perceived product quality and social proof.

- Engineered using the formula $X + A Y^2$ (where $X$ is `ratings` and $Y$ is `no_of_ratings`) to exponentially prioritize products with higher rating volumes.

- Missing values in critical columns (ratings, no_of_ratings) were imputed using median values.

-  **Currency Standardization:** All local prices were converted to USD using external exchange rates for consistency in pricing data.
