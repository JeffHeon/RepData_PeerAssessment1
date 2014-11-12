---
title: "Reproducible Research: Peer Assessment 1"
output: 
  html_document:
    keep_md: true
---



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

![plot of chunk unnamed-chunk-2](figure/unnamed-chunk-2-1.png) 

```r
meanTotalStepsPerDay <- mean(totalStepsPerDay$Steps)
medianTotalStepsPerDay <- median(totalStepsPerDay$Steps)
```
The mean of total number of steps taken per day is: 10766.19

The median of total number of steps taken per day is: 10765




## What is the average daily activity pattern?

```r
# average number of steps taken per interval, averaged across all days
avgStepsPerInterval <- aggregate(activity$steps ~ activity$interval, FUN=mean)
colnames(avgStepsPerInterval) = c("interval", "steps")
plot(avgStepsPerInterval$interval, avgStepsPerInterval$steps, type = "l")
```

![plot of chunk unnamed-chunk-3](figure/unnamed-chunk-3-1.png) 


## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
