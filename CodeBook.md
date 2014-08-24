---
title: "CodeBook.md"
author: "edwin coleman"
date: "24/08/2014"
output: html_document
---

# Getting and cleaning data, project 2

The original data comes fromn an experiment conducted by scientists at University of Genoa, and their somewhat terse description is [here](http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones).

This project takes some of the data from their UCI HAR dataset, about spatial movement of people wearing Samsung devices, and creates a tidy datset giving the means for each of the variables whose names contain 'mean' or 'std', for each activity and subject.

The tidy dataset created has 180 rows (observations) on 81 columns (variables). These variables are as follows. 

1. subject 
  integer in the range [1,30]
  identifies the subject of the observations.  
2. activity
  this is a factor with six levels, coded as
    + 1 WALKING
    + 2 WALKING_UPSTAIRS
    + 3 WALKING_DOWNSTAIRS
    + 4 SITTING
    + 5 STANDING
    + 6 LAYING. 
    
3.
  The remaining variables 3-81 are a subset of the so-called features in the original data set, this whose label contains 'mean' or 'std', viz :
  (this list starts with [1] because subject and activity have been prepended, and two per line)
  
  [1] "tBodyAcc-mean()-X"               "tBodyAcc-mean()-Y"              
 [3] "tBodyAcc-mean()-Z"               "tGravityAcc-mean()-X"           
 [5] "tGravityAcc-mean()-Y"            "tGravityAcc-mean()-Z"           
 [7] "tBodyAccJerk-mean()-X"           "tBodyAccJerk-mean()-Y"          
 [9] "tBodyAccJerk-mean()-Z"           "tBodyGyro-mean()-X"             
[11] "tBodyGyro-mean()-Y"              "tBodyGyro-mean()-Z"             
[13] "tBodyGyroJerk-mean()-X"          "tBodyGyroJerk-mean()-Y"         
[15] "tBodyGyroJerk-mean()-Z"          "tBodyAccMag-mean()"             
[17] "tGravityAccMag-mean()"           "tBodyAccJerkMag-mean()"         
[19] "tBodyGyroMag-mean()"             "tBodyGyroJerkMag-mean()"        
[21] "fBodyAcc-mean()-X"               "fBodyAcc-mean()-Y"              
[23] "fBodyAcc-mean()-Z"               "fBodyAcc-meanFreq()-X"          
[25] "fBodyAcc-meanFreq()-Y"           "fBodyAcc-meanFreq()-Z"          
[27] "fBodyAccJerk-mean()-X"           "fBodyAccJerk-mean()-Y"          
[29] "fBodyAccJerk-mean()-Z"           "fBodyAccJerk-meanFreq()-X"      
[31] "fBodyAccJerk-meanFreq()-Y"       "fBodyAccJerk-meanFreq()-Z"      
[33] "fBodyGyro-mean()-X"              "fBodyGyro-mean()-Y"             
[35] "fBodyGyro-mean()-Z"              "fBodyGyro-meanFreq()-X"         
[37] "fBodyGyro-meanFreq()-Y"          "fBodyGyro-meanFreq()-Z"         
[39] "fBodyAccMag-mean()"              "fBodyAccMag-meanFreq()"         
[41] "fBodyBodyAccJerkMag-mean()"      "fBodyBodyAccJerkMag-meanFreq()" 
[43] "fBodyBodyGyroMag-mean()"         "fBodyBodyGyroMag-meanFreq()"    
[45] "fBodyBodyGyroJerkMag-mean()"     "fBodyBodyGyroJerkMag-meanFreq()"
[47] "tBodyAcc-std()-X"                "tBodyAcc-std()-Y"               
[49] "tBodyAcc-std()-Z"                "tGravityAcc-std()-X"            
[51] "tGravityAcc-std()-Y"             "tGravityAcc-std()-Z"            
[53] "tBodyAccJerk-std()-X"            "tBodyAccJerk-std()-Y"           
[55] "tBodyAccJerk-std()-Z"            "tBodyGyro-std()-X"              
[57] "tBodyGyro-std()-Y"               "tBodyGyro-std()-Z"              
[59] "tBodyGyroJerk-std()-X"           "tBodyGyroJerk-std()-Y"          
[61] "tBodyGyroJerk-std()-Z"           "tBodyAccMag-std()"              
[63] "tGravityAccMag-std()"            "tBodyAccJerkMag-std()"          
[65] "tBodyGyroMag-std()"              "tBodyGyroJerkMag-std()"         
[67] "fBodyAcc-std()-X"                "fBodyAcc-std()-Y"               
[69] "fBodyAcc-std()-Z"                "fBodyAccJerk-std()-X"           
[71] "fBodyAccJerk-std()-Y"            "fBodyAccJerk-std()-Z"           
[73] "fBodyGyro-std()-X"               "fBodyGyro-std()-Y"              
[75] "fBodyGyro-std()-Z"               "fBodyAccMag-std()"              
[77] "fBodyBodyAccJerkMag-std()"       "fBodyBodyGyroMag-std()"         
[79] "fBodyBodyGyroJerkMag-std()"     

They are all numeric variables with values in the range[-1,1]. Some idea of what they mean can be gleaned from the original source [possibly]. Some of them, for example [44], i.e. variable 46 in the dataframe, may not really be means but it's hard to say.