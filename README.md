## Background:

Human Activity Recognition Using Smartphones Dataset

The project contains the main script run_analysis.R which prepares a tidy dataset from Human Activity Recognition Using Smartphones Dataset.

## The dataset includes the following files:
* 'README.md': Explains how all of the script works and which a raw data it uses.

* 'CodeBook.md': Describes the variables, the data, and any transformations or work that script performed to clean up the data.

* 'run_analysis.R': Contains the script code.

* 'tidy_data_mean_std.txt': The tidy data set with the average of mean() and std() variables for each activity and each subject.

### How run script:
1. Download a dataset from https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip to the work directory.
2. Copy the 'run_analysis.R' script to the 'UCI HAR Dataset' directory.
3. Open script in the RStudio or R application.
4. Before to execute the script please install the 'dplyr' library.
5. Run the script and wait few seconds to finish processing the data set.
6. When Analysis FINISHed the data set directory contains the 'tidy_data_mean_std.txt' file.
7. Read the file: tdms <- read.table("tidy_data_mean_std.txt", header = TRUE, sep = "")

## Analysis does:
1. Reads training and test dataset files.
2. Merges the training and the test sets to create one data set.
3. Reads features and activity labels files.
4. Uses descriptive features names to name the featured measurements in the main data set by column position.
5. Extracts only the measurements on the mean and standard deviation (avoid meanFreq) for each measurement from the main data set.
6. Merges the subjects set to the main data set.
7. Uses descriptive activity names to name the activities in the activity data set by ID.
8. Merges the activity set to the main data set.
9. From the main data set, creates a second, independent tidy data set with the average of each variable for each activity and each subject.
10. Saves the tidy data set to the 'tidy_data_mean_std.txt' file.
11. Removes all temporary data.

##License:
Use of this dataset in publications must be acknowledged by referencing the following publication [1]

[1] Davide Anguita, Alessandro Ghio, Luca Oneto, Xavier Parra and Jorge L. Reyes-Ortiz. Human Activity Recognition on Smartphones using a Multiclass Hardware-Friendly Support Vector Machine. International Workshop of Ambient Assisted Living (IWAAL 2012). Vitoria-Gasteiz, Spain. Dec 2012

This dataset is distributed AS-IS and no responsibility implied or explicit can be addressed to the authors or their institutions for its use or misuse. Any commercial use is prohibited.

Anatoli Macarov. January 2019.
