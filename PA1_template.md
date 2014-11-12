# Reproducible Research: Peer Assessment 1



## Loading and preprocessing the data
The data was taken from the forked repository.

```r
unzip("activity.zip")
activity <- read.csv("activity.csv", as.is=TRUE)
activity$date <- as.Date(activity$date)
```



## What is mean total number of steps taken per day?

```r
totalStepsPerDay <- aggregate(activity$steps ~ activity$date, FUN=sum)
colnames(totalStepsPerDay) = c("Date", "Steps")
xlabel <- "Total number of steps taken each day"
hist(totalStepsPerDay$Steps, main = NA, xlab = xlabel)
```

![](PA1_template_files/figure-html/unnamed-chunk-2-1.png) 

```r
meanTotalStepsPerDay <- mean(totalStepsPerDay$Steps)
medianTotalStepsPerDay <- median(totalStepsPerDay$Steps)
```
The mean of total number of steps taken per day is: 10766.19

The median of total number of steps taken per day is: 10765




## What is the average daily activity pattern?



## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
