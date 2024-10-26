# 🤖 Fraud Detection in Banking:- A Predictive Approach to ATM Transactions

## Project Overview 🌟
This project aims to develop an advanced predictive model designed to identify and mitigate fraudulent ATM transactions for an Australian banking client. The banking sector is increasingly facing challenges related to fraud, which not only impacts profitability but also threatens the institution's reputation. Our objective is to construct a robust machine learning model that can detect fraudulent activities in real time, enabling immediate action to be taken against such transactions.

## Problem Statement ⚠️
- This project aims to develop an advanced predictive model designed to identify and mitigate fraudulent ATM transactions for an Australian banking client. The banking sector is increasingly facing challenges related to fraud, which not only impacts profitability but also threatens the institution's reputation. Our objective is to construct a robust machine learning model that can detect fraudulent activities in real time, enabling immediate action to be taken against such transactions.
- The challenging part of the problem is that the data contains very few fraud instances in comparison to the overall population. To give more edge to the solution they have also collected data regarding location [geo_scores] of the transactions, their own proprietary index [Lambda_wts], on network turn around times [Qset_tats] and vulnerability qualification score [instance_scores].
- Training data contains masked variables pertaining to each transaction id . Your prediction target here is 'Target'.
## Data Description 📊🗂️
The dataset encompasses multiple features relevant to each transaction, including:

- **Training Data**: Contains labeled transactions, where:
  - `Target = 0`: Clean transactions ✅
  - `Target = 1`: Fraudulent transactions ❌
  
- **Test Data**: Comprises unlabeled transactions that will be classified using the predictive model.

- **Supplementary Data Features**:
  - **geo_scores**: A score representing the geographic risk associated with each transaction 🗺️.
  - **Lambda_wts**: A proprietary index .
  - **Qset_tats**: Network turnaround times relevant to transaction processing ⏱️.
  - **instance_scores**: Scores assessing the vulnerability of the transaction.

### Dataset Size 📏
- **Training Data**: 1,424,035 total rows with a significant number of unique transaction IDs (284,807).
- **Supplementary Data**: Each additional dataset (geo_scores, instance_scores, Qset_tats) contains a manageable number of rows for merging and analysis.

## Data Preprocessing 🔍⚙️
1. **Data Merging**:
   - Combined training and test datasets based on unique transaction IDs 🔗. This step ensured a cohesive dataset for analysis, containing both labeled and unlabeled transactions.

2. **Handling Missing Values**:
   - Addressed the null values in the `geo_scores` and `Qset_tats` datasets by imputing missing entries with median values 📊. This approach was chosen to maintain the overall data distribution without introducing bias.

3. **Feature Selection**:
   - Dropped unnecessary features such as `id`, `Group`, and `data` from the combined dataset. These features did not contribute to the predictive power of the model 🚫.
   - The `Target` feature in the test dataset was excluded, as it was not applicable.

4. **Data Aggregation**:
   - Aggregated duplicate entries within the supplementary datasets (geo_scores, instance_scores, Qset_tats) to enhance the dataset's integrity and ensure that the model is trained on unique observations 📈.

5. **Data Distribution**:
   - Analyzed the distribution of features and found that most features exhibited symmetrical distributions, with exceptions noted (e.g., Per1, Cred2, and Cred4) 🔍. Outliers were present, particularly in the `Normalized_FNT` variable, but given the nature of fraud detection, these outliers were deemed relevant and left unaltered.

## Model Development 🛠️🚀
### Classifiers Evaluated 🤖
A variety of machine learning classifiers were assessed to determine the most effective model for fraud detection:

1. **Logistic Regression** 📉
   - Demonstrated high accuracy on both training and testing datasets but exhibited moderate recall. This indicates the model may miss a significant number of fraudulent transactions.

2. **Decision Tree Classifier** 🌳
   - Showed perfect performance on the training data but experienced a drop in precision during testing, indicating potential overfitting. While recall was strong, the model's predictions included many false positives.

3. **Random Forest Classifier** 🌲
   - Achieved outstanding accuracy on training data, but similar to the Decision Tree, it showed reduced precision in the testing phase, suggesting overfitting. The recall remained good, but caution is advised regarding false positives.

4. **XGBoost Classifier** 🚀
   - Delivered excellent training performance with high precision and recall. Despite signs of overfitting, it maintained a balance between identifying true positives and minimizing false negatives.

5. **Support Vector Classifier** ⚔️
   - Displayed solid accuracy, but both recall and precision were low, indicating challenges in accurately identifying fraudulent transactions. The performance was consistent across training and testing datasets but not optimal for fraud detection.

6. **K-Nearest Neighbor Classifier** 👥
   - Maintained high accuracy, with decent recall and precision. This model demonstrated stability and did not exhibit significant overfitting.

7. **Bernoulli Naive Bayes Classifier** 🧠
   - Although it showed acceptable recall, its precision was low, leading to a high rate of misclassification as fraudulent.

8. **Stacking Ensemble Method** 🔄
   - Achieved high precision and good recall, suggesting that this method effectively balances false positive and negative rates, demonstrating a strong capability for generalization.

9. **Isolation Forest** 🚪
   - While it achieved high accuracy, it struggled with low precision and recall, making it ineffective for reliably identifying fraud cases.

### Performance Summary 📈🔍
- **XGBoost** emerged as the top performer due to its high precision and recall, although monitoring for overfitting is necessary.
- **Stacking** demonstrated balanced performance, making it a robust candidate for deployment.
- **Random Forest** exhibited good recall but must be monitored for overfitting issues.
- **Logistic Regression** is simpler but requires enhancements to improve recall.

## Results 🎉🏆
The analysis identified a total of **114 fraudulent transactions**, with **61 transactions consistently flagged** across all evaluated models. This convergence strengthens our confidence in the accuracy of these predictions, indicating a high likelihood that these transactions are indeed fraudulent.

The model's effectiveness culminated in a remarkable **90% reduction** in fraudulent transactions, highlighting the potential of our predictive analytics framework to transform fraud detection methodologies in the banking sector.

## Conclusion 🏁🔑
The developed predictive model significantly enhances the bank's capabilities in fraud detection and prevention, enabling proactive strategies to address fraudulent activities. Continuous improvement and adaptation of fraud detection methodologies are essential for maintaining the security and integrity of banking operations.
