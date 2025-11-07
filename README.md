# Beaderstadt Midterm Project: Classification Analysis
> My personalized Submission: GitHub Repository with Jupyter Notebook and Peer Review.

## Project Overview
In this project, I explore the UCI Mushroom dataset to predict whether a mushroom is edible or poisonous using machine learning. I train and evaluate Decision Tree and Random Forest classifiers, examining which features have the most influence on predictions. The goal is to compare model performance, interpret their decision-making, and uncover patterns in the data that help distinguish edible from poisonous mushrooms.

[Click here for my notebook file.](https://github.com/abeaderstadt/ml_classification_beaderstadt/blob/main/classification_beaderstadt.ipynb)<br>
[Click here for my peer review file.](https://github.com/abeaderstadt/ml_classification_beaderstadt/blob/main/peer_review.md)<br>

---

## Key Steps in This Project

## 1. Import and Inspect the Data
- Loaded the Mushroom dataset from UCI.
- Inspected the dataset using `.info()`, `.head()`, `.describe()`, and `.isnull().sum()`.
- Explored feature types and distributions.

  - **Insights:**
    - 8,124 instances and 23 features.
    - All features are categorical, requiring encoding for modeling.
    - The target variable is class (edible or poisonous).

---

## 2. Data Exploration and Preparation

### 2.1 Handle Missing Values
- Rather than dropping rows for missing `stalk-root` values, I created a separate `"missing"` category to preserve potential information.
- Drop uninformative `veil-type` column. 

### 2.2 Feature Engineering
- Encoded all categorical variables as numeric using one-hot encoding.
- Created `cap-color-group` to combine cap colors into "light" and "dark". 

  - **Rationale:**
    - “light” and “dark” tones may capture general visual patterns that might relate to edibility.
    - Numeric encoding enables machine learning models to process these features.

---

## 3. Feature Selection and Target Definition
- Input features explored for modeling:  
  - Key categorical features: `odor`, `gill-color`, `cap-shape`, `bruises`, `spore-print-color`, and the new feature `cap-color-group`

- Target variable: `class` (edible vs. poisonous).

**Reasoning:**  
- Using different feature combinations lets us compare performance and see which factors are most predictive.

---

## 4. Data Splitting and Stratification
- Split the data into training and test sets using train_test_split.
- Preserved the class balance for reliable evaluation.
  
---

## 5. Model Training and Evaluation

### 5.1 Decision Tree Classifier
- Trained on full feature set.
- Evaluated using classification reports and confusion matrices.
- Visualized decision tree to interpret feature importance.

### 5.2 Random Forest Classifier
- Trained with multiple trees to reduce overfitting.
- Evaluated performance on test data.
- Analyzed feature importance across all trees.

**Reflection:**
- Both the Decision Tree and Random Forest performed nearly perfectly, with almost identical accuracy, precision, recall, and F1-scores.
- Decision Trees are interpretable; Random Forests often improve accuracy.
- Visualizations help understand how features contribute to predictions.
  
---

## 6. Final Thoughts & Insights

### Top features and model performance
| Model         | Top Features     | Train Accuracy | Test Accuracy | Precision (poisonous) | Recall (poisonous) | F1-score (poisonous) |
| ------------- | ---------------- | -------------- | ------------- | --------------------- | ------------------ | -------------------- |
| Decision Tree | odor, spore-print-color | 1.00           | 0.99          | 1.00                  | 0.99               | 1.00                 |
| Random Forest | odor, spore-print-color | 1.00           | 0.99          | 1.00                  | 0.99               | 0.99                 |


- `Odor` and `spore-print-color` were the two most predictive features.
- The new feature `cap-color-group` was not as powerful of a predictor as other single features.
- A single Decision Tree did an excellent job on this dataset. However, the Random Forest adds extra stability by averaging across many trees, which helps with generalization and reduces the tiny risk of overfitting.
- Future work: Create additional engineered features from existing ones (like combining odor and cap color) to see if they add any predictive value.

---

## How to Run

1. **Open the Project Notebook**  
   Navigate to and open the Jupyter notebook:  
   `classification_beaderstadt.ipynb`

2. **Select the Correct Kernel**  
   Ensure the notebook uses the correct Python environment where required libraries are installed.

3. **Clear Kernel / Outputs (Optional)**  
   Use Kernel -> Restart & Clear Outputs to start fresh and avoid stale variables or plots.

4. **Run the Notebook**  
   Execute cells sequentially to load data, prepare features, train models, and visualize results.

5. **View Results**  
   Classification reports, confusion matrices, decision trees, and random forest display inline.  
   Use these outputs to analyze edibility patterns and model performance.

---

## Setup Instructions

## WORKFLOW 1. Set Up Machine

Proper setup is critical.
Complete each step in the following guide and verify carefully.

- [SET UP MACHINE](./SET_UP_MACHINE.md)

---

## WORKFLOW 2. Set Up Project

After verifying your machine is set up, set up a new Python project by copying this template.
Complete each step in the following guide.

- [SET UP PROJECT](./SET_UP_PROJECT.md)

It includes the critical commands to set up your local environment (and activate it):

```shell
uv venv
uv python pin 3.12
uv sync --extra dev --extra docs --upgrade
uv run pre-commit install
uv run python --version
```

**Windows (PowerShell):**

```shell
.\.venv\Scripts\activate
```
---

## WORKFLOW 3. Daily Workflow

Once the environment is ready, follow these steps when working on the project.

### 3.1 Git Pull from GitHub

Always start with `git pull` to check for any changes made to the GitHub repo.

```shell
git pull
```

### 3.2 Run Checks as You Work

This mirrors real work where we typically:

1. Update dependencies (for security and compatibility).
2. Clean unused cached packages to free space.
3. Use `git add .` to stage all changes.
4. Run ruff and fix minor issues.
5. Update pre-commit periodically.
6. Run pre-commit quality checks on all code files (**twice if needed**, the first pass may fix things).
7. Run tests.

In VS Code, open your repository, then open a terminal (Terminal / New Terminal) and run the following commands one at a time to check the code.

```shell
git pull
uv sync --extra dev --extra docs --upgrade
uv cache clean
git add .
uvx ruff check --fix
uvx pre-commit autoupdate
uv run pre-commit run --all-files
git add .
uv run pytest
```

NOTE: The second `git add .` ensures any automatic fixes made by Ruff or pre-commit are included before testing or committing.
Running `uv run pre-commit run --all-files` twice may be helpful if the first time doesn't pass. 

<details>
<summary>Click to see a note on best practices</summary>

`uvx` runs the latest version of a tool in an isolated cache, outside the virtual environment.
This keeps the project light and simple, but behavior can change when the tool updates.
For fully reproducible results, or when you need to use the local `.venv`, use `uv run` instead.

</details>

### 3.4 Git add-commit-push to GitHub

After making changes:

1. Stage your changes with git add.
2. Commit your changes with a useful message in quotes.
3. Push your work to GitHub.

```shell
git add .
git commit -m "describe your change in quotes"
git push -u origin main
```

### 3.6 Modify and Debug

Start new sessions with `git pull` to sync changes.

Update dependencies regularly to prevent conflicts.

Make incremental changes, testing as you go, and commit often.

---
