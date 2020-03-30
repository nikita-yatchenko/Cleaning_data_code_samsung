#### Set Up Libraries #####
library(dplyr)
library(data.table)

#### Access Files #####

# Feature names
dir2features <- "/Users/nyatchen/Desktop/R Scripts/Coursera_R/ProgrammingAssignment4/UCI HAR Dataset/"
feature_names <- read.table(paste0(dir2features,'features.txt'))$V2
activity_labels <- read.table(paste0(dir2features,'activity_labels.txt'))$V2

# Train data
dir2train <- "/Users/nyatchen/Desktop/R Scripts/Coursera_R/ProgrammingAssignment4/UCI HAR Dataset/train/"
subject_train <- read.table(paste0(dir2train,'subject_train.txt'), col.names = 'subject_id')
X_train <- read.table(paste0(dir2train,'X_train.txt'))
names(X_train) = feature_names
y_train <- read.table(paste0(dir2train,'y_train.txt'), col.names = 'activity')
train_data <- cbind(subject_train, X_train, y_train)

# Test data
dir2test <- "/Users/nyatchen/Desktop/R Scripts/Coursera_R/ProgrammingAssignment4/UCI HAR Dataset/test/"
subject_test <- read.table(paste0(dir2test,'subject_test.txt'), col.names = 'subject_id')
X_test <- read.table(paste0(dir2test,'X_test.txt'))
names(X_test) = feature_names
y_test <- read.table(paste0(dir2test,'y_test.txt'), col.names = 'activity')
test_data <- cbind(subject_test, X_test, y_test)

# Combining Data
combined_data <- rbind(train_data, test_data)

# Extracting data with mean and std only
feature_set <- grep('(mean\\(\\))|(std\\(\\))', names(combined_data))
extract_data <- cbind(subject_id=combined_data$subject_id, combined_data[,feature_set], activity=combined_data$activity)
extract_data$subject_id <- as.factor(extract_data$subject_id)

# Naming the activities in the data set
extract_data$activity <- as.factor(extract_data$activity)
levels(extract_data$activity) = activity_labels

# Labeling data with descriptive variable names
extract_names <- names(extract_data)
extract_names <- sub('Acc', 'Accelerometer', extract_names)
extract_names <- sub('Gyro', 'Gyroscope', extract_names)
extract_names <- sub('Mag', 'Magnitude', extract_names)
extract_names <- sub('^t', 'time', extract_names)
extract_names <- sub('^f', 'frequency', extract_names)
extract_names <- sub('BodyBody', 'Body', extract_names)
extract_names <- sub('\\(\\)', '', extract_names)
extract_names <- sub('std', 'StandardDeviation', extract_names)
names(extract_data) <- extract_names

# Creating average of each variable for each activity and each subject
avg_data <- tbl_df(copy(extract_data)) %>% group_by(activity, subject_id) %>% summarise_all(mean) %>% arrange(subject_id)
write.table(avg_data, file = 'tidy_summarized_data.txt', row.name=FALSE)