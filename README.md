# Practicum-MSDS692
Practicum Project Details
This notebook focuses on analyzing and matching transactions from two datasets, Athena and Wells Fargo. Here's a breakdown of the key steps and techniques used:
1. Data Loading and Preprocessing
Loaded transaction data from "Athena.csv" and "Wells_Fargo.csv" into pandas DataFrames.
Converted date columns to datetime format.
Cleaned the Amount column by removing currency symbols and commas.
Filtered Athena data to include only 'Credit Card' transactions.
Removed unnecessary rows and columns.
2. Rule-Based Matching
Implemented a custom_match function to identify specific transaction patterns (e.g., matching "Merchant" and "American" keywords in Wells Fargo transactions to Athena transactions).
Used fuzzy matching techniques (e.g., fuzz.WRatio) to compare transaction descriptions and amounts, allowing for slight variations.
Defined a compare_transactions_with_fuzzy_matching function to handle different matching scenarios (exact match, two-transaction match, fuzzy match).
Applied these matching functions to identify potential matches between the datasets.
3. Machine Learning (Random Forest)
Prepared the data for a machine learning model by extracting relevant features (Amount, Description) and creating a binary Match label based on the rule-based matching results.
Used TF-IDF vectorization to convert transaction descriptions into numerical features.
Scaled numerical features using StandardScaler.
Split the data into training, validation, and test sets.
Trained a random forest classifier to predict matches, using GridSearchCV to tune hyperparameters.
Evaluated the model's performance on the validation set.
Created a predict_match function to apply the trained model to new transactions.
4. K-means Clustering
Filtered Athena data for 'Credit Card' transactions.
Prepared data for clustering by selecting Amount and date features, and applying TF-IDF vectorization to transaction descriptions.
Scaled numerical features using StandardScaler.
Applied K-means clustering with k = 5 to group similar transactions.
Added cluster labels to the DataFrames.
5. Visualization and Analysis
Created various visualizations to analyze the results:
Bar chart of matching results (Match, No Match, etc.).
Table of matched transactions.
Scatter plot of cluster distribution.
Bar chart of cluster sizes.
Box plots of transaction amount distribution by cluster.
Calculated cluster statistics (mean, standard deviation, etc.) for both datasets.
Compared cluster statistics between Athena and Wells Fargo.
Identified and printed outliers within each cluster.
Overall, this notebook demonstrates a comprehensive approach to transaction matching, combining rule-based methods, machine learning, and clustering analysis to identify and understand patterns in financial data.
