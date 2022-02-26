Case Study 3 – Classification/Clustering of Spam Emails		*Balaji, Ravi, Apurv*

*Balaji Avvaru, Apurv Mittal, Ravi Sivaraman*

*Quantifying The World | SMU | DR. SLATER*

*CASE STUDY 4*

Classification/Clustering of Emails

![](Aspose.Words.a9dcd058-9301-4684-a440-dde662a24651.001.png)![](Aspose.Words.a9dcd058-9301-4684-a440-dde662a24651.002.png)![](Aspose.Words.a9dcd058-9301-4684-a440-dde662a24651.003.png)



# Abstract

The objective of this study is to find if a company will bankrupt or not. The data is heavily skewed towards companies that do not bankrupt as only some of the companies go bankrupt. The risk in creating this model is it will have an accuracy of over 95% but may still fail to predict when the company is going bankrupt as the data doesn’t have a lot of information about companies that went bankrupt. In this study, the objective is to find out with good accuracy and precision when predicting if companies may go under.

# Introduction
The dataset consists of five files, one for each year, on the various attributes (Attr0 to Attr63) which are numerical; and only one class which is an object that contains if the company went under or it. The class feature is a string, but it is changed to 0 (to non-bankrupt) and 1 (bankrupt).

There were 41322 values that were missing or null. These values must be impute

|**Column**|**Null Value**|**Null Value By %**|
| :- | :- | :- |
|**Attr37**|18984|43.736897|
|**Attr21**|5854|13.486925|
|**Attr27**|2764|6.36793|
|**Attr60**|2152|4.957954|
|**Attr45**|2147|4.946435|
|**Attr24**|922|2.124179|
|**Attr28**|812|1.870752|

The table above shows the columns which has the most null values. The columns/features are formulae.

Reference: https://archive.ics.uci.edu/ml/datasets/Polish+companies+bankruptcy+data

The data distribution of data in the missing columns are:


||**Attr37**|**Attr21**|**Attr27**|**Attr60**|**Attr45**|
| :- | :- | :- | :- | :- | :- |
|**count**|24421|37551|4.06E+04|4.13E+04|41258|
|**mean**|105.085363|3.884997|1.11E+03|4.48E+02|14.825016|
|**std**|3058.42983|228.668931|3.50E+04|3.23E+04|2428.23611|
|**min**|-525.52|-1325|-2.59E+05|-1.24E+01|-256230|
|**25%**|1.1423|0.908225|4.50E-02|5.55E+00|0.019168|
|**50%**|3.0963|1.0452|1.08E+00|9.79E+00|0.282825|
|**75%**|11.414|1.2037|5.14E+00|2.02E+01|0.955588|
|**max**|398920|29907|4.21E+06|4.82E+06|366030|

The standard deviation is very high, indicating the mean is not the right middle value. Median is a better middle value for this data. This study applies median for all missing values, as all columns that were missing data show the same characteristics.

The data is very skewed for all the attributes except Attr29 which is normal.

![Chart

Description automatically generated](Aspose.Words.a9dcd058-9301-4684-a440-dde662a24651.004.png)

*Figure 1-Distribution of values in various attributes*

![A picture containing text, light

Description automatically generated](Aspose.Words.a9dcd058-9301-4684-a440-dde662a24651.005.png)

*Figure 2-Colliniarity heatmap of Attributes*

*Data shows there are lot of collinearity, as this is expected, many of the features are a combination of a few variables (mathematical formulae). It is not surprising they are correlated. This study doesn’t drop any columns and takes all of them for generating model.*


### Target
Target is a binary classification of whether the company went bankrupt or not. Note that, most companies don’t go bankrupt, so the data is heavily skewed.


|<p>![](Aspose.Words.a9dcd058-9301-4684-a440-dde662a24651.006.png)</p><p></p>|<p>![](Aspose.Words.a9dcd058-9301-4684-a440-dde662a24651.007.png) ![](Aspose.Words.a9dcd058-9301-4684-a440-dde662a24651.008.png)</p><p></p><p></p>|
| :- | :- |
# 2. Methods

## Classification Models

### Random Forest Classification
Random forest is an ensemble tree-based learning algorithm where it combines more than one algorithm of the same or different kinds for classifying objects. The Random Forest Classifier is a set of decision trees from a randomly selected subset of the training set. It aggregates the votes from different decision trees to decide the final class of the test object.

Parameters:

\- n\_estimators: number of trees in the forest

\- max\_depth: max number of levels in each decision tree

\- criterion: The function to measure the quality of a split. Supported criteria are “gini” for the Gini impurity and “entropy” for the information gain. Note: this parameter is tree-specific

\- min\_samples\_split = min number of data points placed in a node before the node is split

\- min\_samples\_leaf = min number of data points allowed in a leaf node

\- class\_weight: The “balanced” mode uses the values of y to automatically adjust weights inversely proportional to class frequencies in the input data as 

1. *n\_samples / (n\_classes \* np.bincount(y))*



|![](Aspose.Words.a9dcd058-9301-4684-a440-dde662a24651.009.png)|![](Aspose.Words.a9dcd058-9301-4684-a440-dde662a24651.010.png)|
| :- | :- |


![Chart

Description automatically generated](Aspose.Words.a9dcd058-9301-4684-a440-dde662a24651.011.png)

This study compares two models, Random Forest Classification and XGBoost. Random Forest is the basic unsupervised method to classify using Entropy/Gini. In theory, Random Forest gives a benchmark upon which any sufficient advanced algorithm must beat. In general, any algorithm that is using deep learning principles must have a better outcome than Random Forest. 


# 3. Results

Naïve-Bayes algorithm is run with Grid search with several parameters, to find the optimal results. 



|**Mean**|**Std-dev**|**Alpha**|**Fit Prior**|
| :- | :- | :- | :- |
|**0.985567**|-0.002797|0.0001|TRUE|
|**0.986957**|-0.002473|0.0001|FALSE|
|**0.98717**|-0.002339|0.001|TRUE|
|**0.988774**|-0.002253|0.001|FALSE|
|**0.987064**|-0.002159|0.01|TRUE|
|**0.989202**|-0.002763|0.01|FALSE|
|**0.980862**|-0.00194|0.1|TRUE|
|**0.983642**|-0.002909|0.1|FALSE|
|**0.837806**|-0.008439|1|TRUE|
|**0.882925**|-0.007082|1|FALSE|
|**0.743505**|-0.000318|10|TRUE|
|**0.747675**|-0.003525|10|FALSE|
|**0.743505**|-0.000318|100|TRUE|
|**0.744039**|-0.000549|100|FALSE|
|**0.743505**|-0.000318|1000|TRUE|
*Table 3-NB Classifier Grid Search Results (Green highest accuracy)*



###

|Best Accuracy with Grid Search: 0.989|
| :- |

### Training data Metrics

|**Metrics**|**Value**|
| :- | :- |
|**average accuracy** |0.993|
|**average precision** |0.997|
|**average recall**    |0.977|



### Test data Metrics

|**Metrics**|**Value**|
| :- | :- |
|**average accuracy**  |0.989|
|**average precision** |0.990|
|**average recall**   |0.968|



### Classification report


||**Precision**|**Recall**|**F1-Score**|**Support**|
| :- | :- | :- | :- | :- |
|**1 (Spam)**|0.99|0.97|0.98|2399|
|**0 (Not Spam)**|0.99|1.00|0.99|6954|
|**Accuracy**|||0.99|9353|
|**Macro avg**|0.99|0.98|0.99|9353|
|**Weighted avg**|0.99|0.99|0.99|9353|

### ROC Curve
![Chart, line chart

Description automatically generated](Aspose.Words.a9dcd058-9301-4684-a440-dde662a24651.012.png)

*Figure 3:ROC Curve (True Positive vs False Positive)*

The ROC curve for the NB classifier showed a mean area under the curve AUC of 1.00.

The accuracy, precision, and f-score are all very high and close to 1.00. The ROC curve also indicates there are no false positives compared to the true positive rate. The area under the curve indicates the results cover the entire dataset.


# Conclusion


|**Feature Names**|**Coef Weights**|
| :- | :- |
|**Attr27**|0.093812|
|**Attr24**|0.060054|
|**Attr46**|0.040855|
|**Attr34**|0.040664|
|**Attr6**|0.030436|
|**Attr39**|0.029122|
|**Attr26**|0.028551|
|**Attr16**|0.025875|
|**Attr35**|0.023759|

*Figure 4-Feature Importance based on co-efficient*


||
| :- |
|<p>![Chart, funnel chart

Description automatically generated](Aspose.Words.a9dcd058-9301-4684-a440-dde662a24651.013.png)</p><p>*Figure 5-Feature Importance of top 10 Attributes*</p>|

The above table displays the features with their coefficient levels. These are the top 10 coefficients after the L2 penalty. 

This model is recommended to use as it produces higher accuracy and precision (with a high f-score).
# Appendix – Code

9

