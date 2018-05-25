# Getting and Cleaning Data - Course Project - CodeBook.md


__Author: Edgar Esteban Herrera Collazos__

__2018 Getting and Cleaning Data Course Project__

This document describes the data and transformations I utilized in *run_analysis.R* and the definition of the variables found in *tidy.txt*.

## Dataset Used

This data is obtained from "Human Activity Recognition Using Smartphones Data Set". The data linked are collected from the accelerometers from the Samsung Galaxy S smartphone. A full description is available at the site <http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones>

The data set used can be downloaded from <https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip> 

## Input Data Set

The input data containts the following data files:

- `X_train.txt` has variable features that are intended for training.
- `y_train.txt` has the activities corresponding to `X_train.txt`.
- `subject_train.txt` has information on the subjects from whom data is collected.
- `X_test.txt` has variable features that are intended for testing.
- `y_test.txt` has the activities corresponding to `X_test.txt`.
- `subject_test.txt` has information on the subjects from whom data is collected.
- `activity_labels.txt` has metadata on the different types of activities.
- `features.txt` has the name of the features in the data sets.

## Transformations

Following are the transformations that were performed on the input dataset:

- `X_train.txt` ---> `featuresTrain`.
- `y_train.txt` ---> `activityTrain`.
- `subject_train.txt` ---> `subjectTrain`.
- `X_test.txt` ---> `featuresTest`.
- `y_test.txt` ---> `activityTest`.
- `subject_test.txt` ---> `subjectTest`.
- `features.txt` ---> `featureNames`.
- `activity_labels.txt` ---> `activityLabels`.
- The subjects in training and test set data are merged to form `subject`.
- The activities in training and test set data are merged to form `activity`.
- The features of test and training are merged to form `features`.
- The name of the features are set in `features` from `featureNames`.
- `features`, `activity` and `subject` are merged to form `completeData`.
- Indices of columns that contain std or mean, activity and subject are taken into `requiredColumns` .
- `extractedData` is created with data from columns in `requiredColumns`.
- `Activity` column in `extractedData` is updated with descriptive names of activities taken from `activityLabels`. `Activity` column is expressed as a factor variable.
- Acronyms in variable names in `extractedData`, like 'Acc', 'Gyro', 'Mag', 't' and 'f' are replaced with descriptive labels such as 'Accelerometer', 'Gyroscpoe', 'Magnitude', 'Time' and 'Frequency'.
- `tidyData` is created as a set with average for each activity and subject of `extractedData`. Entries in `tidyData` are ordered based on activity and subject.
- Finally, the data in `tidyData` is written into `tidy.txt`.

## Output Data Set

The output data `tidy.txt` is a a space-delimited file. The header line contains the names of the variables. It contains the mean and standard deviation values of the data contained in the input files. The header is restructued in an understandable manner. 
