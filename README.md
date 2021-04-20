## LIME_Replication

In this project, I tried to build LIME and replicate the findings (figure 2, experiment 1 (section 5.2) & 2 (section 5.3) from the paper. I had a Random explainer as baseline, where explanations are randomly chosen from the instance as comparison for sanity check. 

Components

- Vectorizer

- Explainers
  - LIME
  - RandomExplainer

Classifiers 
  - L1 Logistic Regression
  - L2 Logistic Regression
  - Nearest Neighbors
  - SVM

Experiment_1 ("Section 5.2 - Are explanations faithful to the model?")
Experiment_2 ("Section 5.3 - Should I trust this prediction?")

Procedure for LIME

I first built the bag of words model using sklearn's countVectorizer. Then find nonzeros features from the sparse matrix generated from the vectorizer. I then permuted the nonzeros features of the instance vector randomly to generate 15000 number of samples. Then I got the labels from samples using the specified classifier. Then I calculated the consine distance of those samples and weight it by the distance kernel specified in the paper. Then I used those weights and labels to perform regularization on the features to select the K number of features and fit a localized linear model on weighted distances and labels.

## Replicating Figure 2
The results for figure 2 seems similar with order of the explanations ordered by coefficients slightly off.



# Experiment 1 - Replicating the results from 5.2

# Experiment 2 - Replicating the results from 5.3
    | Books      | DVDS
|      |   LR  |   NN |  SVM  |          LR  |   NN |  SVM  |
|-----:|--------------------:|---------------------:|----------------------------------------:|---------------:|----------------:|
|    Random |                49.4 |                 50.6 |                                    76.6 |           49.4 |            49.4 |
|   60 |                46.2 |                 50.6 |                                    53.2 |           49.4 |            98   |
|  120 |                46.4 |                 50.6 |                                    92   |           52.6 |           100   |
|  250 |                49.4 |                 75.4 |                                    60   |           59.2 |            99.8 |
|  500 |                49.4 |                 50.6 |                                    94   |           88.6 |           100   |
| 1000 |                49.4 |                 60   |                                    97.2 |           58.8 |           100   |
| 2000 |                49   |                 61   |                                   100   |           75   |           100   |
| 4000 |                44.2 |                 81.6 |                                   100   |           97.6 |           100   |


