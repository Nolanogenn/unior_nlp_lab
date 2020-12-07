**Argomenti**
1. [If...else](#ifelse)
2. [Loop](#loop)
3. [Csv & Json](#csvjson)



## If...else <a name='ifelse'></a>

Abbiamo già mostrato alcune delle **condizioni logiche** utilizzabili in python:
```python
print(x == y)
print(x != y)
print(x < y)
print(x >= y)
print(x is y)

#questi codici stamperanno SEMPRE True o False
```

Un'applicazione più pratica delle **condizioni logica** è rappresentata dalle cosiddette **dichiarazioni condizionali** (***conditional statements***) che rappresentano un modo di controllare il flusso del codice che stiamo scrivendo.

L'idea alla base è di dare alla macchina il comando: fai x se la **condizione logica** che ti ho indicato è vera, fai y se è falsa.

Prima di proseguire, occorre notare che su Python gli spazi sono importanti. Dopo determinati comandi è **necessario** indentare, ovvero mandare avanti di quattro spazi (un *tab*). Il tasto *TAB* sulla tastiera serve proprio a questo!

```python

a = 12
b = 120

if b >= a:
  print("b è maggiore di a!") ###NOTARE L'INDENTAZIONE! 
else:
  print("a è maggiore di b!")

##NB: un if non indentato darà sempre errore
if 1=0:
print(False)
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

## Loop <a name='loop'></a>

Un'idea centrale nella programmazione è il concetto di **loop** o **ciclo**, ovvero un comando che ci permette di dare alla macchina il comando: *ripeti l'azione x per y volte*. Ogni volta che l'azione viene ripetuta, si parla di **iterazione**.

In Python esistono due tipi di **cicli**: ***while*** e ***for***. Vediamoli uno alla volta.

### Ciclo While

Un ciclo di questo tipo ordina al codice di *ripetere una determinata azione **fintanto che** la condizione definita sia vera*.

```python

i = 1
while i < 6:
  print(i)

### Questo codice stamperà la variabile i all'infinito, visto che 1 sarà sempre minore di 6

### NB NOTARE LA DIFFERENZA CON:

i=1
if i < 6:
  print(i)
  
###

i = 1
while i < 6:
  print(i)
  i+1
###Questo codice si interromperà dopo 5 iterazioni

```
**NB: NEL CASO DI UN LOOP INFINITO, PREMERE IL PULSANTE 'PAUSA' SU JUPYTERLAB O CTRL+C NEL PROMPT COMANDI PER INTERROMPERE**

### Ciclo For

Il ciclo **for** permette di ripetere un'azione un determinato numero di volte (a differenza di **while**). Per far ciò, questo **loop** utilizza una determinata sequenza su cui itereare l'azione richiesta. 

L'idea è dare alla macchina l'ordine: *per ogni elemento della sequenza, compi l'azione x*.

```python

num_lista = [1,2,3,4,5,6]

for num in num_lista:
  if num%2 == 0:
    print(num," è pari!")
    
vocali_lista = ['a', 'e', 'i', 'o', 'u']
parola = "gennaro"

for lettera in parola:
  if lettera in vocali_lista:
    print(lettera, " è una vocale")
  else:
    print(lettera, " è una consonante")

###Notare che la variabile dell'elemento che andiamo a iterare (num, o lettera) può essere scelta arbitrariamente
###Basta ricordarsela successivamente!

for x in range(6):
  print(x)
```

Questi due cicli hanno degli **statement** in comune. 

-**break**, comanda di interrompere il loop
```python
i = 1

while i%2==0:
  print(i, ' è pari')
  i**2 + 1
  if i == 100:
    break

```
-**continue**, comanda di interrompere l'iterazione corrente e continuare alla prossima.
```python
ha_biglietto = ['Marco', 'Giulio', 'Tonio']
persone = ["Marco", "Giulio", "Tonio", "Carlo", "Andrea"]

for persona in persone:
  if persona not in ha_biglietto:
    continue
  print(persona)


```

-**pass** comanda di non fare nulla (è ridondante, ma a volte può servire) 
```python
vocali_lista = ['a', 'e', 'i', 'o', 'u']
frase = "Quel bacio gli brucia nel cuore, ma il vecchio non muta la sua idea"
vocali_frase = []

for lettera in frase:
  if lettera in vocali_lista:
    vocali_frase.append(lettera)
  else:
    pass

```

-**else**, comanda di fare qualcosa quando la condizione non è più vera (per **while**) o quando la sequenza è conclusa (per **for**):
```python
frase = "Gennaro è stato a Ekaterinburg per 5 mesi."

###Output desiderato = "gennaro è stato a ekaterinburg per 5 mesi.<FINE>"

output = ""
for parola in frase.split():
  output += parola.lower()
else:
  output += '<FINE>'
```
---
## csv e json <a name='csvjson'></a>

Tra i diversi modi di conservare e utilizzare file di tipo linguistico, due sono quelli principalmente utilizzati: **.csv** e **.json**. All'interno di Python, questi prendono solitamente la forma di, rispettivamente: **matrici** e **dizionari**.

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

Esistono diversi modi di interpretare un file **csv** su Python (noi useremo la libreria *Pandas*, che usa la forma dati del **dataframe**), ma l'idea è generalmente di avere di fronte una **matrice mxn**, ovvero una *lista di liste tutte della stessa lunghezza*

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

#in questo caso abbiamo solo due oggetti e quattro caratteristiche, 
#per cui è ancora abbastanza facile ricordare quale ordine nella lista corrisponde a quale caratteristica
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

print(dizionario_anna['altezza'], dizionario_marco['altezza'])
print(dizionario_anna['altezza'] == dizionario_marco['altezza'])

```
La struttura di un dizionario comprende quindi **chiavi** (**keys**) e **valori** (**values**), dove le **chiavi** sono gli elementi a sinistra delle assegnazioni e i #**valori** gli elementi a destra.

Per ogni **chiave** si può avere **un unico valore** e le **chiavi** non possono ripetersi nello stesso dizionario, poiché rappresentano gli identificatori dei valori.

Un **valore** può essere rappresentato da un qualunque tipo di dato.
```python

dizioario_dati = {"stringa" : "test",
"int" : 7357,
"list" : ['t', 'e', 's', 't'],
"dict" : {"stringa" : "test",
"int" : 7357,
"list" : ['t', 'e', 's', 't']}
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

