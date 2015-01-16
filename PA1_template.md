# Reproducible Research: Peer Assessment 1


## Loading and preprocessing the data


```r
# read the raw data into data frame objec rawData
rawData <- read.csv(unz("activity.zip", "activity.csv"))
# filter out NAs
filteredData <- rawData[complete.cases(rawData),]
# Aggregate steps, sum by date and store in q1HistoData
q1HistoData <- aggregate(filteredData$steps, by=list(Date=filteredData$date), FUN=sum)
Q2Data <- aggregate(filteredData$steps, by=list(Interval=filteredData$interval), FUN=mean)
```



## What is mean total number of steps taken per day?

Below is the histogram for sum of steps by Date

![](PA1_template_files/figure-html/unnamed-chunk-2-1.png) 

Mean - total number of steps taken per day : 

```r
mean(q1HistoData$x)
```

```
## [1] 10766.19
```

Median - total number of steps taken per day: 

```r
median(q1HistoData$x)
```

```
## [1] 10765
```


## What is the average daily activity pattern?



## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
