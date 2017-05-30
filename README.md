## ML_-and_DataScience_WWC
Session for Women Who Code for using R for ML in Data Science.
    
    Project1_linmod.R
    irinamahmudjanova

    Sun Apr 9 21:29:32 2017

    bike <- read.csv('bikeshare.csv')
    print(head(bike))
    ##              datetime season holiday workingday weather temp  atemp
    ## 1 2011-01-01 00:00:00      1       0          0       1 9.84 14.395
    ## 2 2011-01-01 01:00:00      1       0          0       1 9.02 13.635
    ## 3 2011-01-01 02:00:00      1       0          0       1 9.02 13.635
    ## 4 2011-01-01 03:00:00      1       0          0       1 9.84 14.395
    ## 5 2011-01-01 04:00:00      1       0          0       1 9.84 14.395
    ## 6 2011-01-01 05:00:00      1       0          0       2 9.84 12.880
    ##   humidity windspeed casual registered count
    ## 1       81    0.0000      3         13    16
    ## 2       80    0.0000      8         32    40
    ## 3       80    0.0000      5         27    32
    ## 4       75    0.0000      3         10    13
    ## 5       75    0.0000      0          1     1
    ## 6       75    6.0032      0          1     1
    # EDA

library(ggplot2)

ggplot(bike, aes(temp, count)) + geom_point(alpha= 0.5, aes(color= temp)) + theme_bw()


# convert time to POSIXct()
bike$datetime <- as.POSIXct(bike$datetime)

pl <- ggplot(bike, aes(datetime, count)) + geom_point(aes(color=temp), alpha=0.5)
print(pl)


pl + scale_color_continuous(low = '#55D8CE', high='#FF6E2E' ) + theme_bw()


#e can look at the correlation factor between tempeture and count
cor(bike[,c('temp','count')])
##            temp     count
## temp  1.0000000 0.3944536
## count 0.3944536 1.0000000
ggplot(bike, aes(factor(season), count)) + geom_boxplot(aes(color=factor(season)))+theme_bw()
