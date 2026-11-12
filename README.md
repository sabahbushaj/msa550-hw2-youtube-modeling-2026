# Assignment 2: Modeling YouTube Trending Video Data

**MSA 550 – Homework 2**
**Due:** November 30

## Overview

Recall the YouTube trending-videos dataset you cleaned in Homework 1. The cleaned version is included in this repository as `youtube.csv`, so it is ready for modeling. In this assignment you will build, tune, and compare predictive models from the techniques we have covered: multiple linear regression, logistic regression, kNN, decision trees (CART), and ensemble methods. You will do this with scikit-learn **pipelines** and **GridSearchCV**.

You will choose **one** of the two modeling tasks below, regression or classification, and complete it.

## The Data

`youtube.csv` has 38,627 videos and 7 columns:

| Column | Type | Description |
|---|---|---|
| `category` | text | Video category (16 categories, e.g., Music, Gaming, News & Politics) |
| `views` | integer | Number of views |
| `likes` | integer | Number of likes |
| `dislikes` | integer | Number of dislikes |
| `comment_count` | integer | Number of comments |
| `comments_disabled` | 0/1 | 1 if comments are disabled on the video |
| `ratings_disabled` | 0/1 | 1 if ratings are disabled on the video |

`category` is text, so you will need to decide how to encode it for each model.

## Your Task

Choose **one** of the following.

### Option 1 – Regression: predict `views`

Build models that predict the number of views a video receives. Use the other columns as candidate predictors.

Consider how skewed `views` is. If you transform the target (for example, with a log), explain why, and make sure you evaluate your final results in a way that is meaningful to someone reading them.

### Option 2 – Classification: predict `comments_disabled`

Build models that predict whether a video has comments disabled.

Before you start, look at how `comments_disabled` relates to `comment_count`. In your notebook, explain what issues this relationship could cause for your model and how you handle them. Also look at the class balance, since it affects which metrics are useful.

## Requirements

**1. Data preparation**
- Choose your features and justify them.
- You can use the full dataset. If runs take too long, you may instead use a subset of it (at least 1,000 observations).
- Split into training and test sets. Use a fixed `random_state`, and stratify if you chose classification.

**2. Models**
Fit **at least three different models** using techniques we have covered (for example multiple linear regression, logistic regression, kNN, decision trees, and ensemble methods such as Random Forest or Gradient Boosting). Choosing models that suit your task is part of the assignment.

- Build each model as a scikit-learn `Pipeline`, with preprocessing (encoding, scaling, and so on) inside the pipeline rather than done by hand beforehand.
- Tune hyperparameters with `GridSearchCV` using cross-validation on the training set only. Do not tune on the test set.
- For every model, explain **why you chose it** and what its tuned hyperparameters do.

**3. Evaluation**
- Evaluate on the held-out test set with metrics that fit the task and justify your choices.
  - Regression: for example RMSE, MAE, R².
  - Classification: accuracy alone is not enough for this data. Include a confusion matrix and metrics such as precision, recall, F1, and ROC-AUC.
- Compare cross-validation and test performance. Comment on any overfitting.
- Where a model offers it (coefficients, feature importances), say which features matter most and whether that makes sense.

**4. Comparison and conclusion**
Compare your models in a single summary table and recommend one model. Justify your recommendation by considering performance, interpretability, and complexity.

## Submission via GitHub

1. Click **Use this template** at the top of this repository, choose **Create a new repository**, and set it to **Private**.
2. Add the instructor (Dr. Bushaj) as a collaborator: `sabahbushaj` right after creating the repository, or your work won't be visible.
3. Clone your repository to your computer and do your work there. Commit regularly with meaningful messages.
4. Your notebook must be named `fname_lname_msa550_hw02.ipynb` and placed in the root of the repository, next to `youtube.csv`.
5. Before pushing your final version, restart the kernel and **Run All** to confirm the notebook runs top to bottom without errors, and that its output is saved.
6. Push to GitHub before the deadline. The latest commit before the deadline is what will be graded.

Do not modify `youtube.csv`.

## Grading

| Component | Weight | What I'm looking for |
|---|---|---|
| Data preparation | 10% | Justified feature choices and a sound train/test split, including how you handle the issues noted in your task |
| Model implementation | 40% | Correct use of pipelines and GridSearchCV, at least three models, no data leakage |
| Performance analysis | 25% | Appropriate metrics, interpretation of the results, and discussion of overfitting and feature importance |
| Comparison and justification | 15% | Clear summary tables and a well-supported model recommendation |
| Documentation and readability | 10% | Markdown explanations, clear code and comments, notebook runs cleanly, tidy repository |

Good luck, and enjoy exploring predictive modeling with this dataset!
