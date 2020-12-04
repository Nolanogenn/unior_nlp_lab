# Intro al corso

## NLP?

Con **Natural Language Processing** s'intede la dottrina che comprende linguistica, informatica e machine learning che ha, come obiettivo principale, far sì che le macchine capiscano il linguaggio umano, ovvero che il linguaggio umano possa essere analizzato automaticamente da una macchina. Perché?\
Perché la potenza di calcolo di una macchina è ben superiore alla potenza di calcolo di qualunque essere umano e può quindi compiere azioni su un numero di dati estremamente elevato. Tali azioni, inoltre, possono essere ripetute (teoricamente all'infinito) senza perdita di dati, e possono avvenire in remoto. \
La ricerca in ambito NLP ha permesso lo sviluppo di una serie di applicazioni pratiche che trovano utilizzo nella vita quotidiana:

- Correzione automatica
- MT
- Sentiment Analysis
- QA / Chatbot
- Filtri Spam

Nella pratica, ognuna di queste applicazioni può essere suddivisa in quelli che definiamo ***task***, ovvero problemi più piccoli e meglio definiti. Due task principali in cui si snoda tutto l'NLP sono il **Natural Language Understanding** e **Natural Language Generation**, ma, scendendo più nello speficifico, si possono definire una serie di ***task*** legati a diversi aspetti linguistici, come:

- tokenizzazione
- lemmatizzazione
- Minimum Edit Distance
- ngrams
- language models
- classificatori
- parsing
- text
- speech recognition
- named entity recognition
...

Nonostante questi **task** possano essere risolti a mano, è molto più comodo ed efficiente risolverli utilizzando un computer. L'esistenza di molti software / servizi in cloud permette inoltre di affrontare questi problemi anche senza determiante conoscenze informatiche, ma l'utilizzo di linguaggi di programmazione ci offre maggiore libertà nei progetti. \
Ovviamente, il prezzo da pagare è che bisogna imparare a utilizzare gli strumenti a nostra disposizione, non solo per quanto riguarda la teoria ma anche praticamente. In particolare, in questo corso ci soffermeremo sul linguaggio di programmazione **Python**, che viene solitamente usato allo stato dell'arte.

## Elementi fondamentali di NLP

Su quali dati lavoriamo? Si tratta di dati linguistici, raccolti in un **corpus**, o in più **corpora**. I **corpora** possono essere di diverso tipo (monolingue, multilingue, paralleli, annotato, *raw*...) e trattano gli argomenti più svariati. \
Un corpus è solitamente composto da più frasi. Le frasi possono essere delimitate da segnalatori, come **<s>...</s>** o **<START>...<FINISH>**. Ogni frase è composta da più parole. Ma come si distinguono le parole? \
È accettata la concezione che la parola venga definita come la **stringa tra due spazi**. Questo è il modo migliore per permettere a una macchina di comprendere il concetto di parola. Sotto questa forma, solitamente non si parla di parole ma di **token**. Si parla inoltre di **type** per indicare il numero di token diversi presenti in un corpus. \
Questa definizione va bene per le lingue che usano gli spazi per dividere le parole, ma per quelle che non rientrano in questa categoria (ad esempio cinese e giapponese) servono algoritmi molto più complessi. Nel nostro caso questa definizione ci basta. \
Un corpus è quindi descritto come avente **N token** e un vocabolario composto da **V type**.\
Un corpus può inoltre essere descritto dal numero di **lemmi** (ovvero la forma che compare nel dizionario di una determinata parola). \
Un problema fondamentale nel creare un corpus è quello della **normalizzazione del testo**, ovvero della 'fissazione' delle caratteristiche di un testo affinché esso sia considerabile unitario nel suo complesso. \
  In generale, la **normalizzazione** è la prima vera parte di processamento del testo, e comprende generalmente tre fasi/task:
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


###CONDIZIONI LOGICHE

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
   
  print("Gli spazi\tsono importante") 
  
  caps = "QUESTA FRASE è IN CAPS"
  print(caps.lower())
  
  ```

### Aprire e salvare file testuali 

Nel caso ci trovassimo a lavorare con file in formato .txt, possiamo aprirli su python utilizzando il comando

```python
f = open("path", 'r')
file_txt = f.read()
```
Dove "path" è il percorso dove si trova il file (rispetto alla cartella in cui ci troviamo). Se quindi siamo già nella cartella in cui si trova il file, ci basterà inserire il nome di quest'ultimo.

Una volta caricato in questo modo, il file viene trattato come se fosse una stringa. Ma questo non è sempre l'ideale, a volte è preferibile caricare il file diviso già per righe. Ad esempio, ogni riga potrebbe essere una frase che vogliamo analizzare separatamente. In questo caso il codice sarà:

```python
f = open("path", "r")
file_txt = f.readlines()
```

In questo caso il file verrà importato sotto forma di lista. Questa differenza nei modi di importare un file testuale diventa inoltre importante nel momento in cui vogliamo salvare un file. Il codice generico per salvare una stringa è:

```python
text_prova = "Ho perso la penna. La penna mi è caduta."
with open("path", "w") as f:
  f.write(text_prova)
```
Questo codice non farà altro che creare un file testuale in "path" e scrivere al suo interno le frasi "Ho perso la penna. La penna mi è caduta.". A volte ci basta questo processo, se non ci interessa mantenere una divisione in frasi per un'analisi successiva. Se invece volessimo salvare una lista di frasi in formato testuale, il codice da usare sarebbe il seguente:
```python
lista_frasi = ['Ho perso la penna.', 'La penna mi è caduta.']
with open("path", "w") as f:
  for frase in lista_frasi:
    f.write(frase)
    f.write('\n')
```
Questo codice:
1. Apre un file bianco in "path";
2. Fa un loop di tutte le frasi nella lista che abbiamo scelto (vedremo nella prossima lezione come funzionano i loop);
3. Scrive la frase nel file in "path";
4. Alla fine della frase scrive '\n' (ovvero l'accapo in forma testuale).

È buona norma, una volta finito di lavorare su un file aperto, usare il codice:
```python
f.close()
```

Per non incappare in possibili errori.
