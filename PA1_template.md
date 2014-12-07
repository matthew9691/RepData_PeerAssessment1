## Reproducible Research: Peer Assessment 1

Submitted as part of the December 2014 Coursera session.

### Loading and preprocessing the data
Data is extracted assuming the repository has been cloned to local computer and has been set as the current working directory.


```r
wd <- "~/repos/RepData_PeerAssessment1"  # modify as required
setwd(wd) 
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

![plot of chunk plot1-total-steps-per-day](figure/plot1-total-steps-per-day-1.png) 

```r
mean_steps <- mean(steps$steps)
median_steps <- median(steps$steps)
```

The mean number of steps per day is 1.076619 &times; 10<sup>4</sup> and the median number steps per day is 10765.

### What is the average daily activity pattern?

```r
data$time_index <- c(1:288)/12 # assign each time interval its sequential number per day. Divide by 12 to get the integer numbers as hours.
steps <- aggregate(steps ~ time_index, data=data, mean)

plot(steps$steps ~ steps$time_index,
     xlab = "Hour of each day",
     ylab = "Number of steps in 5 minute intervals",
     main = "Average number of steps during the day: October-November 2012", 
     type = "l")
```

![plot of chunk plot2-steps-by-time](figure/plot2-steps-by-time-1.png) 




### Imputing missing values



### Are there differences in activity patterns between weekdays and weekends?
