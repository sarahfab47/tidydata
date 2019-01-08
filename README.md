# tidydata
#Coursera Programming Assignment
#Sarah Jane Fabito

#Unizipping the downloaded zipped file
unzip(zipfile="./data/mydata.zip",exdir="./data")

#Set the correct directory
setwd("C:/Users/sjfabito/Desktop/Coursera/data")

#Prepare the data sets
xtrain=read.table("C:/Users/sjfabito/Desktop/Coursera/data/X_train.txt", header=FALSE)
ytrain=read.table("C:/Users/sjfabito/Desktop/Coursera/data/Y_train.txt", header=FALSE)
subject_train=read.table("C:/Users/sjfabito/Desktop/Coursera/data/subject_train.txt", header=FALSE)

xtest=read.table("C:/Users/sjfabito/Desktop/Coursera/data/X_test.txt", header=FALSE)
ytest=read.table("C:/Users/sjfabito/Desktop/Coursera/data/Y_test.txt", header=FALSE)
subject_test=read.table("C:/Users/sjfabito/Desktop/Coursera/data/subject_test.txt", header=FALSE)

features=read.table("C:/Users/sjfabito/Desktop/Coursera/data/features.txt", header=FALSE)
activityLabels=read.table("C:/Users/sjfabito/Desktop/Coursera/data/activity_labels.txt", header=FALSE)

#Activity names
colnames(xtrain) = features[,2]
colnames(ytrain) = "activityId"
colnames(subject_train) = "subjectId"

colnames(xtest) = features[,2]
colnames(ytest) = "activityId"
colnames(subject_test) = "subjectId"

colnames(activityLabels) <- c('activityId','activityType')

#MERGE
merge_train = cbind(ytrain, subject_train, xtrain)
merge_test = cbind(ytest, subject_test, xtest)

merge_all = rbind(merge_train, merge_test)

colNames = colnames(merge_all)
mean_sd = (grepl("activityId" , colNames) | grepl("subjectId" , colNames) | grepl("mean.." , colNames) | grepl("std.." , colNames))

mean_sd_subset <- merge_all[ , mean_sd == TRUE]
mean_sd_subsetnames = merge(mean_sd_subset, activityLabels, by='activityId', all.x=TRUE)

tidy_data <- aggregate(. ~subjectId + activityId, mean_sd_subsetnames, mean)
tidy_data <- tidy_data[order(tidy_data$subjectId, tidy_data$activityId),]

#Export final tidy dataset
write.table(tidy_data, "tidy_data.txt", row.name=FALSE)
