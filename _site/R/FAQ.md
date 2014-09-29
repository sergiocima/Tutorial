FAQ
========================================================

# Filtrare escludendo righe senza dati


```r
birth <- read.csv("/Users/sergiomac/Documents/Formazione/Visualize this/code-n-data/ch06/data/birth-rate.csv")
birth[1:5, ]
```

```
##                Country X1960 X1961 X1962 X1963 X1964 X1965 X1966 X1967
## 1                Aruba 36.40 35.18 33.86 32.46 30.99 29.51 28.07 26.72
## 2          Afghanistan 52.20 52.21 52.21 52.20 52.19 52.17 52.13 52.08
## 3               Angola 54.43 54.39 54.32 54.20 54.04 53.84 53.59 53.30
## 4              Albania 40.89 40.31 39.60 38.79 37.91 37.01 36.11 35.24
## 5 Netherlands Antilles 32.32 30.99 29.62 28.23 26.85 25.52 24.28 23.17
##   X1968 X1969 X1970 X1971 X1972 X1973 X1974 X1975 X1976 X1977 X1978 X1979
## 1 25.52 24.49 23.67 23.06 22.63 22.34 22.18 22.11 22.12 22.19 22.28 22.36
## 2 52.01 51.92 51.82 51.69 51.55 51.40 51.24 51.09 50.97 50.87 50.81 50.79
## 3 52.98 52.67 52.38 52.14 51.97 51.88 51.86 51.92 52.03 52.17 52.31 52.44
## 4 34.42 33.66 32.95 32.28 31.63 30.98 30.34 29.72 29.14 28.61 28.14 27.74
## 5 22.23 21.47 20.93 20.61 20.48 20.52 20.66 20.86 21.05 21.19 21.24 21.18
##   X1980 X1981 X1982 X1983 X1984 X1985 X1986 X1987 X1988 X1989 X1990 X1991
## 1 22.41 22.39 22.31 22.17 21.96 21.67 21.30 20.87 20.39 19.89 19.36 18.84
## 2 50.80 50.83 50.89 50.95 51.02 51.08 51.16 51.24 51.33 51.42 51.51 51.60
## 3 52.55 52.64 52.72 52.79 52.84 52.88 52.91 52.92 52.90 52.85 52.72 52.49
## 4 27.40 27.11 26.87 26.64 26.42 26.17 25.89 25.58 25.22 24.80 24.32 23.79
## 5 21.01 20.75 20.44 20.14 19.86 19.64 19.51 19.48 19.51 19.59 19.65 19.64
##   X1992 X1993 X1994 X1995 X1996 X1997 X1998 X1999 X2000 X2001 X2002 X2003
## 1 18.33 17.84 17.37 16.91 16.46 15.99 15.52 15.02 14.53 14.04 13.58 13.15
## 2 51.69 51.76 51.80 51.80 51.75 51.65 51.47 51.23 50.90 50.49 49.98 49.42
## 3 52.14 51.68 51.12 50.52 49.94 49.43 49.00 48.66 48.35 48.01 47.55 46.94
## 4 23.20 22.56 21.89 21.16 20.36 19.51 18.62 17.71 16.85 16.08 15.44 14.96
## 5 19.49 19.19 18.73 18.16 17.52 16.88 16.30 15.81 15.41 15.10 14.82 14.56
##   X2004 X2005 X2006 X2007 X2008
## 1 12.77 12.44 12.16 11.92 11.72
## 2 48.80 48.18 47.58 47.02 46.54
## 3 46.18 45.33 44.44 43.61 42.88
## 4 14.64 14.48 14.46 14.53 14.65
## 5 14.31 14.05 13.79 13.53 13.28
```

```r
birth2008 <- birth$X2008[!is.na(birth$X2008)]
```


L'istruzione è: prendi la colonna del 2088 ed escludi le righe in cui la cella è NA (nessuan dato).

Dato prima del filtro


```r
birth$X2008[1:20]
```

```
##  [1] 11.716 46.538 42.875 14.649 13.281 26.324 14.004 17.269 15.299     NA
## [11]     NA 13.800  9.326 17.800 34.465 11.672 39.395 47.212 21.431 10.194
```


Dato dopo il filtro


```r
birth2008[1:20]
```

```
##  [1] 11.716 46.538 42.875 14.649 13.281 26.324 14.004 17.269 15.299 13.800
## [11]  9.326 17.800 34.465 11.672 39.395 47.212 21.431 10.194 18.017 16.704
```


# Condizioni
Condizioni

    barplot(hotdogs$Dogs.eaten, names.arg = hotdogs$Year, col=fill_colors, border="NA", xlab="Year", ylab="Hot dogs and buns (HDB) eaten")

Serve per colorare le barre di un grafico il cui dato è “United States”
  
  
    fill_colors <- c()
    for ( i in 1:length(hotdogs$New.record) ) { 
      if (hotdogs$New.record[i] == 1) {
      	fill_colors <- c(fill_colors, "#821122")
    	} else { fill_colors <- c(fill_colors, "#cccccc")
    	}
    }

Serve per colorare le barre di un grafico il cui dato è “1”

# Import dati Banca mondiale

library(WDI)

Plotta da WB (http://www.r-chart.com/2010/06/plotting-world-bank-data-with-r.html, http://www.r-bloggers.com/world-bank-api-r-package-available/)

> DF <- WDI(country=c("IT","FR","DE"), indicator="NY.GDP.MKTP.KD.ZG",
> start=1990, end=2008) ggplot(DF, aes(year, NY.GDP.MKTP.KD.ZG,
> color=country))+geom_line(stat="identity")+theme_bw()+xlab("Year")+labs(title="Annual GDP Growth rate (%)")+ylab("")

Plotta il grafico del GPD per i paesi selezionati


> WDI(country = "IT", indicator = "AG.LND.IRIG.AG.ZS",
> +     start = 2005, end = 2011, extra = FALSE, cache = NULL)

Questo comando scarica i dati di un paese per l'indicatore scelto. Gli indicatori si trovano qui http://data.worldbank.org/indicator

# Plottare in plot.ly
Plot.ly
http://plot.ly/api/arduino/docs/bar-charts

# Import Twitter
http://cran.r-project.org/web/packages/streamR/streamR.pdf

> library(streamR)
> requestURL <- "https://api.twitter.com/oauth/request_token"
> accessURL <- "http://api.twitter.com/oauth/access_token"
> authURL <- "http://api.twitter.com/oauth/authorize"
> consumerKey <- "ScetmhLpxf4Xz35QGrASg"
> consumerSecret <- "abcd1234EFGH5678ijkl0987MNOP6543qrst21"
> Cred <- OAuthFactory$new(consumerKey=consumerKey, consumerSecret=consumerSecret, requestURL=requestURL, accessURL=accessURL, authURL=authURL)

# You can also embed plots, for example:


```r
plot(cars)
```

![plot of chunk unnamed-chunk-4](figure/unnamed-chunk-4.png) 


