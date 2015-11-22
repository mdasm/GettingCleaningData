# CodeBook
*****
This is a code book that describes the variables, data, and any transformations or work that was performed to clean up the data.

## Raw Data Collection
*****

### Data Collection

downloads required data from https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip

### Data Set Information

The experiments have been carried out with a group of 30 volunteers within an age bracket of 19-48 years. Each person performed six activities (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING) wearing a smartphone (Samsung Galaxy S II) on the waist. Using its embedded accelerometer and gyroscope, we captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz. The experiments have been video-recorded to label the data manually. The obtained dataset has been randomly partitioned into two sets, where 70% of the volunteers was selected for generating the training data and 30% the test data.

The sensor signals (accelerometer and gyroscope) were pre-processed by applying noise filters and then sampled in fixed-width sliding windows of 2.56 sec and 50% overlap (128 readings/window). The sensor acceleration signal, which has gravitational and body motion components, was separated using a Butterworth low-pass filter into body acceleration and gravity. The gravitational force is assumed to have only low frequency components, therefore a filter with 0.3 Hz cutoff frequency was used. From each window, a vector of features was obtained by calculating variables from the time and frequency domain.

### Attribute Information:

For each record in the dataset is provided:

Triaxial acceleration from the accelerometer (total acceleration) and the estimated body acceleration.
Triaxial Angular velocity from the gyroscope.
A 561-feature vector with time and frequency domain variables.
Its activity label.
An identifier of the subject who carried out the experiment.

See Readme file into 'UCI HAR Dataset' for more information.
*******
## Raw Data Transformation

Raw data transformation is performed using run_analysis.R. The code:
unzips the file if it has not been uncompressed
creates results folder if it does not exist (all files are stored in this folder)
loads features.txt used for columns
loads X_train.txt, y_train.txt, subject_train.txt
X_train contains the data using the feature data set as columns
y_train contains the activity labels
subject_train contains the ids
loads and appends test dataset using X_test.txt, y_test.txt, subject_test.txt
X_test contains the data using the feature data set as columns
y_test contains the activity labels
subject_test contains the ids
appends train and test data
rearrange the data using id
loads activity_labels.txt
changes the data activity row to use the activity labels
saves the mean and std into mean_and_std.csv
saves the tidy dataset into tidy_dataset.csv
saves the tidy dataset into a text file tidy_dataset

**Merge training and test sets.** Test and training data, subject ids and activity ids are merged to obtain a single data set. Variables are labelled with the names assigned by original collectors.

**Extract mean and standard deviation variables.** Keep only the values of estimated mean and standard deviation .

**Get descriptive activity names.** A new column is added to intermediate data set with the activity description.

**Get label variables appropriately.** Labels given from the original collectors were used

**Create a tidy data set.** From the intermediate data set is created a final tidy data set where numeric variables are averaged for each activity and each subject.

mean_and_std.csv: contains 10299 rows and 81 columns or 10300 (including header) rows and 82 columns (including enumeration column) in a default csv format

tidy_dataset: contains 180 rows and 81 columns or 181 rows (including header) and 82 columns (including enumeration column) in a default csv format

variables:
id
activity
"tBodyAcc.mean...X" " "tBodyAcc.mean...Y" "tBodyAcc.mean...Z" "tGravityAcc.mean...X" "tGravityAcc.mean...Y" 
"tGravityAcc.mean...Z" "tBodyAccJerk.mean...X" "tBodyAccJerk.mean...Y" "tBodyAccJerk.mean...Z" "tBodyGyro.mean...X" 
"tBodyGyro.mean...Y" "tBodyGyro.mean...Z" "tBodyGyroJerk.mean...X" "tBodyGyroJerk.mean...Y" "tBodyGyroJerk.mean...Z" 
"tBodyAccMag.mean.." "tGravityAccMag.mean.." "tBodyAccJerkMag.mean.." "tBodyGyroMag.mean.." "tBodyGyroJerkMag.mean.." 
"fBodyAcc.mean...X" "fBodyAcc.mean...Y" "fBodyAcc.mean...Z" "fBodyAcc.meanFreq...X" "fBodyAcc.meanFreq...Y" 
"fBodyAcc.meanFreq...Z" "fBodyAccJerk.mean...X" "fBodyAccJerk.mean...Y" "fBodyAccJerk.mean...Z" "fBodyAccJerk.meanFreq...X" 
"fBodyAccJerk.meanFreq...Y" "fBodyAccJerk.meanFreq...Z" "fBodyGyro.mean...X" "fBodyGyro.mean...Y" "fBodyGyro.mean...Z" 
"fBodyGyro.meanFreq...X" "fBodyGyro.meanFreq...Y" "fBodyGyro.meanFreq...Z" "fBodyAccMag.mean.." "fBodyAccMag.meanFreq.." 
"fBodyBodyAccJerkMag.mean.." "fBodyBodyAccJerkMag.meanFreq.." "fBodyBodyGyroMag.mean.." "fBodyBodyGyroMag.meanFreq.." 
"fBodyBodyGyroJerkMag.mean.." "fBodyBodyGyroJerkMag.meanFreq.." "tBodyAcc.std...X" "tBodyAcc.std...Y" "tBodyAcc.std...Z" 
"tGravityAcc.std...X" "tGravityAcc.std...Y" "tGravityAcc.std...Z" "tBodyAccJerk.std...X" "tBodyAccJerk.std...Y" 
"tBodyAccJerk.std...Z" "tBodyGyro.std...X" "tBodyGyro.std...Y" "tBodyGyro.std...Z" "tBodyGyroJerk.std...X" 
"tBodyGyroJerk.std...Y" "tBodyGyroJerk.std...Z" "tBodyAccMag.std.." "tGravityAccMag.std.." "tBodyAccJerkMag.std.." 
"tBodyGyroMag.std.." "tBodyGyroJerkMag.std.." "fBodyAcc.std...X" "fBodyAcc.std...Y" "fBodyAcc.std...Z" "fBodyAccJerk.std...X" 
"fBodyAccJerk.std...Y" "fBodyAccJerk.std...Z" "fBodyGyro.std...X" "fBodyGyro.std...Y" "fBodyGyro.std...Z" "fBodyAccMag.std.." 
"fBodyBodyAccJerkMag.std.." "fBodyBodyGyroMag.std.." "fBodyBodyGyroJerkMag.std.."
