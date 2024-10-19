[Deployment Link](https://huggingface.co/spaces/gustana/Credit-Score-Analysis)  
[Slides Link](https://www.canva.com/design/DAGTztbp2So/d0kVqNKiaLM9BEk19jkn_w/view?utm_content=DAGTztbp2So&utm_campaign=designshare&utm_medium=link&utm_source=editor)

# Background Problem
- **Credit score is a metric used to determine credit worthiness of a customer**. In other words, this score reveals how reliable a customer is in their ability to pay off their debt.
- For a banking business, one of the key benefits of assessing its customers' credit scores is reducing the risk of non-performing loans (NPLs), thereby lowering overall financial risk.

# Objective
- Creating a classification model to predict customer’s credit score based on their charactheristics.
- The model should be able to achieve minimum precision of 90% using the following critherias:
    - Positive class: good credit score
    - Negative class: standard or bad credit score
    - FN: customers with good credit scores classified as bad or standard credit scores
    - FP: customers with bad or standard credit scores classified as good credit scores

# Modeling
## Cross Validation
| ML Algorithm       | Precision        ||
| :----------------- | :------ | :------ |
|                    | Mean    | Std     |
| KNN                | 76%     | 0       |
| SVC                | 72%     | 0       |
| Decision Tree      | 78%     | 1%      |
| **Random Forest**  | **85%** | **1%**  |
| XGBoost Classifier | 84%     | 1%      |

> Based on Cross Validation, the best model for this dataset is Random Forest with mean of precission 85%

## Evaluation
- Precision on Train set: 100%
- Precision on Test set: 64%

- This model is overfitted, Thus it doesn't reliable for classifying credit score
> To improve the model, I will tune the model in the next section using Random Search

## Hyperparameter Tuning
| Hyperparameter | Value   |
| :------------- | :------ |
| random_state   | 9       |
| n_estimators   | 80      |
| max_depth      | 5       |
| criterion      | entropy |

## Evaluation
- Precision on Train set: 91%
- Precision on Test set: 74%

>Trough hyperparameter tunning, the model's overfitting were reduced quite significantly.   
But, it still overfitted

# Conclusion
<ul>
    <li><b>Customers with poor credit score have slightly higher number of credit card on average.</b></li>
    <li>Outstanding Debt, Delay from Due Date, and Credit Card Age are top 3 variables with a high correlation to Credit Score.</li>
    <li>There are 29% customers with poor credit score.</li>
</ul>

<ul>
    <li>The Model is highly overfitted, thus it’s not reliable for the task</li>
    <li>Generalization can be used to improve it’s performance</li>
    <li>Improving the quality of the dataset can also greatly improve the model's performance</li>
</ul>