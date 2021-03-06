# Pattern nel tempo
## A barre / barplot()
I dati temporali possono essere categorizzati o continui. Il grafico a barre rappresenta 
 - Dati non continui


### Condizioni

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

## A barre in pila / barplot()
Dati non continui
No serie temporali

### Nomi di colonna
Se i nomi di colonna sono numeri R aggiunge un X davati, 2000 diventa X2000. Bisogna usare la funzione `name(nome della variabile) <- c("2000")`

### Data frame e matrici
2000    2001    2002    2003    2004
25      50.0    50.5    44.5    53.5
24      31.0    26.0    30.5    38.0
22      23.5    25.5    29.5    32.0

nome_data_matrice<-as.matrix(nome_data_frame)

### Caratteri del barplot

barplot(hot_dog_matrix, border=NA, space=0.25, ylim=c(0, 200), xlab="Year", ylab="Hot dogs and buns(HDBs) eaten", main="Hot Dog Eating Contest Result, 1980-2010")

`barplot` fai un grafico a barre
`hot_dog_matrix` usa la variabile
`border=NA` nessun bordo
`space=0.25` spazio tra le barre 
`ylim=c(0, 200)` limite min e max dell'asse y
`xlab="Year"` etichetta asse x
`ylab="Hot dogs and buns(HDBs) eaten"` etichetta asse y
`main="Hot Dog Eating Contest Result, 1980-2010"` titolo del grafico

## Punti / plot( type="p")
Scatterplot
Dati non temporali
### Limita le righe
`vettore[1:5,]` piglia le prime 5 righe del vettore

### Plotta la colonna
`plot(vettore$colonna)` plotta la colonna del vettore

### Plotta linee verticali (high density)

    plot(subscribers$Subscribers, type="p", ylim=c(0, 30000))

    plot(subscribers$Subscribers, type="h", ylim=c(0, 30000))

`type="p"` plotta punti
`type="h"` plotta punti e linee verticali
`type="l"` plotta linee


### Aggiungi punti
`points(subscribers$Subscribers, pch=20, col="red")` aggiunge punti sopra le linee

## Linea / plot( type="l")

E' importante l'ordine delle coordinate dei punti (nodi)

> plot(population`$`Year, population`$`Population)

Plotta gli anni sulla x e la popolazione sulla y

> plot(population`$`Population, population`$`Year)

Plotta la popolazione sulla x e gli anni sulla y

## Grafico a gradini / plot( type="s")
Per es un prezzo che resta fermo per anni e sale di colpo da un giorno all'altro

## LOESS / scatter.smooth()

> scatter.smooth(1:length(unemployment`$`Value), unemployment`$`Value)

`scatter.smooth` traccia una linea di tendenza curva

> scatter.smooth(1:length(unemployment`$`Value), unemployment`$`Value,
> ylim=c(0,11), degree=2, col="#CCCCCC", span=0.5)

`ylim` limita i valori y tra 0 e 11
`degree` controlla i gradi della curva polinomiale
`span` controlla la morbidità della curva, 0.1 linea spezzata a >10 linea con curvatura morbida

# Visualizzare proporzioni
I dati di proporzione possono essere raggruppati in categorie, sottocategorie e popolazione

## Parti del tutto
La proporzione più semplice: hai una serie di proporzioni che sommate danno 1 o una serie di percentuali che sommate danno 100. Viene mostrato il controbuto della singola parte all'interno del tutto

### Grafici a torta / pie()

 1. Partendo da ore 12 metti le parti maggiori e via via quelle minori
 2. Colora le parti maggiori con colori più scuri
 3. Evitare colori brillanti

### Grafici a ciambella / pie()
Avendo un buco questi grafici vengono interpretati solo in base alla linghezza dell'arco e non all'angolo. Sono efficaci con poche categorie.

### Barre in pila

### Tree map / map.market()
Installare e avviare la libreria portfolio

     id  views comments                  category
1  5019 148896       28    Artistic Visualization
2  1416  81374       26             Visualization
3  1416  81374       26                  Featured
4  3485  80819       37                  Featured
5  3485  80819       37                   Mapping
6  3485  80819       37              Data Sources
7   500  76495       10 Statistical Visualization
8   500  76495       10                   Mapping
9   500  76495       10     Network Visualization
10 4092  66650       70        Ugly Visualization

> map.market(id=data`$`id, area=posts`$`views, group=posts`$`category,
> color=posts`$`comments, main="Flowing data Map")


`id` indica univocamente un dato su ogni riga
`area` indica la colonna da usare come area del rettangolo
`group` indica la colonna da usare per la gerachia dei dati
`comments` indica il valore da passare alla colorazione più o meno intensa (opzionale)

## Proporzioni nel tempo
### Linee in pila (staked plot) / plot.stacked()
### Stream graph / plot.stream()
http://www.r-bloggers.com/data-mountains-and-streams-stacked-area-plots-in-r/
Arguments are similar for both functions regarding the input of x and y series and polygon attributes (fill color, border color, border line width). The stream plot also requires that the degree of meandering for the baseline be defined by the arguments frac.rand and spar; frac.rand, controls the meander amplitude (uniform random numbers added to baseline as a fraction of the total y range) and spar controls the amount of smoothing (as fit by the function smooth.spline). 

Oppure qui : http://my.safaribooksonline.com/book/programming/r/9781449363086/4dot-line-graphs/recipe_line_graph_stacked_area_html

 year            category expenditure sex
1 2008                Food        6443   1
2 2008 Alcoholic Beverages         444   1
3 2008             Housing       17109   1
4 2008             Apparel        1801   1
5 2008      Transportation        8604   1

> ggplot(expenditures, aes(x=year, y=expenditure, fill=category)) +
+     geom_area(colour="black", size=.2, alpha=.4) +
+     scale_fill_brewer(palette="Blues", breaks=rev(levels(expenditures$category)))

# Visualizzare relazioni
## Correlazioni / plot()
`plot(coordinata x, coordinata y)` disegna uno scatterplot

> Togliere una riga crime2 <- crime[crime$state != "District of
> Columbia",] si crea un altro vettore e dalla colonna state di toglie
> District of Columbia

    > plot(crime2$murder, crime2$burglary, xlim=c(0, 10), ylim=c(0, 1200))
plotta lo scatter
    > scatter.smooth(crime2$murder, crime2$burglary, xlim=c(0, 10), ylim=c(0, 1200))

Plotta la linea di tendenza

###  Plottare tutte le variabili
Confronta tutte le combinazioni di variabili possibili e plotta una matrice di scatterplot

plot(crime2[,2:9]) fa partire il confronto dalla seconda colonna perché la prima contiene solo il nome dello stato

`pairs(crime2[,2:9], panel=panel.smooth)` inserisce le linee di tendenza nella matrice degli scatterplot

## Bolle / symbols(x, y, circles=colonna)
Il grafico a bolle è uno scatterplot al quale è possibile assegnare un valore all'area del cerchio. Quindi è possibile esplorare 3 variabili. La dimensioen delle bolle deve essere assegnata all'area e non al raggio o al diametro.

> symbols(crime`$`murder, crime`$`burglary, circles=crime`$`population)
> radius<-sqrt(crime`$`population/pi)
> symbols(crime`$`murder, crime`$`burglary, circles=radius)

La popolazione era proporzionale al raggio del cerchio. Bisogna fare in modo che la popolazione sia proporzionale all'area.

> symbols(crime`$`murder, crime`$`burglary, circles=radius, inches="0.35",
> fg="white", bg="red", xlab="Murder", ylab="Burglary Rate"

`inches="0.35`" dimensione massima del raggio
`fg="white"` colore circonferenza
`bg="red"` colore cerchio

> symbols(crime`$`murder, crim`e$`burglary, squares=sqrt(crime`$`population),
> inches=0.5)

`squares(`) plotta quadrati

> plot(pisa`$`PPS, pisa$pisa.2012)
> text(pisa`$`PPS, pisa$pisa.2012, pisa`$`country, cex=0.5)

`text()` mette etichetta a bolle e scatterplot
`cex=` dà dimensione al testo

## Distribuzione / hist() /density()

La distribuzione può essere rappresentata da una linea o da un istogramma. Sugli assi ci sono delle misure continue. L'asse delle ascisse la frequenza, l'asse delle ordinate può non rappresentare nulla

## Bar plot orizzontali
Leggi il file


```r
x <- read.csv("/Users/sergiomac/Documents/Documenti da applicazioni/Github/Dataset/governo_renzi_20140304.csv", 
    sep = ";")
```


Trasforma in matrice


```r
xmatrice <- as.matrix(x)
```


Plotta la matrice


```r
barplot(xmatrice, horiz = TRUE, main = "Governo", names.arg = c("Altro", "Professioni intellettuali"), 
    xlim = range(0:60))
```

![plot of chunk unnamed-chunk-3](figure/unnamed-chunk-3.png) 


