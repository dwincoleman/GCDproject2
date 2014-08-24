GCDproject2
===========
This project provides a tidy dataset extracted from the experiment reported  [here](http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones).

To see the dataset **it should be read into R [preferably into rstudio]** with read.table, using row.names=FALSE, header =TRUE
Otherwise it may look more untidy than it is - don't try excel, for example!

The R code works as described in comments therein, i.e.


**This script assumes the working directory is the UCI HAR dataset**

### Load the train and test data
xtrain <- read.table("train/X_train.txt")

ytrain <- read.table("train/y_train.txt")

xtest <- read.table("test/X_test.txt")

ytest <- read.table("test/y_test.txt")

testsubs <- read.table("test/subject_test.txt")

trainsubs <- read.table("train/subject_train.txt")


### Merge data, with training first
data1 <- rbind(xtrain,xtest)

subjects <- rbind(trainsubs,testsubs)

actions <- rbind(ytrain,ytest)

### Read in activities and features
acts <- read.table("activity_labels.txt")

feats <-read.table("features.txt")

### Use features data to rename columns in data1
cn <-as.character(feats[,2])

colnames(data1) <-cn

### Select columns with names containing 'mean' or 'std'
cols1 <- grep("mean",cn)

cols2 <- grep("std",cn)

cols<-c(cols1,cols2)

### Subset dataframe to desired columns
data2 <- data1[,cols]

###  Recode activity levels to names
library(car)

test <-acts$V2[match(actions$V1,acts$V1)]

### Add columns for subject identifier and activity to data frame, rename them
data3 <-cbind(subjects,test,data2)

names(data3)[1] <- "subject"

names(data3)[2] <- "action"

## data3 is the first tidy dataset required

### Use aggregate to divide up the data for calculating group means
attach(data3)

dataB <- data3[,3:81]

data4 <- aggregate(dataB, by=list(subject,action),mean)

detach(data3)

### Rename columns introduced by aggregate, save second tidy dataset
colnames(data4)[1]<-"subject"

colnames(data4)[2]<-"activity"

write.table(data4,file="tidy2.txt",row.names=FALSE)


## Done!