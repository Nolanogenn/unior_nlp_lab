## csv e json

Tra i diversi modi di conservare e utilizzare file di tipo linguistico, due sono quelli principalmente utilizzati: **.csv** e **.json**. All'interno del linguaggio di programmazione, questi prendono solitamente la forma di, rispettivamente: **matrici** e **dizionari**.

- csv e matrici
Un **csv** (**c**omma **s**eparated **v**alues) è un file testuale che rappresenta una tabella. Ad esempio, una tabella del tipo:
![](https://i.ibb.co/6bNqHB1/tab-esempio.png)
se salvata come **.csv** avrà la forma seguente:
```csv
,i,want,to,eat,chinese,food,lunch,spend
i,5,827,0,9,0,0,0,2
want,2,0,608,2,0,6,5,1
to,2,0,4,686,2,0,6,211
eat,0,0,2,0,16,2,42,0
chinese,1,0,0,0,0,82,1,0
food,15,0,15,0,1,4,0,0
lunch,2,0,0,0,0,1,0,0
spend,1,0,1,0,0,0,0,0
```
L'aspetto positivo dei **csv** è la loro facilità di creazione e la possibilità, che offrono, di poter essere utilizzati in diverse applicazioni e linguaggi di programmazione (ad esempio Python e sql). In realtà il nome è fuorviante perché il separatore (di base una virgola) può in realtà essere qualunque altro simbolo. A volte si trova il punto e virgola, o **quattro spazi** (ovvero un **tab**, simboleggiato da "\t"). In quest'ultimo caso si parla solitamente di **tsv**. 

Esistono diversi modi di interpretare un file **csv** su Python (noi useremo la libreria *Pandas*), ma l'idea è generalmente di avere di fronte una **matrice**, dove per matrice s'intende una *lista di liste della stessa lunghezza*

```python

matrice_prova = [[0,1,2,3],
                 [1,2,3,4],
                 [2,3,4,5]]

print(len(matrice_prova))

print(matrice_prova[0])
print(matrice_prova[0][0])

print(matrice_prova[1:2])

csv_prova = [[i,5,827,0,9,0,0,0,2],
["want",2,0,608,2,0,6,5,1],
["to",2,0,4,686,2,0,6,211],
["eat",0,0,2,0,16,2,42,0],
["chinese",1,0,0,0,0,82,1,0],
["food",15,0,15,0,1,4,0,0],
["lunch",2,0,0,0,0,1,0,0],
["spend",1,0,1,0,0,0,0,0]]

```

- json e dizionari

Prima di descrivere cos'è un file **json** (**J**ava**S**cript **O**bject **N**otation) è necessario introdurre il concetto di **dizionario**.

Un **dizionario** è un tipologia di dati definita come ***una lista indicizzata***. Vediamo cosa vuol dire.

```python
#cerchiamo di definire un oggetto della realtà, ad esempio un essere umano
#una persona può essere identificata da una serie di caratteristiche
#l'altezza, l'età, il sesso, il colore di capelli
#cerchiamo di definire una persona con una lista

lista_anna = [160, 24, "f", "castani"]
lista_marco = [170, 22, "m", None]

#nel caso volessimo mettere a confronto le due persone e chiederci, ad esempio, chi tra i due sia più alto

print(persona_marco[0] > persona_anna[0])

#in questo caso abbiamo solo due oggetti e quattro caratteristiche, per cui è ancora abbastanza facile ricordare quale ordine nella lista corrisponde a quale caratteristica
#ma nel caso di più caratteristiche e più oggetti diventa più complicato tenere il passo
#è meglio avere un tipo di dato indicizzato, ovvero che permette di estrapolare determinate caratteristiche sulla base di un indice

dizionario_anna = {"altezza" = 160,
"età" = 24,
"sesso" = "f",
"colore_capelli" = castani"
}
dizionario_marco = {"altezza" = 170,
"età" = 22,
"sesso" = "m",
"colore_capelli" = None
}

print(dizionario_anna['altezza'] == dizionario_marco['altezza'])

#la struttura di un dizionario comprende quindi **chiavi** (**keys**) e **valori** (**values**), dove le **chiavi** sono gli elementi a sinistra delle assegnazioni e i #**valori** gli elementi a destra
#per ogni **chiave** si può avere **un unico valore** e le **chiavi** non possono ripetersi
#un **valore** può essere rappresentato da un qualunque tipo di dato

dizioario_dati = {"stringa"="test",
"int" = 7357,
"list" = ['t', 'e', 's', 't'],
"dict" = {"stringa"="test",
"int" = 7357,
"list" = ['t', 'e', 's', 't']}
}

print(dizionario_dati['dict']['int'])

print(dizionario_dati.keys())
print(dizionario_dati.values())

chiavi = list(dizionario_dati_keys())
print(chiavi[0])

#cosa succede se si richiama una chiave non esistente?

print(dizionario_anna['dipartimento'])

```

Un file **.json** è strutturalmente un dizionario:

```json
{
   "description":"A list of quotes from US Presidents from http://bit.ly/1hsAYQT. ID matches up with https://govtrack.us API results.",
   "data":[
      {
         "quotes":[
            "It's easier to do a job right, than to explain why you didn't"
         ],
         "id":38455,
         "name":"Martin Van Buren"
      },
      {
         "quotes":[
            "It is not strange... to mistake change for progress"
         ],
         "id":16115,
         "name":"Millard Fillmore"
      },
      {
         "quotes":[
            "A little flattery will support a man through great fatigue"
         ],
         "id":43159,
         "name":"James Monroe"
      },
      {
         "quotes":[
            "The only thing we have to fear is fear itself",
            "Remember, remember always, that all of us, and you and I especially, are descended from immigrants and revolutionists"
         ],
         "id":43176,
         "name":"Franklin D. Roosevelt"
      },
      {
         "quotes":[
            "Do what you can, with what you have, where you are",
            "It is hard to fail, but it is worse never to have tried to succeed"
         ],
         "id":43161,
         "name":"Theodore Roosevelt"
      }

]
}
```

# If...else

Abbiamo già mostrato le **condizioni logiche** utilizzabili in python:
```python
print(x == y)
print(x != y)
print(x < y)
print(x >= y)
print(x is y)

#questi codici stamperanno SEMPRE True o False
```

Un esempio più complicato è rappresentato dalle cosiddette **dichiarazioni condizionali** (***conditional statements***) che rappresentano un modo di controllare il flusso
del codice che stiamo scrivendo / di controllare i dati a cui stiamo lavorando.

L'idea alla base è di dare al codice il comando: fai x se la **condizione logica** che ti ho indicato è vera, fai y se è falsa.
**NB**  gli spazi sono **MOLTO** importanti in Python! Dopo un if **È NECESSARIO** indentare (ovvero: andare avanti di un tab). Il tasto *TAB* sulla tastiera serve proprio a questo!

```python

a = 12
b = 120

if b >= a:
  print("b è maggiore di a!") ###NOTARE L'INDENTAZIONE! 
else:
  print("a è maggiore di b!")

##NB: un if non indentato darà sempre errore
```
Notare che il condizionale **else** NON è necessario su python: nel caso sia assente e la condizione sia falsa, il codice non farà nulla. In pratica, questo può essere esplicitato scrivendo:

```python
a = 'gennaro'
b = 'guglielmo'

if len(a) > len(b):
  print('gennaro ha più lettere di guglielmo')
else:
  pass

```

**elif** è utilizzato per dire al codice 'se la condizione precendete è falsa, controlla questa condizione':

```python
a = 24
b = 12
c = 3

if b > a:
  print('b è maggiore di a')
elif b > c:
  print('b è maggiore di c')
```

È inoltre possibile ampliare le condizioni logiche utilizzando **and** e **or**:

```python
a = 24
b = 12
c = 3

if a > b and b > c:
  print('i valori sono in ordine di grandezza')
  
if b > a or b > c:
  print('b è maggiore almeno di uno degli altri due valori')
  
```

