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
paste('Mean - total number of steps taken per day : ', mean(q1HistoData$x))
```

```
## [1] "Mean - total number of steps taken per day :  10766.1886792453"
```

Median - total number of steps taken per day: 

```r
paste('Median - total number of steps taken per day : ', median(q1HistoData$x))
```

```
## [1] "Median - total number of steps taken per day :  10765"
```


## What is the average daily activity pattern?

![](PA1_template_files/figure-html/unnamed-chunk-5-1.png) 

Below is the calculation that work out the 5-minute interval that, on average, contains the maximum number of steps:

In 5-minute interval

```r
paste('Maximum steps interval = ', Q2Data[Q2Data$x == max(Q2Data$x), "Interval"])
```

```
## [1] "Maximum steps interval =  835"
```

In equivalent time in the day:

```r
maxMinuteInt <- Q2Data[Q2Data$x == max(Q2Data$x), "Interval"]
paste('Maximum stpes interval in Time = ', maxMinuteInt %/% 60, ':' , maxMinuteInt %% 60)
```

```
## [1] "Maximum stpes interval in Time =  13 : 55"
```



## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
