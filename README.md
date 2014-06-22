projectweek3
============
#setting working directory. Here are all the necesary files to read
setwd("/Users/carolinesielfeld/Documents/Caroline/Cursos Online/Cursos Coursera/3. Getting and Cleaning Data/Week 3/Project/UCI HAR Dataset")
#reading files of train and test
trainset <- read.table("X_train.txt")
trainact <- read.table("y_train.txt")
trainsubj <- read.table("subject_train.txt")
testset <- read.table("X_test.txt")
testsubj <- read.table("subject_test.txt")
testact <- read.table("y_test.txt")
trainact <- read.table("y_train.txt")
#combinig tables so that they include nr of subject, of activity and observations in all rows
datostest <- cbind(testsubj,testact,testset)
datostrain <- cbind(trainsubj,trainact,trainset)

#putting names of the first two columns, that are subjects and avticity

colnames(datostest)[1:2] <- c("subject", "activity_type")
colnames(datostrain)[1:2] <- c("subject", "activity_type")
this file includes de code and description of what each step does (with #)

#merging both info tables (test and train)

mergeddata <- merge(datostest,datostrain, all=T)

#reading the features info that has the info of names o variables of observations

features <- read.table("features.txt")
features2 <- as.character(features$V2)

#putting the names of variables instead of "V1", "V2", etc.

colnames(mergeddata)[3:563] <- features2

#changing the numbers of activties for their real names

mergeddata$activity_type <- factor(mergeddata$activity_type, levels = c(1,2,3,4,5,6), labels = c("WALKING", "WALKING_UPSTAIRS", "WALKING_DOWNSTAIRS", "SITTING", "STANDING", "LAYING"))

#cleaning data: eliminating the columns that are NOT mean or std

mergeddata[9:42] <- list(NULL)
names(mergeddata)
mergeddata[15:48] <- list(NULL)
mergeddata[21:54] <- list(NULL)
mergeddata[27:60] <- list(NULL)
mergeddata[33:66] <- list(NULL)
mergeddata[35:58] <- list(NULL)
mergeddata[37:47] <- list(NULL)
mergeddata[39:49] <- list(NULL)
mergeddata[41:51] <- list(NULL)
mergeddata[47:68] <- list(NULL)
mergeddata[50:97] <- list(NULL)
mergeddata[56:77] <- list(NULL)
mergeddata[59:106] <- list(NULL)
mergeddata[65:86] <- list(NULL)
mergeddata[69:105] <- list(NULL)
mergeddata[68:78] <- list(NULL)
mergeddata[71:82] <- list(NULL)
mergeddata[72:73] <- list(NULL)
mergeddata[74:81] <- list(NULL)
mergeddata[75:76] <- list(NULL)
mergeddata[77:84] <- list(NULL)
mergeddata[78:79] <- list(NULL)
#now mergeddata has only info of means and stds
