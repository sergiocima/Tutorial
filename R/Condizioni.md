  

# Tipi di grafico
## A barre
I dati temporali possono essere categorizzati o continui. Il grafico a barre rappresenta 
 - Dati non continui


----------


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

----------

## A barre in pila
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

## Punti
