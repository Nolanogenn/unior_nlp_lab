# Intro al corso

## NLP?

Con **Natural Language Processing** s'intede la dottrina che comprende linguistica, informatica e machine learning. L'attenzione di base è far sì che le macchine capiscano il linguaggio umano / che il linguaggio umano possa essere analizzato da una macchina. Perché? Perché la potenza di calcolo di una macchina è ben superiore alla potenza di calcolo di qualunque essere umano. Per tal motivo una macchina può compiere azioni su un numero di dati estremamente elevato. Tali azioni possono essere ripetute, e possono avvenire in remoto. \
Gli sviluppi in NLP hanno permesso lo sviluppo di una serie di applicazioni pratiche molto utili nella vita quotidiana:

- Correzione automatica
- MT
- Sentiment Analysis
- QA / Chatbot
- Filtri Spam

Nella pratica, ognuna di queste applicazioni può essere suddivisa in quelli che definiamo ***task*** più piccoli e definiti. Una prima divisione principale viene solitamente fatta tra **Natural Language Understanding** e **Natural Language Generation**, ma, scendendo più nello speficifico, si possono definire una serie di ***task*** legati a diversi aspetti linguistici:

- tokenizzazione
- lemmatizzazione
- calcolo della Minimum Edit Distance
- ngrams
- language models
- classificatori
- parsing
- text
- speech recognition
- named entity recognition
...

Nello specifico, questi ***task*** vengono risolti attraverso l'uso del computer. In particolare, lo stato dell'arte tende a preferire l'uso del linguaggio di programmazione Python.

## Elementi fondamentali

Su quali dati lavoriamo? Si tratta di dati linguistici, raccolti in un **corpus**, o in più **corpora**. I **corpora** possono essere di diverso tipo (monolingue, multilingue, paralleli...) e trattano gli argomenti più svariati. \
Un corpus è solitamente composto da più frasi. Le frasi possono essere delimitate da segnalatori, come **<s>...</s>** o **<START>...<FINISH>**. Ogni frase è composta da più parole. Ma come si distinguono le parole? \
È accettata la concezione che la parola venga definita come la **stringa tra due spazi**. Questo è il modo migliore per permettere a una macchina di comprendere il concetto di parola. Sotto questa forma, solitamente non si parla di parole ma di **token**. Si parla inoltre di **type** per indicare il numero di token diversi presenti in un corpus.
Un corpus è quindi descritto come avente **N token** e un vocabolario composto da **V token**.\
  La relazione tra V e N è definita **legge di Herdan** o **di Heaps** (il primo la scoprì riguardo la linguistica, il secondo riguardo l'information retrieval), la quale dice che
```
  |V| = kN^B
```
Un corpus può inoltre essere descritto dal numero di **lemmi** (ovvero la forma che compare nel dizionario di una determinata parola). \
Un problema fondamentale nel creare un corpus è quello della **normalizzazione del testo**, ovvero della 'fissazione' delle caratteristiche di un testo affinché esso sia unitario. In generale, è la prima vera parte di processamento del testo, e comprende generalmente tre fasi/task:
  1. Tokenizzazione
  2. Normalizzazione delle parole
  3. Segmentazione delle frasi
 Non esistono metodi fissi per effettuare le task sopra citate, per una serie di questioni. A volte può servire tokenizzare eliminando tutta la punteggiatura e mettendo il testo in **lowercase**, ma non sempre è bene farlo (come distinguere ***us*** e ***U.S.***?). A volte ci può interessare l'ordine delle parole nelle frasi, ma non è sempre così (**Bag of Words**). La seconda fase comprende, solitamente, un processo di lemmatizzazione/stemming. Ma questo può farci perdere delle informazioni importanti riguardo il testo. \
  Bisogna sempre tenere ben in mente il progetto finale.
  
## Intro Python

### Installazione

Vedi la guida all'installazione di Python.

### "Hello World"

```python
print('Hello World!')
```

### Sintassi base
- assegnazione variabili (singole e multiple)
```python
prova_variabile = 1
prova_variabile = 2

prova_variabile = prova_variabile + 1
prova_variabile += 1

print(prova_variabile)
type(prova_variabile)

print(variabile_non_esistente)

###CONFRONTI TRA VARIABILI

x = 4
y = 4.0

print(x == y)
print(x != y)
print(x < y)
print(x >= y)
print(x is y)

```

- tipi di dati
  - int & float
  ```python
  x = 4
  k = 7
  print(type(x), type(k))
  
  y = 7.8
  print(type(y))
  
  print(x+k+y)
  
  z = x + k
  print(type(z))
  
  j = x + y
  print(type(j))
  
  ###OPERAZIONI
  
  addizione = x + y
  sottrazione = x - y
  moltiplicazione = x * y
  divisione = x / y
  modulus = x % y
  potenza = x ** y
  floor_division = x // y
    
  ```
  - list
  
   ```python
   x = [1,11,21,1211]
   print(x)
   
   print(len(x))
   
   print(x[0])
   print(x[-1])
   print(x[1:3])
   
   x.append()
   print(x)
   
   x.insert(1,'prova')
   print(x)
   
   x.remove('prova)
   print(x)
   
   x.pop(0)
   print(x)
   
   y = x.copy()
   z = list(x)
   print(y,z)
   print(y==z)
   
   j = x + y
   print(j)
   
   reverse(x)
   sort(x)

   ```
  - str
  ```python
  string_prova = "Questa è una stringa di testo"

  print(string_prova[0])
  print(string_prova[0:10])
  print(len(string_prova))
  
  print('Marco' in string_prova)
  
  stringa_due = stringa_prova + ' Marco'
  print(stringa_due)
  
  print("Per me si va ne la città dolente \n
          per me si va ne l'etterno dolore")
     
  
  caps = "QUESTA FRASE è IN CAPS"
  print(caps.lower())
  
  ```
