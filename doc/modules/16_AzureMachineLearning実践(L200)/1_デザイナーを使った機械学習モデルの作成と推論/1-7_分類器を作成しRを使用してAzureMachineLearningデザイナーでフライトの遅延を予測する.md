###### Azure Machine Learning 実践 (L200) > 1. デザイナーを使った機械学習モデルの作成と推論 > 1

# 7. 分類器を作成し、R を使用して Azure Machine Learning デザイナーでフライトの遅延を予測する

## ヒント

### Flight Delays Data 用の R スクリプト

```r
azureml_main <- function(dataframe1, dataframe2){
  print("R script run.")
  dataframe1$CRSDepTime = dataframe1$CRSDepTime %/% 100
  return(list(dataset1=dataframe1, dataset2=dataframe2))
}
```

### Weather Dataset 用の R スクリプト

```r
azureml_main <- function(dataframe1, dataframe2){
  print("R script run.")

  Year <- dataframe1$Year
  Month <- dataframe1$Month
  Day <- dataframe1$Day
  Time <- dataframe1$Time
  Hour <- ceiling(Time/100)
  Timezone <- dataframe1$TimeZone
  
  n <- nrow(dataframe1)
  
  fulldate <- lapply(1:n, function(i) as.POSIXlt(sprintf("%4d-%02d-%02d %02d:00:00", Year[i], Month[i], Day[i], Hour[i]), tz = "UTC") + Timezone[i] * 3600)
  adjustdate <- do.call(c,fulldate)
  
  AdjustedMonth <- as.POSIXlt(adjustdate)$mon + 1
  AdjustedDay   <- as.POSIXlt(adjustdate)$mday
  AdjustedHour  <- as.POSIXlt(adjustdate)$hour

  AirportID <- dataframe1$AirportID
  Weather <- dataframe1[,7:14]
  
  out_dataframe <- data.frame(cbind(Year, AdjustedMonth, AdjustedDay, AirportID, AdjustedHour, Timezone, Weather))

  return(list(dataset1=out_dataframe, dataset2=dataframe2))
}
```


---


## ブループリント

<details>
<summary>ネタバレ注意</summary>
<img src="https://github.com/k14i-Azure/MachineLearningDesigner_ja-jp/raw/master/articles/samples/media/r-script-flight-delay-prediction/pipeline-graph.png">
</details>
