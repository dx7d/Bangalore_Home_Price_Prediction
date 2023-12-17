# Bangalore Home Price Prediction

## Overview

This project focuses on predicting home prices in Bangalore using a linear regression model. The model takes location, square footage, bathrooms, and bedrooms as input and returns prices in lakhs.


## Table of Contents

- [Getting Started](#getting-started)
  - [1. Import Libraries](#1-import-libraries)
  - [2. Data Preprocessing](#2-data-preprocessing)
  - [3. Dimensionality Reduction](#3-dimensionality-reduction)
  - [4. Outlier Removal](#4-outlier-removal)
  - [5. One Hot Encoding](#5-one-hot-encoding)
- [Model Development](#model-development)


## Getting Started

### 1. Import Libraries

Ensure you have the necessary libraries installed:

```bash
pip install -r requirements.txt
```

### 2. Data Preprocessing

- Drop unnecessary features: 'area_type', 'society', 'balcony', 'availability'.
- Remove rows with null values.
- Extract the number of bedrooms (bhk) from the string.
- Handle ranges in total square footage by taking the average.

### 3. Dimensionality Reduction

Apply dimensionality reduction techniques to reduce the number of locations. Locations with less than 10 data points are tagged as "Other."

### 4. Outlier Removal

- Set a minimum threshold per bedroom to remove suspicious outliers.
- Remove outliers per location using mean and one standard deviation.
- Remove 2 BHK apartments with price_per_sqft less than the mean price_per_sqft of 1 BHK apartments.

For a detailed explanation, refer to the [Outlier Removal section](#).

### 5. One Hot Encoding

Perform one-hot encoding for location since machine learning models cannot handle categorical values.

## Model Development

1. Split the dataset into training and test sets.
2. Utilize linear regression for price prediction.
3. Apply k-fold cross-validation (5 iterations) using the `ShuffleSplit` cross-validator.
