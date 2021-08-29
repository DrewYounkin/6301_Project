# Credit Line Increase Model Card

### Basic Information

* **Person or organization developing model**: Drew Younkin, `drew_younkin@gwu.edu`
* **Model date**: August, 2021
* **Model version**: 1.0
* **License**: MIT
* **Model implementation code**: [DNSC_6301_Project.ipynb](https://colab.research.google.com/drive/1FO125zXmVwuFnpKRe-Z1O_C2nhcAPpDZ#scrollTo=hdV7vATxozMQ)

### Intended Use
* **Primary intended uses**: This model is an *example* probability of default classifier, with an *example* use case for determining eligibility for a credit line increase.
* **Primary intended users**: Students in GWU DNSC 6301 bootcamp.
* **Out-of-scope use cases**: Any use beyond an educational example is out-of-scope.

### Training Data

* Data dictionary: 

| Name | Modeling Role | Measurement Level| Description|
| ---- | ------------- | ---------------- | ---------- |
|**ID**| ID | int | unique row indentifier |
| **LIMIT_BAL** | input | float | amount of previously awarded credit |
| **SEX** | demographic information | int | 1 = male; 2 = female
| **RACE** | demographic information | int | 1 = hispanic; 2 = black; 3 = white; 4 = asian |
| **EDUCATION** | demographic information | int | 1 = graduate school; 2 = university; 3 = high school; 4 = others |
| **MARRIAGE** | demographic information | int | 1 = married; 2 = single; 3 = others |
| **AGE** | demographic information | int | age in years |
| **PAY_0, PAY_2 - PAY_6** | inputs | int | history of past payment; PAY_0 = the repayment status in September, 2005; PAY_2 = the repayment status in August, 2005; ...; PAY_6 = the repayment status in April, 2005. The measurement scale for the repayment status is: -1 = pay duly; 1 = payment delay for one month; 2 = payment delay for two months; ...; 8 = payment delay for eight months; 9 = payment delay for nine months and above |
| **BILL_AMT1 - BILL_AMT6** | inputs | float | amount of bill statement; BILL_AMNT1 = amount of bill statement in September, 2005; BILL_AMT2 = amount of bill statement in August, 2005; ...; BILL_AMT6 = amount of bill statement in April, 2005 |
| **PAY_AMT1 - PAY_AMT6** | inputs | float | amount of previous payment; PAY_AMT1 = amount paid in September, 2005; PAY_AMT2 = amount paid in August, 2005; ...; PAY_AMT6 = amount paid in April, 2005 |
| **DELINQ_NEXT**| target | int | whether a customer's next payment is delinquent (late), 1 = late; 0 = on-time |

* **Source of training data**: GWU Blackboard, email `drew_younkin@gwu.edu` for more information
* **How training data was divided into training and validation data**: 50% training, 25% validation, 25% test
* **Number of rows in training and validation data**:
  * Training rows: 15,000
  * Validation rows: 7,500

### Test Data
* **Source of test data**: GWU Blackboard, email `drew_younkin@gwu.edu` for more information
* **Number of rows in test data**: 7,500
* **State any differences in columns between training and test data**: None

### Model Details
* **Columns used as Inputs in Model**: Limit_Bal, Pay_0, Pay_2 - Pay_6, Bill_AMT1 - Bill_AMT6, Pay_AMT1 - Pay_AMT6
* **Columns used as Target in Model**: DELINQ_NEXT
* **Type of Model**: Decison Tree
* **Software used to Implement Model**: Jupyter Notebook in Google Colab, Scikit Learn
* **Version of Software**: 0.22.2.post1
* **Hyperparameters or other settings of model**: cp_alpha=0.0, class_weight=None, criterion='gini',
                       max_depth=6, max_features=None, max_leaf_nodes=None,
                       min_impurity_decrease=0.0, min_impurity_split=None,
                       min_samples_leaf=1, min_samples_split=2,
                       min_weight_fraction_leaf=0.0, presort='deprecated',
                       random_state=1234, splitter='best

### Quantatitve Analysis
 
* **Metrics used to Evaluate Final Model**: Validation AUC, Test AUC, AIR between White and Hispance, Asian, Black and Female to Male AIR
* **Training AUC**: 0.782
* **Validation AUC**: 0.753
* **Test AUC**: 0.748
* **Hispanic - White AIR**: 0.82
* **Black - White AIR**: 0.85
* **Asian - White AIR**: 1.02
* **Female - Male AIR**: 1.04
#### Histograms for each Column
![image](https://user-images.githubusercontent.com/89538749/131180228-dedb7c43-2917-455f-b751-83476527c730.png)
#### Iteration Plot for First Model
![image](https://user-images.githubusercontent.com/89538749/131180419-8e51442b-11c9-4ce6-b5d0-edadc7954faa.png)
#### Iteration Plot for Final Model Adjusted for Bias
![image](https://user-images.githubusercontent.com/89538749/131180626-9371d767-aaf3-4e50-9826-dd5776fbe36e.png)

### Ethical Considerations

One 
