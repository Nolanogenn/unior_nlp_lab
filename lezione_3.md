## Librerie

Le librerie offrono funzionalità aggiuntive, e sono indispensabili per lavorare con Python. 
Per poter utilizzare una libreria già esistente c'è bisogno di seguire due passaggi fondamentali:

- **installare** la libreria 
- **importare** la libreria nel codice che stiamo utilizzando

Una terza opportunità è quella di creare proprie librerie, ma in questo corso ci focalizzeremo principalmente su tre librerie già esistenti: **Pandas**, **Json** e **NLTK**.
Delle tre, **json** viene scaricata con Python, per cui può essere sempre importata senza essere installata precedentemente. 

## Installare librerie

Per installare una libreria si utilizza lo strumento **pip**, già utilizzato per installare Jupyter Lab. La procedura da seguire è la seguente:

1. Aprire il menù **Start** e scrivi nella barra della ricerca **cmd**. Aprire **Prompt dei Comandi**
2. Scrivere il comando **pip install** seguito dal nome della libreria che vogliamo isntallare
3. Aspettare che finisca l'operazione
4. Ben fatto!

Prima di proseguire, seguendo le istruzioni installiamo le librerie **pandas** e **nltk**.

**NB: A causa di un bug su windows, prima di poter utilizzare nltk bisogna anche installare la versione 1.19.3 della libreria numpy. si può fare utilizzando il seguente codice:**
***- pip install numpy==1.19.3***

# Importare librerie

Prima di utilizzare una libreria, è necessario *importarla* all'interno del codice che stiamo utilizzando. Il comando da utilizzare è:

```python
import pandas
```

In questo caso abbiamo semplicemente importato la libreria pandas e tutti i comandi a essa legata. Per evitare però di dover scrivere ogni volta *pandas* prima di invocare un comando, si può utilizzare il codice

```python
import pandas as pd
```
Che ci permette di usare l'*alias* pd al posto di *pandas*. Ci sono alcune convenzioni generalmente accettare per quanto riguarda le librerie più utilizate, ad esempio

```python
import pandas as pd
import numpy as np

```
Ma ciò non toglie che è possibile importare una libreria utilizzando un *alias* arbitrario. Questo significa anche che dobbiamo stare attenti agli *alias* scelti!
In questa lezione vedremo i comandi relativi alle due librerie **json** e **pandas** per importare database.
**NB: creare notebook su cui testare i comandi successivi**

# Pandas

Pandas è la libreria generalmente utilizzata per lavorare con i csv. Quando si lavora con Pandas, queste tabelle prendono il nome di *dataframe*.\
Nel file *note_pandas.md* ci sono diversi comandi utili che pandas permette di utilizzare. In questa lezione ne vedremo i principali. \
Scaricare il file *graduate_data_6 città.csv* presente nella cartella principale del corso:
1. Cliccare sul file
2. Cliccare su download
3. Una volta aperto il file testuale, cliccare con il tasto destro e *scaricare come*

Una volta scaricato il file, eseguire il comando seguente da notebook:
```python
import pandas as pd

df = pd.read_csv('path')
```
Dove per *path* si intende il *percorso del file che vogliamo caricare **relativo alla cartella in cui stiamo lavorando**. \
Ci sono diversi modi di esplorare il file che abbiamo appena caricato
```python
df.columns() #stampa il nome delle colonne del csv
df.head(n) #stampa le prime n righe del csv
df.tail(n) #stampa le ultime n righe del csv
```
Nel csv che abbiamo caricato, ad esempio, le colonne sono: *tweet_id,permalink,username,text,date,num_rt,num_favs,num_mentions,num_hashtags,tweet_loc,mentioned_locs,verified,user_description* \
Se vogliamo sapere esattamente cosa riguarda una determinata colonna, possiamo usare il comando
```python
df['tweet_id'] #stampa la colonna 'tweet_id'
```
Prima di esplorare una colonna però è necessaria renderla in forma di lista
```python
x = list(df['tweet_id']) 
```
Possiamo inoltre esplorare le righe attraverso il comando
```python
df.iloc(n) #stampa la nesima riga
df.iloc(n,m) #stampa la mesima colonna della nesima riga

df.loc[df['column_name']==y] #stampa tutte le righe in cui la colonna 'column_name' assume il valore y
```
Se volessimo creare un nuovo dataframe da zero, in cui abbiamo i seguenti dati:
| matricola  |nome   |cognome   |voto|
|---|---|---|---|
|  mts00235  |gennaro   |nolano   |30L   | 
| mc00523  | maria  | esposito  | 19  | 
| mts0001  |giampiero   |altrui   |26   |


Avremmo quattro colonne (matricola, nome, cognome, voto) e tre righe di dati. Un modo per creare un dataframe di questo tipo è utilizzando il seguente codice:
```python
df = [['matricola','nome','cognome','voto],
["mts00235","gennaro","nolano",33],
["mc00523","maria","esposito",19],
["mts0001","giampiero","altrui",26]
]

df = pd.DataFrame(df) #in questo caso il dataframe creato userà la prima riga come colonne
print(df.columns())

#Una seconda soluzione possibile
df = [["mts00235","gennaro","nolano",33],
["mc00523","maria","esposito",19],
["mts0001","giampiero","altrui",26]
]

df = pd.DataFrame(df, columns=['matricola','nome','cognome','voto])
print(df.columns())
```
Il dataframe può successivamente essere salvato con il codice
```python
df.to_csv('path')
```
Dove, ancora una volta, *path* sta per il percorso dove si vuole salvare il file.

# Json

Come già detto in precedenza, un file **json** funziona alla stessa maniera di un dizionario su python. Per fare dei test scaricare il file *clean_data_wcitta_week6.json* dalla cartella principale del corso seguendo le stesse istruzioni utilizzate per scaricare il file csv. \
Il comando per caricare il file sul codice è però diverso in questo caso:

```python
import json

with open('path') as infile:
  prova_json = json.load(infile)
```
Una volta importato in questa forma, il file è accessibile utilizzando la variabile che gli è stata affibbiata.

Possiamo poi salvare il file:
```python
with open('path', 'w') as outfile:
  json.dump(prova_json, outfile)
 
#notare bene la dicitira 'w+', che è un'opzione del comando 'open', che crea direttamente un file vuoto dal nome selezionato
```
Una volta importato, un file json è utilizzabile sostanzialmente come se fosse un dizionario. È importante quindi prima di tutto esplorarlo con
```python
prova_json.keys()
```
---
# Esercizio

Scegliere un corpus tra quelli presenti nel README.md della pagina del corso. Caricarlo su Python. 

Provare poi a caricarlo come stringa unica e poi come lista di frasi.

Da quante frasi è composto il corpus caricato? Da quanti caratteri?

Stampare la prima frase e l'ultima frase del corpus.

Descrivere brevemente il corpus: 

**Se csv**: 
 - Da quali colonne è formato il corpus?
 - Quali sono le colonne che possono essere di interesse?
 
**Se json:** 
  - Quali chiavi sono presenti nel corpus?
  - Qual è la gerarchia delle chiavi?
  - Quali valori possono essere di interesse?
