# KU Data Preprocessing Package

## 1. Repository Structure
```sh
.
├── dataset
│   ├── ecg_mitbih_test.csv
│   └── imputed_data
│       └── ecg_mitbih_test_imputed.csv
├── imputation.py
└── README.md
```

## 2. Preprocessing module
### 2.1 Missing Value (NA) Imputation
#### 2.1.1 Supported Options & Sample Usage
Impute the missing values in a dataset and save the result.
- Simple Imputation with `mean, median, most_frequent, constant` value [[description]](https://scikit-learn.org/stable/modules/generated/sklearn.impute.IterativeImputer.html#sklearn.impute.IterativeImputer)
```Python
# Sample Usage
python imputation.py --data_path='./dataset/ecg_mitbih_test.csv' \
                     --option='simple' \
                     --strategy='mean' \
                     --output_path='./dataset/imputed_data/ecg_mitbih_test_imputed.csv'
```

- KNN Imputation [[description]](https://scikit-learn.org/stable/modules/generated/sklearn.impute.KNNImputer.html)
```Python
# Sample Usage
python imputation.py --data_path='./dataset/ecg_mitbih_test.csv' \
                     --option='knn' \
                     --n_neighbors=5 \
                     --output_path='./dataset/imputed_data/ecg_mitbih_test_imputed.csv'
```
- MICE Imputation [[description]](https://scikit-learn.org/stable/modules/generated/sklearn.impute.IterativeImputer.html#sklearn-impute-iterativeimputer)
```Python
# Sample Usage
python imputation.py --data_path='./dataset/ecg_mitbih_test.csv' \
                     --option='mice' \
                     --output_path='./dataset/imputed_data/ecg_mitbih_test_imputed.csv'
```
#### 2.1.2 Testing imputation module by adding random NAs to temporary dataset.
Just add `--test_module` argument to the command-line for testing the module.
If ``--test_module` argument is given, `imputation.py` automatically adds random NAs to the dataset and then continues to impute the missing values.
```Python
* Sample Usage
python imputation.py --data_path='./dataset/ecg_mitbih_test.csv' \
                     --option='simple' \
                     --strategy='mean' \
                     --output_path='./dataset/imputed_data/ecg_mitbih_test_imputed.csv'
                     --test_module
```