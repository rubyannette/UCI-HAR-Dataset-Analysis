## CodeBook for Tidy UCI HAR Dataset

# What is it?
This CodeBook describes the data contained in the output of the run_analysis.R script contained in this repository. The tidy flat text file can be read using data.table to create a data table for further analysis.

tidy_data <- data.table("tidy_data.txt")

The script creates a tidy, condensed version of the University of California Irvine's (UCI's) dataset for Human Activity Recognition (HAR) using smartphones that can be used for further research and analysis. The original UCI HAR Dataset is a public domain dataset built from the recordings of subjects performing activities of daily living (ADL) while carrying a waist-mounted smartphone with embedded inertial sensor (see http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones).

As noted in the above referenced document, the original data comes from experiments that were carried out with a group of 30 volunteers within an age bracket of 19-48 years. Each person performed six activities (walking, walking_upstairs, walking_downstairs, sitting, standing, and laying) wearing a Samsung Galaxy S II smartphone on the waist. Using its embedded accelerometer and gyroscope, 3-axial linear acceleration and 3-axial angular velocity were captured at a constant rate of 50Hz. The experiments were video-recorded to label the data manually.

The sensor signals (accelerometer and gyroscope) were pre-processed by applying noise filters and then sampled in fixed-width sliding windows of 2.56 sec and 50% overlap (128 readings/window). The sensor acceleration signal, which has gravitational and body motion components, was separated using a Butterworth low-pass filter into body acceleration and gravity. The gravitational force was assumed to have only low frequency components, so a filter with a 0.3 Hz cutoff frequency was used. From each window, a vector of features was obtained by calculating variables from the time and frequency domain.

The script generates a combined subset of the original data by extracting the mean and standard deviation features for each of the 33 processed signals, for a total of 66 features (out of the 561 available features from the original feature vector). This combined subset contains 10299 observations of 68 variables, with activity and subject appended to the 66 features.

The combined subset is further reduced by calculating the mean of the observations by activity and subject pair to generate 180 observations (6 activities * 30 subjects) of the same 68 variables. This dataset is tidied to generate a narrow and lean dataset containing 11880 observations with 4 variables each and is saved as a text file in the current working directory with the name tidy_data.txt

##Variable name cleanup

As part of the tidying process the variable names are cleaned up using the following transformations.

#1.leading t or f is based on time or frequency measurements.
# Body = related to body movement.
# Gravity = acceleration of gravity
# Acc = accelerometer measurement
# Gyro = gyroscopic measurements
# Jerk = sudden movement acceleration
# Mag = magnitude of movement
# mean and SD are calculated for each subject for each activity for each mean and 
# SD measurements. The units given are g's for the accelerometer and rad/sec for the gyro 
# and g/sec and rad/sec/sec for the corresponding jerks.

## activity
The activity name with the following possible values.

    'laying',
    'sitting',
    'standing',
    'walking',
    'walking_downstairs'
    'walking_upstairs'
mean

The mean of the measurements.