# DAS-Group-21

This repository contains Group 21's work for the spam email analysis in Data Analysis Skills Group Project 2.

## Project Overview

The project looks at which email features are related to spam. We use logistic regression and compare:

- the original full model
- the reduced model
- an improved model with transformed predictors and a train-test split

## Dataset

The analysis uses `dataset21.csv`, which has 920 emails and these variables:

- `yesno`: spam label (`y` for spam, `n` for non-spam)
- `crl.tot`: total length of capital letter runs
- `dollar`: frequency of the dollar sign
- `bang`: frequency of exclamation marks
- `money`: frequency of the word `money`
- `n000`: frequency of the string `000`
- `make`: frequency of the word `make`

The dataset has no missing values. It contains 557 non-spam emails and 363 spam emails.

## Files

- `Group-21.qmd`: main Quarto report source
- `Group-21.pdf`: final PDF report
- `Group-21.html`: old HTML output from earlier version
- `dataset21.csv`: project dataset
- `README.md`: short project summary

## Improved Model

The final improved model is:

`yesno ~ log_crl_tot + log_dollar + log_bang + log_money + log_n000`

We kept the same logistic regression idea, but transformed the skewed predictors and checked the model on a held-out test set.

## Key Results

Main results in the report:

- the original full model achieved an in-sample accuracy of `0.8511`
- the original reduced model achieved a very similar in-sample accuracy of `0.8500`
- the improved model achieved:
  - accuracy: `0.8197`
  - sensitivity: `0.7083`
  - specificity: `0.8919`
  - AUC: `0.8879`

The improved model gives a lower accuracy than the in-sample result, but it is a more realistic result because it is tested on unseen data.

## Main Conclusion

Higher values of capital-letter runs, dollar signs, exclamation marks, the word `money`, and the string `000` are all associated with a higher probability that an email is classified as spam.

## Reproducing the Analysis

1. Open the repository folder in RStudio or a terminal.
2. Make sure the required R packages are installed:
   - `tidyverse`
   - `broom`
   - `caret`
   - `pROC`
   - `knitr`
3. Render the report from the repository root:

```bash
quarto render Group-21.qmd
```

This produces the PDF output `Group-21.pdf`.

The report uses `set.seed(21)` so the train-test split can be reproduced.

If Quarto is not installed, you can still run the code chunks in `Group-21.qmd` from RStudio after setting the working directory to the repository folder.
