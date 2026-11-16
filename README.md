# Tourism Accommodation Classification Using Decision Trees

## Project overview

This project applies a **Decision Tree Classifier** to tourism
accommodation data. The aim is to classify selected tourism records into
two relative categories:

-   **Low (0):** the record's tourism value is less than or equal to the
    median calculated from the training data.
-   **High (1):** the record's tourism value is greater than the median
    calculated from the training data.

This project demonstrates a basic supervised-learning classification
workflow for a Machine Learning assignment.

## Problem statement

> To classify tourism accommodation records into High and Low categories
> using a Decision Tree Classification algorithm based on geographical
> area and year.

## Dataset

The CSV used during development contains tourism observations and fields
including:

-   `country` --- geographical area name (the data may include regions
    as well as countries)
-   `year` --- observation year
-   `guest_residence` --- visitor-residence category
-   `measure` --- measurement type
-   `accommodation` --- accommodation category
-   `is_country_group` --- indicates whether a row represents an
    aggregate country group
-   `value` --- numerical tourism measurement

The original dataset used during development contained **99,391 rows and
16 columns**.

### Filtering

The model keeps records matching all of these conditions:

-   `measure == "Number"`
-   `is_country_group == False`
-   `guest_residence == "Total"`
-   `accommodation == "Hotels and similar accommodation"`

The filtered records are split into training and testing subsets using
an 80/20 split and `random_state=42`.

**Dataset source and redistribution:** Add the dataset provider,
original source URL, citation and dataset licence here before
publishing. Do not upload or redistribute the CSV unless its licence or
provider permits it. If redistribution is not permitted, leave the CSV
out of this repository and explain how authorised users can obtain it.

## Methodology

1.  Import the required Python libraries.
2.  Load and inspect the CSV dataset.
3.  Review column types and missing values.
4.  Filter the dataset using the conditions above.
5.  Split the filtered records into training (80%) and testing (20%)
    subsets.
6.  Calculate the median `value` from the training subset only.
7.  Create the target labels: `0` for Low (`value` less than or equal to
    the median) and `1` for High (`value` greater than the median).
8.  Use `country` and `year` as input features.
9.  Apply One-Hot Encoding to `country`; pass `year` through as a
    numerical feature. Fit the encoder on training data only, then
    transform the testing data.
10. Train a `DecisionTreeClassifier` with `max_depth=5` and
    `random_state=42`.
11. Predict the testing labels and evaluate the model using accuracy,
    confusion matrix and classification report.
12. Visualise the confusion matrix and decision tree.

## Model configuration

  Setting                  Value
  ------------------------ ----------------------------------------
  Algorithm                Decision Tree Classifier
  Learning type            Supervised learning --- classification
  Input features           `country`, `year`
  Target                   `tourism_category` (Low / High)
  Training/testing split   80% / 20%
  Split random state       42
  Maximum tree depth       5
  Model random state       42
  Categorical encoding     One-Hot Encoding

## Suggested repository structure

``` text
.
├── README.md
├── requirements.txt
├── LICENSE
├── Decision_Tree_Classification.ipynb
└── data/
    └── (include the dataset only if redistribution is permitted)
```

Use the actual notebook filename downloaded from Kaggle.

## How to run

### Kaggle

1.  Open the notebook in Kaggle.
2.  Attach the dataset using **Add Input**.
3.  Check that the CSV path in the notebook matches the Kaggle input
    path, usually under `/kaggle/input/`.
4.  Run all notebook cells.

### Local Python environment

1.  Clone or download this repository.

2.  Install the dependencies:

    ``` bash
    python -m pip install -r requirements.txt
    ```

3.  Place the authorised CSV file in your project directory or update
    the path in the notebook.

4.  Open the notebook in Jupyter or VS Code and run the cells.

## Evaluation

The notebook reports:

-   Accuracy
-   Confusion matrix
-   Precision
-   Recall
-   F1-score

Run the notebook to obtain the results for your environment and dataset.
Results can differ if the dataset, filtering, split or code changes.

## Limitations and interpretation

-   The High/Low labels are **relative to the median of the training
    data**. They are not official tourism-demand classifications.
-   The model classifies records; it does not predict the exact number
    of tourists.
-   A random split can place observations from the same geographical
    area in both training and testing sets. Test accuracy therefore does
    not establish performance on entirely unseen geographical areas or
    future years.
-   The dataset may include regions as well as sovereign countries.
    Interpret `country` as a geographical-area field where appropriate.
-   After filtering, the model uses only `country` and `year`. Interpret
    results in the context of this limited feature set.

## Author

**Author:** \[Your Name\]\
**Course / Subject:** Machine Learning\
**Project:** Decision Tree Classification --- Tourism Dataset

## Licence

The source code and project documentation are released under the MIT
License. This does not automatically grant permission to redistribute
the third-party dataset. See `LICENSE` and the dataset provider's terms.
