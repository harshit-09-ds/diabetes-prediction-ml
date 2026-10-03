# Model Results

Results below are taken from the project notebook.

## Evaluation

- Accuracy: **0.68**
- ROC-AUC: **0.7282948594**
- Diabetes precision: **0.71**
- Diabetes recall: **0.83**
- Diabetes F1-score: **0.77**

## ROC-AUC

- Train ROC-AUC: **0.7545088588**
- Test ROC-AUC: **0.7282948594**

## Selected XGBoost Configuration

```text
colsample_bytree = 0.8
learning_rate    = 0.05
max_depth        = 3
min_child_weight = 7
n_estimators     = 10000
n_jobs           = -1
subsample        = 0.8
```
