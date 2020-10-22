# Intro al corso

## Cos'è NLP?

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

- token
- corpus
- normalizzazione
- relazione tra parole

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
  - str
  ```python
  string_prova = "Questa è una stringa di testo"

  print(string_prova[0])
  print(string_prova[0:10])
  
  
  ```
  - range
  - bool
  - dict
- commenti 
