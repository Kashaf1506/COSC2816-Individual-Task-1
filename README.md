# Student Success Early-Warning Analysis

## Project overview

This project investigates whether machine-learning models can identify students
at risk of dropout or unsuccessful academic outcomes using information
available early in their studies.

The analysis was completed for RMIT COSC2816 Individual Task 1. Predictions are
intended to support student-success teams and should not be used to make
automatic decisions about students.

## Research question

Can machine-learning models identify students at risk of dropout or
unsuccessful academic outcomes using enrolment, early academic and
online-learning information?

## Datasets

### Dataset 1: Predict Students' Dropout and Academic Success

Source:  
https://archive.ics.uci.edu/dataset/697/predict+students+dropout+and+academic+success

This dataset contains 4,424 records and 36 original predictors covering
enrolment, demographics, socioeconomic circumstances and academic performance.
The target classes are Dropout, Enrolled and Graduate.

The six second-semester predictors were excluded to create a more realistic
early-warning analysis.

### Dataset 2: Open University Learning Analytics Dataset

Source:  
https://archive.ics.uci.edu/dataset/349/open+university+learning+analytics+dataset

OULAD contains 32,593 student-course records and more than 10 million
virtual-learning interaction records. It includes student characteristics,
registration, assessment and online-engagement information.

Only information available by day 60 was used. The binary target was:

- At Risk: Withdrawn or Fail
- Successful: Pass or Distinction

## Models

Two classification algorithms were applied to both datasets:

- Decision Tree
- Random Forest

The models were compared using stratified five-fold cross-validation on the
training data. Random Forest achieved the strongest cross-validation results
for both datasets and was selected for final test evaluation.

A random seed of `42` was used throughout the analysis.

## Evaluation measures

The reported measures include:

- accuracy;
- balanced accuracy;
- macro F1-score;
- per-class precision, recall and F1-score;
- confusion matrices.

Dropout recall was emphasised for Dataset 1. Precision, recall and F1-score for
the At Risk class were emphasised for Dataset 2.

## Main findings

For Dataset 1, Random Forest achieved a test macro F1-score of `0.6582` and
Dropout recall of `0.6655`. First-semester academic performance and tuition
payment status were among the strongest predictors.

For Dataset 2, Random Forest achieved a test macro F1-score of `0.7379` and At
Risk recall of `0.6582`. Assessment performance, missing assessments and early
online engagement were the strongest predictors.

The findings are complementary: enrolment and academic information provide one
view of student risk, while early assessment and online-learning behaviour
provide additional warning signals.

## Project structure

```text
.
├── data/
│   ├── raw/
│   └── processed/
├── evidence/
│   └── screenshots/
├── notebooks/
│   ├── student_success_analysis.ipynb
│   └── results/
│       ├── figures/
│       └── metrics/
├── src/
│   ├── __init__.py
│   ├── data_preparation.py
│   └── modelling.py
├── .gitignore
├── README.md
└── requirements.txt