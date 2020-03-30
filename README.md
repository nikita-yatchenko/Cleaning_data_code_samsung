==================================================================

Getting and Cleaning Data Course Project (Coursera)
==================================================================

The goal of this project is to combine test and train datasets in a tidy format and outut summarized data in a table. That table summarizes the experiments that have been carried out with a group of 30 volunteers within an age bracket of 19-48 years. Each person performed six activities (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING) wearing a smartphone (Samsung Galaxy S II) on the waist.

We first read train and test datasets and extract variable names vector into the R environment. For each set of data there are feature dataset (X), label dataset (y) and subject identification vector (subject_[train | test]). We combine complete train dataset first, then test dataset, making sure to use variable names as the new column names for both datasets. After subject_id, activity, train and test data, and proper naming have been compiled we procede to stapling both datasets together. 

We then work with a combined dataset to: \n
a. convert activity labels (1-6) to (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING) \n
b. rename columns to have more user-friendly names \n
c. compile a summary tidy dataset with the average of each variable for each activity and each subject \n

The final dataset is tidy per the ReadMe that can be read into R with read.table(header=TRUE), where each row contains a single observation (unique combination of subject with an activity), each column representing a variable, and a table containing variables relating only to movement analysis.

The dataset includes the following files:
=========================================

- 'README.md' - explains the procedure and purpose of the project

- 'CodeBook.md': shows information about the variables used

- 'run_analysis.R': r script that performs raw data to tidy dataset transformation

- 'tidy_summarized_data.txt': final tidy data
