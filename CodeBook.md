# Coursera Getting and Cleaning Data Course Project

## Project Description
The purpose of the project is to assemble a dataset from raw data provided and to then create a tidy dataset which 
contains summarized data which could be used for further analysis.

## Study design and data processing
The data used was from the following study:
==================================================================
Human Activity Recognition Using Smartphones Dataset
Version 1.0
==================================================================
Jorge L. Reyes-Ortiz, Davide Anguita, Alessandro Ghio, Luca Oneto.
Smartlab - Non Linear Complex Systems Laboratory
DITEN - Università degli Studi di Genova.
Via Opera Pia 11A, I-16145, Genoa, Italy.
activityrecognition@smartlab.ws
www.smartlab.ws
==================================================================

The experiments have been carried out with a group of 30 volunteers within an age bracket of 19-48 years. Each person performed six activities 
(WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING) wearing a smartphone (Samsung Galaxy S II) on the waist. Using its 
embedded accelerometer and gyroscope, we captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz. 
The experiments have been video-recorded to label the data manually. The obtained dataset has been randomly partitioned into two sets, where 70% of the 
volunteers was selected for generating the training data and 30% the test data. 

The sensor signals (accelerometer and gyroscope) were pre-processed by applying noise filters and then sampled in fixed-width sliding windows of 2.56 sec 
and 50% overlap (128 readings/window). The sensor acceleration signal, which has gravitational and body motion components, was separated using a Butterworth 
low-pass filter into body acceleration and gravity. The gravitational force is assumed to have only low frequency components, therefore a filter with 0.3 Hz cutoff 
frequency was used. From each window, a vector of features was obtained by calculating variables from the time and frequency domain. See 'features_info.txt' for more details. 

# Collection of the raw data
The section above describes how the raw data was collected.

# Guide to create the tidy data file
1. Download the data using the link provided in the project description (https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip).
2. Unizp the files and move all pertinent files to the working directory for the project.  Files needed are:
```
"subject_train.txt"
"y_train.txt"
"x_train.txt"
"subject_test.txt"
"y_test.txt"
"x_test.txt"
"activity_labels.txt"
```
3. Read the text files into dataframes in R.
4.  Merge the training and text data (including subjects, activities, and values) into one dataset.
5.  Retain only the variables that are the mean and standard deviation for each measurement.
6.  Summarize the dataset created above into a tidy dataset which contains the average of each measurement for each participant
and each activity.

## Cleaning of the data
The cleaning script reads in the data provided, merges it into one data set and retains only the mean and standard deviation measurements.
That dataset is then summarized to provide the average of each of the measurements in the dataset for each subject and activity combination.
See the readme.txt file for detailed description of the data cleaning process.

## Description of the variables in the tidy_data.txt file

### General description of the file:

* Dimensions of the dataset - 180 rows, 68 columns
* Summary of the data - each row consists of a subject/activity pair with the averages for each of the mean and standard deviation measurements
* Variables present in the dataset - 
```
 [1] "Subject"                  "Activity"                 "tBodyAccMeanX"            "tBodyAccMeanY"           
 [5] "tBodyAccMeanZ"            "tBodyAccStdX"             "tBodyAccStdY"             "tBodyAccStdZ"            
 [9] "tGravityAccMeanX"         "tGravityAccMeanY"         "tGravityAccMeanZ"         "tGravityAccStdX"         
[13] "tGravityAccStdY"          "tGravityAccStdZ"          "tBodyAccJerkMeanX"        "tBodyAccJerkMeanY"       
[17] "tBodyAccJerkMeanZ"        "tBodyAccJerkStdX"         "tBodyAccJerkStdY"         "tBodyAccJerkStdZ"        
[21] "tBodyGyroMeanX"           "tBodyGyroMeanY"           "tBodyGyroMeanZ"           "tBodyGyroStdX"           
[25] "tBodyGyroStdY"            "tBodyGyroStdZ"            "tBodyGyroJerkMeanX"       "tBodyGyroJerkMeanY"      
[29] "tBodyGyroJerkMeanZ"       "tBodyGyroJerkStdX"        "tBodyGyroJerkStdY"        "tBodyGyroJerkStdZ"       
[33] "tBodyAccMagMean"          "tBodyAccMagStd"           "tGravityAccMagMean"       "tGravityAccMagStd"       
[37] "tBodyAccJerkMagMean"      "tBodyAccJerkMagStd"       "tBodyGyroMagMean"         "tBodyGyroMagStd"         
[41] "tBodyGyroJerkMagMean"     "tBodyGyroJerkMagStd"      "fBodyAccMeanX"            "fBodyAccMeanY"           
[45] "fBodyAccMeanZ"            "fBodyAccStdX"             "fBodyAccStdY"             "fBodyAccStdZ"            
[49] "fBodyAccJerkMeanX"        "fBodyAccJerkMeanY"        "fBodyAccJerkMeanZ"        "fBodyAccJerkStdX"        
[53] "fBodyAccJerkStdY"         "fBodyAccJerkStdZ"         "fBodyGyroMeanX"           "fBodyGyroMeanY"          
[57] "fBodyGyroMeanZ"           "fBodyGyroStdX"            "fBodyGyroStdY"            "fBodyGyroStdZ"           
[61] "fBodyAccMagMean"          "fBodyAccMagStd"           "fBodyBodyAccJerkMagMean"  "fBodyBodyAccJerkMagStd"  
[65] "fBodyBodyGyroMagMean"     "fBodyBodyGyroMagStd"      "fBodyBodyGyroJerkMagMean" "fBodyBodyGyroJerkMagStd" 
```

```
Variable 1 
Subject - the study participant
integer value ranging from 1 to 30.
No unit of measurement
```

```
Variable 2 
Activity - the activity that these measurements pertain to
Factor value with 6 levels: WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING
No unit of measurement
```

```
Variables 3 - 68

The features selected for this database come from the accelerometer and gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ. 
These time domain signals (prefix 't' to denote time) were captured at a constant rate of 50 Hz. Then they were filtered using a 
median filter and a 3rd order low pass Butterworth filter with a corner frequency of 20 Hz to remove noise. Similarly, the acceleration 
signal was then separated into body and gravity acceleration signals (tBodyAcc-XYZ and tGravityAcc-XYZ) using another low pass Butterworth 
filter with a corner frequency of 0.3 Hz. 

Subsequently, the body linear acceleration and angular velocity were derived in time to obtain Jerk signals (tBodyAccJerk-XYZ and tBodyGyroJerk-XYZ). 
Also the magnitude of these three-dimensional signals were calculated using the Euclidean norm (tBodyAccMag, tGravityAccMag, tBodyAccJerkMag, tBodyGyroMag, tBodyGyroJerkMag). 

Finally a Fast Fourier Transform (FFT) was applied to some of these signals producing fBodyAcc-XYZ, fBodyAccJerk-XYZ, fBodyGyro-XYZ, fBodyAccJerkMag, 
fBodyGyroMag, fBodyGyroJerkMag. (Note the 'f' to indicate frequency domain signals). 

These signals were used to estimate variables of the feature vector for each pattern:  
'-XYZ' is used to denote 3-axial signals in the X, Y and Z directions.
```

```
tBodyAcc-XYZ
tGravityAcc-XYZ
tBodyAccJerk-XYZ
tBodyGyro-XYZ
tBodyGyroJerk-XYZ
tBodyAccMag
tGravityAccMag
tBodyAccJerkMag
tBodyGyroMag
tBodyGyroJerkMag
fBodyAcc-XYZ
fBodyAccJerk-XYZ
fBodyGyro-XYZ
fBodyAccMag
fBodyAccJerkMag
fBodyGyroMag
fBodyGyroJerkMag
```

```
The standard deviation and mean for each of the features listed above make up the variables in columns 3 to 68.
The variables are numeric values.
```
```
The Features are normalized and bounded within [-1,1].
```
## Sources
The information provided above relating to the features and the description of the data collection come from files in the downloaded zip file.