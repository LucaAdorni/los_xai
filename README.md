# LOS Prediction: Replication Codes

The following repository contains the codes to replicate the results in the paper "Improving hospital healthcare by optimizing length of stay with explainable artificial intelligence : enhancing both performance and interpretability ".

The MIMIC-III database is freely available here : https://mimic.mit.edu/docs/gettingstarted/
The main codes are in the folder notebooks. To fully reproduce the analysis, it is first necessary to setup a local PostgreSQL server containing the MIMIC-III database. For more information, follow the official documentation at the following [link](https://mimic.mit.edu/docs/gettingstarted/).

## Queries

### 0. SETUP MIMIC-III DATASET

After having successfully setup a local PostgreSQL version of the MIMIC-III dataset, follow the instructions in the "queries* folder to run the SQL queries and create the main tables used in the analysis.

## Codes

### 1. all_data_raw.ipynb

Run the following notebook to get the raw tabular data from the previously created tables. 

### 2. data_preparation.ipynb

Merges the tabular data with the clinical notes, keeping only discharge notes and removing any duplicates. 

### 3. data_cleaning.ipynb

Clean and process tabular data. Furtherly merges the data with ICD-9 codes chapters, see [link](https://rdrr.io/cran/icd9/man/icd9Chapters.html) for more information.

### 4. LDA_Text_Vectorization.ipynb

Process the discharge notes by firstly applying Bag of Word Methods (BOW), then generating Latent Dirichlet Allocation topics (LDA) which will be then used in the Mixed model.

### 5. LOS_Tabular.ipynb

Trains an AutoGluon Tabular Predictor model over the tabular-only dataset. Similarly, it trains the same model over the Mixed dataset (combining tabular data with LDA topics).

### 6. LOS_Text_Only.ipynb

Fine-tunes a ClinicalBioBERT model over the discharge notes. Furthermore, computes the LIME weights over the test set to enhance model interpretability.

### additional_analysis/A_descriptive_stats.py

Contains codes to produce a table with summary statistics.