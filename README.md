# Readme for run_analysis.R

This readme file describes how the script "run_analysis.R" works.

The script assumes that the data sets needed in the script have already been downloaded
to the user's working directory (per project description).

1.  The first section of the script reads each of the files needed for the project into an
R data frame. 
```
The training data consists of:
subject_train.txt - the list of subjects corresponding to the data
y_train.txt - the activity the measurements pertain to
x_train.txt - the measurements  collected for each of the 561 features
Each file has 7352 rows.
```
```
The test data consists of:
subject_test.txt - the list of subjects corresponding to the data
y_test.txt - the activity the measurements pertain to
x_test.txt - the measurements  collected for each of the 561 features
Each file has 2947 rows.
```
```
The final data set read in this step is:
activity_labels.txt - a text description of the activity number provided in the activity
files above (y_train.txt, y_test.txt).
```
2. Next a data set is created which contains the mean and standard deviation features 
that we want in our final data frame.  
  a.  The features.txt file is read in.  This file contains the names of each of the 561 features.
  b.   We select only those features which contain 'mean' or 'std'.  We do not select those
which contain 'meanfreq'.  We use the grepl function to do this.
  c.  We do some minor editing of variable names to make them more readable. 

3.  Check to make sure the 'dplyr' package is installed.  Functions from dplyr will be used.

4.  Combine the data from the training and test datasets using rbind.  Take a subset of the
columns by using the columns selected in step 2 above.  Use the names of the features found
in step 2 above to name the columns.

5.  Use rbind to combine the subjects from the test and training data sets.  Name the column
"Subject".

6.  Use rbind to combine the activities for the training and test data sets.  Use the
activites data set read in step 1 above to substitute the character description of the 
activities for the numeric activity number in the combined data set.  Name the column "Activity".

7.  Use cbind to combine the subjects, labels, and data dataframes that were created in
steps 4 - 6 above.

8.  Use group_by from the dplyr package to group the dataframe created in step 7 by subject and
activity.  Then use summarize_each function to calculate the average value of each of the
data values in the dataframe for each subject/activity combination.  The format of
the dataframe is the wide format with each of the average values associated with a column 
variable.  This data frame has 180 rows and 68 columns. This is the tidy data set 
described in step 5 of the project instruction.  It meets the requirements of tidy data because:
  * each variable is in one column
  * each observation is in a different row
  * there is only one kind of data in the table

9.  Use write.table() using row.names=FALSE to create 'tidy_data.txt" to upload for the project.

Notes:  
1.  The numbers of the above steps are reflected in the comments of the run_analysis.R
file.
2.  See the CodeBook.md file for the project code book.
or 'std'.
