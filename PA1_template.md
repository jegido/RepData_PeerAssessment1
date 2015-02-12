# Reproducible Research: Peer Assessment 1


## Loading and preprocessing the data

1. Load the data

```r
activity <- read.csv(file="activity.csv")
```

2. Process/transform the data 


```r
activity$dat <- as.Date(activity$date)
activity$day <- format(activity$dat,"%d")
```


## What is mean total number of steps taken per day?

For this part of the assignment, you can ignore the missing values in the dataset.

```r
good <- complete.cases(activity)
act1 <- activity[good,]
```

1. Calculate the total number of steps taken per day


```r
res1 <- tapply(act1$steps,act1$day,sum)
```

2. Make a histogram of the total number of steps taken each day

```r
hist(res1,breaks=30,col="grey",xlab="Steps",
    main="Total number of steps taken each day")
```

![](./PA1_template_files/figure-html/unnamed-chunk-3-1.png) 


3. Calculate and report the mean and median of the total number of steps taken per day

```r
st.mean <- round(mean(act1$steps),0)
st.median <- round(median(act1$steps),0)
```

- Mean total steps taken per day : 37
- Median total steps taken per day: 0

## What is the average daily activity pattern?

1. Make a time series plot (i.e. type = "l") of the 5-minute interval (x-axis) and the average number of steps taken, averaged across all days (y-axis)

2. Which 5-minute interval, on average across all the days in the dataset, contains the maximum number of steps?


## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
