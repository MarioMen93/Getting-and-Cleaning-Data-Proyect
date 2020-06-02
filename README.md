# Getting-and-Cleaning-Data-Proyect

run_analysis

Necesary packages library(data.table) library(dplyr)

Getting feature and activity labels data with read.table()

Getting data related with train set with read.table()

Getting data related with test set with read.table()

Merging train and test sets with rbind

Naming columns from featureNames[2] and using transpose

Creating the complete data adding properly column names

Extracts only the measurements on the mean and standard deviation for each measurement

Uses descriptive activity names to name the activities in the data set

extractedData$Activity <- as.character(extractedData$Activity) for (i in 1:6){ extractedData$Activity[extractedData$Activity == i] <- as.character(activityLabels[i,2]) } extractedData$Activity <- as.factor(extractedData$Activity)

Appropriately labels the data set with descriptive variable names.

From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject.

extractedData$Subject <- as.factor(extractedData$Subject) extractedData <- data.table(extractedData)

Use of write.table

tidyData <- aggregate(. ~Subject + Activity, extractedData, mean) tidyData <- tidyData[order(tidyData$Subject,tidyData$Activity),] write.table(tidyData, file = "Tidy.txt", row.names = FALSE)
