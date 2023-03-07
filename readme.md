## Predicting Long-Term Mortality: Evidence from Wisconsin Longitudinal Study

### Background:
The current academic literature in predicting mortality has extensively focused on disease and frailty, although social, behavioral, and psychological statuses may herald broad physiological decline. I tested the effectiveness of the machine learning algorithms on the NSHAP sample in Project 1 and learnt the important features predicting mortality. This project will extend the analysis by 1) using a different set of predictors 2) applying some new algorithms in addition to tree-based algorithm 3) using a different dataset.

### Context:
Wisconsin Longitudinal Study (WLS) is a prospective cohort study of graduates of Wisconsin high schools. I use 2004 characteristics as baseline and 2020 disposition status as target.

### Goal:
The goal of this project is to train a binary classifier to predict the mortality of US Adults in modern nationally representative aging surveys. I will also discuss the social and demographic characteristics of the cases whose disposition statuses were either wrongly predicted as death or alive by the algorithms. The findings will serve important purposes for public health practitioners in understanding the risk and protective factors of mortality in the aging process.

### Task:
The task is to train a supervized binary classification model to predict mortality in the next 16 years using the baseline characteristics in 2004.

### Dataset Links:
<a href= https://researchers.wls.wisc.edu/data/survey-data/>WLS Dataset</a>

#### List of features I will be using:
1. Body mass index: HRS: HC139 - weight in pounds (continuous)
2. Hypertension: HRS: HC005 (binary)
3. Diabetes: HRS: HC010 (binary)
4. Self-rated health: HRS: HC001 (ordinal)
5. Arthritis: HRS: HC070 (binary)
6. Smoking: HRS: HC117 (binary)
7. Drunk alcohol: HRS: HC128 (binary)
8. Age at baseline: HRS: HX067_R (ordinal, year of birth)
9. Education: HRS: HB014A (ordinal)
10. Net household assets: HRS: HC134 + HQ331 + HQ376 (continuous)
11. Marital status: HRS: HMARITAL (binary)
12. Sex: HRS: HX060_R (binary)
13. Race: HRS: HB031A (binary)
14. Religion Importance:  HRS: HB053 (ordinal)
15. Children co-residence: HRS: HE012 (binary)
16. Grandchildren: HRS: HE046 (binary)
17. Relatives: HRS: HF174 (ordinal)
18. Volunteer: HRS: HG092 (binary)
19. Friends: HRS: HF176 (ordinal)
20. Functional limitations: HRS: HG001 (binary)

### Conclusion

I have used the WLS dataset to predict mortality in the next 16 years using the baseline characteristics in 2004. I further explored the topic of class inbalance problem originated from project 1, and tried several new models. Different from upsampling and down sampling method tried in p1, I hereby aimed to improve the class inbalance performance by conducting better features. I explored MinMax scalling normalization and polynomial feature expansion. Different from tree models and ensemble method explored in p1, I hereby mainly explored linear models: logistic regression, SVM and fuzzy svm. To better understand the performance, I have also discussed the social and demographic characteristics of the false cases, and made some attempt to explain why models made these mistake.

1. Data processing and exploration: I have converted the feature values to appropriate forms. Then, I drop the samples with missing features. Then, I checked the balance condition of labels and distribution of features. After checking the balance and distribution, I explored the data ahead by displaying their correlation.
2. Pipeline: Feature Processing, Parameter Selection, and Model Training: I selected parameter for tuning basing on the property of models, characteristic of data and knowledge gained from previous step. Then, because I mainly focus on class-imbalance problem and models' ability of distinguishing samples, I mainly choose models with better roc_auc score and balanced f1 score for further analysis. In mortality problem, although deceased samples are significantly less than not deceased in our dataset, I think people with relatively higher deceased possibility need more attention. Therefore, I want to pay more attention on models with more balanced performance and do better on positive samples.
3. Model Evaluation (On Test Set) and Error Analysis: I have evaluated the models on the test set and analyzed the errors of the models. I have also discussed the social and demographic characteristics of the cases whose disposition statuses were either wrongly predicted as death or alive by the algorithms.

Overall the findings will serve important purposes for public health practitioners in understanding the risk and protective factors of mortality in the aging process. When comparing between model performances in accurately predicting mortality, svm with linear kernel has the best overall accuracy, and fuzzy svm with linear membership function has most balanced performance. I think this is mainly because there is significant linear pattern within samples. SVM with linear kernel separate samples by support vector, and has better capability to capture general difference between positive and negative samples. However, it is less efficient on distinguishing vague samples near the boundres. Fuzzy SVM get the hyperplane by calculating membership degree based on training samples. It first optimizes membership significance by methods similar to clustering, and decide testing sample's prediction by weighted voting-like method. This is how the membership function works. It has better performance on positive samples, for it can capture more features despite the number of positive sample it limited. Fuzzy SVM can reach highperformance on small dataset, while need more time to iterate on the same size of data, compared to svm and logistic regression. This enables fuzzy svm to conduct prediction when samples are hard or expensive to get.

Future avenues of research include the following (collaborate with Yiang Li):
1. Comparing and contrasting the differences in the important predictors of mortality between the NSHAP, WLS and HRS datasets.
2. Proposing the best model for predicting mortality in the aging process based on the differences in the important predictors of mortality between the NSHAP, WLS and HRS datasets.
