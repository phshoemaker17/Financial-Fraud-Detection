# Financial-Fraud-Detection
See below for the description of this assignment.

You work at a financial services company that has seen their data intake grow rapidly in recent years. As a result, much of the data processing, wrangling, and analysis that had been using R and Python (pandas) is difficult to do now that datasets are too large to fit on local computers. You and your team have been asked to provide a report on how to accommodate big data and what tools are available to use to process, analyze, and model large amounts of data and use big data processing to process and model a dataset on suspicious activity using transactions data.

Dataset: Bank Transactions Download Bank Transactions

Part 1
The first part of the presentation should address include the following and be comprehensible for both technical and non-technical audiences.

How can the organization process big data?
What tools can be used and how can analysts work with them in familiar programming languages?&
Given the organization's familiarity with pandas and Python, what differences are there between pandas and PySpark
What are the main components involved with processing big data? Where does the computational power for processing big data come from?
The presentation should include specific references to big data tools, the data structures used, and specific references to programming (languages, syntax, techniques) that the organization should be aware of in the adoption of big data processing tools.

Part 2
The second part of the presentation will use a Databricks notebook where you and your team carry out a big data analysis using Spark via PySpark and the bank_transactions.csv dataset. You will carry out the following steps in a Databricks notebook and briefly explain each step that includes code.

Upload the dataset to your Databricks filestore
Read in the data and call it df
Check the schema of the dataset
Create a new column called destination_diff by subtracting oldbalanceDest from newbalanceDest
What is the mean amount per transaction by type? Execute this code without adding .show() to the line of code.
What is the mean amount per transaction by type? Execute this code with .show() on the end of the line of code. How does the output in #5 and #6 differ? Why does it differ? What does this show us about Spark?
Make a SQL table from your df and call it df_table
Explain how to run a different programming language in a given cell.
Write a SQL query to count the number of transaction by type and return the result in descending order. Generate a bar plot of the results using Databricks’ plot options. Explain the results.
Create a new column that labels the transaction as suspicious. The new column should be called label and take the value of 1 if:
The oldbalanceOrg is less than 54000 and the type of transaction is a transfer and the new balance is less than or equal to 105, or
The oldbalanceOrg is greater than 56900 and he newbalanceOrig is less than or equal to 12, or
The oldbalanceOrg is greater than 56900 and the newbalanceOrig is greater than 12 and the amount is greater than 1160000,
Otherwise, the value should be 0.
Calculate the percentage of transactions labeled suspicious (“label”) out of all transactions
Import StringIndexer, OneHotEncoder, and VectorAssembler from pyspark. Explain what each of these PySpark processing tools is used for.
Convert the column “type” to a numeric column of indices called typeIdx
Encode “typeIdx” to create a binary representation of it called “type_bins”
The “type_bins” feature is stored as a SparseVector. What is a SparseVector and why does Spark use it to store data?
Assemble the columns into a single vector column with the following input columns: "type_bins","amount","oldbalanceOrg", "newbalanceOrig", "oldbalanceDest", "newbalanceDest", "destination_diff". Call the output column “features” and select “features” and “label.”
Split the data into train and test sets with 30% held out for testing.
Import the DecisionTreeClassifier from pyspark.
Instantiate the model
Fit the model to training data
Make predictions using the test data
Evaluate the model using the BinaryClassificationEvaluator by using the predictions to get the Area under the ROC and save this number as a variable called dt_auc.
Perform steps 18 through 22 again but use a Random Forest Classifier instead of a Decision Tree. Save the result from the Area under the ROC step as a variable called rf_auc
Perform steps 18 through 22 again but use a Gradient Boosted Tree instead of a Decision Tree. Save the result from the Area under the ROC step as a variable called gb_auc
Print dt_auc, rf_auc, and gb_auc to summarize each models performance and recommend the organization move forward with the best model. Summarize your recommendations and future analysis that would be useful.
