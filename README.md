# CoLA Classifier

This is a research of an appropriate classifier for CoLA dataset from GLUE

## Research

CoLA - dataset from GLUE with unbalanced data. 

There are following aspects considered in this study:
1. **Representation function.** This part is responsible for mapping text features into vector representation. Two options were selected: doc2vec and BERT with attention mask. Doc2vec is selected because this model is an optimal trade-off between effectiveness and computational and/or memory consumption. In contrast with doc2vec BERT model is more advanced model with high performance but it resources-demanding.
2. **Model choice.** Generally, selected models could be divided into two groups: basic classifiers and recurrent classifier. Basic classifiers includes LogisticRegression, XGBClassifier, NearestCentroid, etc., recurrent classifier is a bidirectional LSTM.
3. **Balancing techniques:** undersampling and oversampling by SMOTE. These two techniques are one of the simpliest to apply to evaluate the performance. Undersampling is applied on majority class in order to make it equal to minority class. Oversampling is more advanced technique and includes multiple approaches from the simplest and effective like SMOTE to most relevant generative models to produce new samples.

File ```cola.ipynb``` reflects all experiments and its performance and file ```GLUE classifier.pdf``` provides with short report with analysis.

## Analysis

ColA classification is complicated with data imbalanced, but
despite of this f1-score were achieved up to 0.81.

1. **Representation function.** Based on AUC metric BERT model performed better then Doc2Vec. BERT model is more complex state-of-the-art representation model with better architecture to derive data features therefore it managed learn more data features. Moreover, BERT model is a pretrained model therefore it has better understanding of data distribution because it had learnt more features from other datasets. Doc2Vec was trained on CoLA dataset and could not benefit from previous features learning.
2. **Model choice.** LSTM model was not able to correctly classify different classes. Losses values showed LSTM was overfitted from the early epochs and only learnt to classify all instances as instances belonging to one class. At the same time basic classifiers were able to distinguish one class from another with better AUC values up to 0.62.
3. **Balancing techniques.** AUC metrics indicated there is no significant difference in performance of models with applied o balancing techniques. It emphasizes the idea of data complexity - simple balancing techniques were not able to handle the imbalance by deleting instances of majority classes or detecting and generating features of minority classes within the representation approaches applied in the study.
