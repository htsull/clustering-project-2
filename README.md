# Summary

In this report, we are approching two topics and we divided the whole document in two sections.

For the two sections we perform the data processing with these same general steps :
- We load and clean the dataset
    - We verified and remove all the rows with missing values and outliers because that can introduce some noise in the data and hurt the performance of the models.
    - We remove all duplicated rows in the dataset.

### **Section 1**

The problem we are approching in this section is the unbalanced dataset case (`Paris Housing`). Our goal is to analyze the impacts of the unbalanced dataset on the models performance and find the best way to evaluate them. So to do this we proceed as the following :
- We perform several models on the dataset : `Logistic Regression (logreg)`, `k-Nearest Neighbors (kNN)`, `Linear Discriminant Analysis (LDA)`, S`upport Vector Machine (SVM)` and use the accuracy and AUC metrics and the confusion matix to evaluate them.
- We perfoorm an undersampling using the `RandomUnderSampler()` function from the `imblearn` package to balance the distribution of the target `(category)`.
- We perform the same models another time, tuned them  and evaluate the using the same metrics as before.

At the end, we found out the models `(logreg, kNN, LDA, SVM)` are severely affected by the data that are unbalanced `(basic : 87%, luxury : 13%)`. We've seen that the `LDA` and `logreg` perform singnificantly better after the undersampling. The accuracy and the AUC metrics and the confusion matrices for these two models are proof that this method works. We can synthetize this section as :
- There is a high accuracy score for all the models before the undersampling (`KNN` : 85.65%, `logreg`: 87.30%, `SVM`: 87.30%, `LDA`: 87.50%) and when we look at the AUC scores and confusion matrices we see that only the `LDA` have a real prediction power `(AUC = 0.95)`. As for the other ones, their AUC scores are gravitating round 0.50, meaning that they have hardly some power to predict the right classes. The only reason we have these high accuracy scores is because the data is unbalanced at this point. So the models generaly have a good accuracy in predicting the majority class and can hardly have a good classification on the minority class.
- After the undersampling, we tuned the models and we have seen that there is a significant drop in the accuracies in two of the models (`logreg` : 97.10%, `LDA` : 91.44%, `KNN` : 52.17%, `SVM` : 49.67%). We can see also that the `logreg` model now have a better performance than all the others and have gain a real power of prediction `(AUC = 1)`.  One of the reasons of this is because the logistic regression is a great tool to use when you have binary classifiaction.

An interesting case that we have not explored and considered as a limit in this report is the difference between the (`logreg`, `LDA`) and (`kNN`, `SVM`) models that makes them perform poorly on the dataset. An explaination for this difference is a case to explore in perpective to be more accurate in the understanding of these algorithms.

### **Section 2**
In this section, we perform a clustering task on the `covid` dataset. We use k-Means adn GMM algorithms to find the best way to represent the clusters and proceeded as the following : 
- We use two methods in k-Means clustering (`elbow` and `silouhette`)
    - Elbow method suggests that we chose two clusters  whereas the silouette suggests two or three, so we chose to go with the 3 provided by the silouette because the graphic representation is better and we can see with the silouhette metric that we have overlappng clusters.
- We we the GMM and it specifies that we chose 3 clusters. That confirms the three clusters we decided to go in the k-Means clustering task. 

 
