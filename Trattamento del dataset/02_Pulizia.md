# Pulizia

> I dati di una colonna del foglio di calcolo dovrebbero essere omogenei per categoria (es: elenco città), ma se la compilazione è avvenuta manualmente possono esserci degli errori: Google Refine permette di pulire questi errori velocemente (abbastanza...). 
Dataset: 0100 contractors fp7 W.xls


## Opzioni di modifica
![enter image description here][1]

I menu a tendina di ogni colonna presentano varie opzioni: di filtro, di modifica, di ordinamento, di riconciliazione con fonti esterne di dati
## Filtro di una colonna
![enter image description here][2]

Fare un clic sulla colonna che si vuole editare e scegelire il percorso `Facet>Text facet`. Dopo una elaborazione dei dati proporzionale al numero delle righe e alla variabilità dei dati Refine mostra un blocco a sinistra con un filtro a faccette che indica ogni contenuto del campo e il numero di occorrenze.
## Trasformazioni comuni
![enter image description here][3]

In trasformazioni comuni si possono controllare il Ma/Mi delle parole e il formato (testo, data, numero)
## Normalizzare le informazioni di una colonna
![enter image description here][4]

Creata una faccetta di testo Refine indica le occorrenze di ciascun dato, cliccando su `Cluster` Refine propone un elenco di voci simili che è possibile riunificare sotto a un unico nome, nuovo o preesistente. Un altro percorso per ottenere cluster è: `Modifica celle->Cluster e modifica`
## Cluster
![enter image description here][5]

In `Values in Cluster` si trovano i valori che potrebbero coincidere (calcolati in base a un determinato algoritmo), spuntando la casella `Merge?` si comanda che tutti i valori indicati nel cluster devono essere trasformati nel valori inserito nel campo `New Cell Value`. Si può scegliere il nuovo valore cliccando su uno dei valori del cluster oppure riscrivendolo nella cella del nuovo valore. Altre informazioni sul clustering:
https://github.com/OpenRefine/OpenRefine/wiki/Clustering
## Navigare nel Cluster
![enter image description here][6]

Passare col mouse nel limite inferiore della cella e cliccare sulla scritta `Naviga questo cluster`, qui si possono operare delle modfiche al cluster stesso
## Modificare un Cluster
![enter image description here][7]

E' possibile cambiare anche un singolo componenete del cluster.
## Filtrare e Clusterizzare
![enter image description here][8]

E' possibile anche filtrare con `Filtro testo` e quindi creare dei cluster che contengono le sole parole filtrate, in questo modo Refine risponde più velocemente ai comandi.
## Sostituzione
![enter image description here][9]

Il percorso `Modifica celle->Trasforma` permette di operare trasformazioni su tutta la colonna tramite uso di espressioni regolari in linguaggio JSON o GREL.
## Sostituzione con il GREL
![enter image description here][10]

Un semplice comando GREL è il cerca/sostituisci:

    value.replace("termine da sostituire","termine che sostituisce")

Altre guide qui:
- https://sakai.unc.edu/access/content/group/b45a6f34-de04-4e63-8bb5-131c910306b5/Cleaning%20Data/Cleaning%20Data%20With%20Refine


  [1]: images/Pulizia/media_1390325279287.png
  [2]: images/Pulizia/Schermata_2012-12-17_alle_10.16.32.png
  [3]: images/Pulizia/media_1390325328235.png
  [4]: images/Pulizia/media_1355736343087.png
  [5]: images/Pulizia/media_1390325377203.png
  [6]: images/Pulizia/media_1390325436998.png
  [7]: images/Pulizia/media_1390325462400.png
  [8]: images/Pulizia/media_1390470187522_lg.png
  [9]: images/Pulizia/media_1390325484001.png
  [10]: images/Pulizia/media_1390325500930.png