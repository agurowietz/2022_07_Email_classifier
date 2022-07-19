# 2022_07_Email_classifier

The aim was to build a binary classifier which is able to identify spam emails to practice a basic NLP text processing work flow.

## EDA & Feature Engineering
The dataset contains the text of emails and spam emails. From this the additional features word, sentence, punctuation and currency symbol count as well as average word length and sentence length were engineered. Due to their varying dimensions, those features were normalized. Punctuation, sentence and word count showed multicollinearity but were kept as features for now nonetheless. Then stopwords and punctuation was removed from the text and the remaining text was tokenized, stemmed and vectorized using a simple Bow approach. 

## Model Building & Tuning
Due to the imbalanced database, the train test split was stratified to maintain the initial target distribution in the test data. The training data was then undersampled according to the underrepresentated category (Spam emails). The baseline performance of various classification algorithm was screened by cross fold validation on the training data. The three best performing models were multinomial naive bayes, random forest and logistic regression. The latter two were optimized using random searched and grid searched hyperparameters. The performance of the three classifiers on the test data was validated by confusion matrices and ROC Curve whereby the MultinomialNB classifier showed the best results. Finally, the three models were ensembled using a soft voting classifier, which was tested on the test data but didn't achieve better results as the multinomial naive bayes classifier.
