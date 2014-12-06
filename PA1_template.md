# Reproducible Research: Peer Assessment 1
Submitted as part of the December 2014 Coursera session.

### Loading and preprocessing the data
Data is extracted assuming the repository has been cloned to local computer and has been set as the current working directory.


```r
setwd("~/repos/RepData_PeerAssessment1") # modify as required
data <- read.csv(unzip("activity.zip"))
data$date <- as.Date(data$date)
```


### What is mean total number of steps taken per day?

```r
steps <- aggregate(steps ~ date, data=data, sum)
hist(steps$steps, 
     main = "Histogram of total steps per day",
     xlab = "Total steps per day")
```

![](PA1_template_files/figure-html/unnamed-chunk-2-1.png) 

```r
mean_steps <- mean(steps$steps)
median_steps <- median(steps$steps)
```

The mean number of steps per day is 1.076619\times 10^{4} and the median number steps per day is 10765.

### What is the average daily activity pattern?

```r
time_of_day <- aggregate(steps ~ interval, data=data, mean)
```




### Imputing missing values



### Are there differences in activity patterns between weekdays and weekends?
