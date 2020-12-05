## Argomenti
1. [NLP - definizione e applicazioni](#nlp)
2. [Python](#python)
---
# NLP? <a name='nlp'></a>
Con **Natural Language Processing** s'intede la dottrina che ha come obiettivo principale la comprensione da parte delle macchine del linguaggio umano. 

Alla base c'è una *fusione* di,tre domini: la linguistica, l'informatica e il machine learning. Ma perché è importante una macchina capisca il linguaggio umano?

Il motivo principale è che la potenza di calcolo di una macchina è ben superiore alla potenza di calcolo di qualunque essere umano. È quindi possibile affidare alla macchina compiti estremamente ripetitivi con un numero di dati estremamente elevato. 

Un computer può compiere azioni e ripetere compiti teoricamente all'infinito senza alcuna perdita di dati né di informazioni. 

La ricerca in ambito NLP ha permesso lo sviluppo di una serie di applicazioni pratiche che trovano utilizzo nella vita quotidiana:

- Correzione automatica;
- MT (SMT / NMT);
- Sentiment Analysis;
- QA / Chatbot / Agenti Conversazionali;
- Filtri Spam;
- ...

Nella pratica, ognuna di queste applicazioni può essere suddivisa in quelli che definiamo ***task***, ovvero problemi più piccoli e meglio definiti.

Due *macrotask* in cui si può dividere l'NLP sono il **Natural Language Understanding** e **Natural Language Generation**, ma, scendendo più nello speficifico, si possono definire una serie di *microtask* legati a diversi aspetti linguistici e alla risoluzione di problematiche ben definite, come:

- tokenizzazione;
- lemmatizzazione;
- calcolo della *Minimum Edit Distance*;
- analisi di *ngrams*;
- *language models*;
- classificatori;
- *parsing* (semantico e sintattico);
- speech recognition;
- named entity recognition;
- ...

Nonostante questi *microtask* possano essere risolti a mano da un esperto, è molto più comodo ed efficiente lasciarli risolvere a un computer. 

Ad oggi l'esistenza di molti software / servizi in cloud permette inoltre di affrontare questi problemi anche senza determiante conoscenze informatiche, ma l'utilizzo di linguaggi di programmazione ci offre maggiore libertà e flessibilità nei progetti. 

Ovviamente, il prezzo da pagare è che bisogna imparare a utilizzare gli strumenti a nostra disposizione, non solo per quanto riguarda la parte teorica ma anche l'applicazione pratica. Il rischio è di corrompere dati o fare analisi errate. Ma il gioco vale la candela, poiché queste pratiche sono alla base dello stato dell'arte in NLP.

Tra gli strumenti possibili, in questo corso ci soffermeremo sull'utilizzo del linguaggio di programmazione **Python**, accademicamente accettato come il linguaggio più consono allo studio di dati di qualunque tipo. 

## Elementi fondamentali di NLP

Su che tipo di dati lavoriamo?

Si tratta di dati linguistici, raccolti in un **corpus**, o in più **corpora**. I **corpora** possono essere di diverso tipo (monolingue, multilingue, paralleli, annotati, *raw*...) e possono trattare gli argomenti più svariati. 

Un corpus è solitamente composto da più frasi, le quali possono essere delimitate da segnalatori, come **\<s\>...\</s\>**, **\<STAR\T>...\<FINISH\>** o semplicemente dal capoverso **\n**. Ogni frase è a sua volta composta da più parole. Ma come distinguaimo le parole all'interno di una frase? Come fa un computer a capire cos'è una parola?

È generalmente accettata la concezione che la parola venga definita come una **stringa di caratteri tra due spazi**. Sebbene questo sia il modo più comodo per permettere a una macchina di comprendere il concetto di parola, questa definizione non è abbastanza per le lingue che non usano spazi per dividere le parole (come ad esempio cinese e giapponese). In questi casi servono algoritmi molto più complessi, di cui però non ci occuperemo in questa sede.

Sotto questa forma, solitamente si parla non di parole ma di **token** e **type**. Laddove con **type** si intendono le parole *diverse* presenti in un corpus, con **token** si intendono le parole *complessive* del corpus.

Ad esempio, la stringa:
```
"Tre tigri contro tre tigri,\n
tre tigri contro tre tigri".
```
Contiene 10 token, ma solo 3 type ("tre", "tigri", "contro").

Un corpus è quindi descritto come avente **N token** e un vocabolario composto da **V type**. Il rapporto tra token e type in percentuale viene chiamato **ttr** e descrive la varietà linguistica di un corpus. Si calcola:

```
(num.type / num.token) * 100
```

Un corpus può inoltre essere descritto dal numero di **lemmi** (ovvero la forma che compare nel dizionario di una determinata parola). 

Un problema fondamentale nella creazione un corpus è quello della **normalizzazione del testo**, ovvero della *fissazione* delle caratteristiche di un testo affinché esso sia considerabile unitario nel suo complesso o rispetto ad altri corpora. \
  In generale, la **normalizzazione** è la prima vera parte di processamento del testo, e comprende generalmente tre fasi/task:
  1. Tokenizzazione;
  2. Normalizzazione delle parole;
  3. Segmentazione delle frasi.
 Non esistono metodi fissi per effettuare le task sopra citate, per una serie di questioni. 
 
A volte può servire tokenizzare eliminando tutta la punteggiatura e mettere il testo in **lowercase**, ma non sempre è bene farlo (come distinguere poi ***us*** e ***U.S.***?). A volte ci può interessare l'ordine delle parole nelle frasi, ma non è sempre così (si veda ad esempio l'approccio **Bag of Words**).

Anche normalizzando le parole, attraverso ad esempio un processo di lemmatizzazione/stemming si potrebbero perdere delle informazioni importanti riguardo il testo. 
---
# Python <a name='python'></a>

## Installazione

Vedi la [guida all'installazione di Python](https://github.com/Nolanogenn/unior_nlp_lab/blob/main/installare_python.md).

## "Hello World"

```python
print('Hello World!')
```

## Sintassi base
- operazioni di base 
  ```python
  print(4+2)
  print(7-2)
  print(5*3)
  print(48/4)
  print(13%4)
  print(7**2)
  print(64//3)
  ```

- commenti al codice \
Qualunque linea introdotta da cancelletto (#) non ha valore per il codice, ma viene usata per comunicare con chiunque altro userà il codice, o per definire determinate parti di codici lunghi. \
```python
#questa riga è un commento
4+6
```
In questo corso i commenti verranno usati per spiegare parti di codice. 


- assegnazione variabili (singole e multiple) \
Si può assegnare a un'entità una *variabile*, con la quale potremmo poi in seguito lavorare.

```python
prova_variabile = 1
prova_variabile = 2

prova_variabile = prova_variabile + 1
prova_variabile += 1

print(prova_variabile)
type(prova_variabile)

print(variabile_non_esistente)
```

- condizioni logiche \
Si definisce condizione logica un'espressione che ha come risultato un valore tra **vero** e **falso**. Questo tipo di valore (vero\falso) è detto **booleano**.

```python
x = 4
y = 4.0

print(x == y)
print(x != y)
print(x < y)
print(x >= y)
print(x is y)

```

- tipi di dati \
Esistono diverse tipologie di dati processabili:

  * int & float \
  Rappresentano i numeri, in particolare **int** rappresenta i numeri interi e **float** i numeri decimali.
  
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
  ```

  * list \
  Questo tipo di dati rappresenta una **lista** che contiene altri elementi. Una volta definita una lista, è possibile selezionarle gli elementi e modificarla.
  
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
  * str \
  Questo tipo di dati rappresenta una **stringa di caratteri stampabili**.
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

Nel caso ci trovassimo a lavorare con file in formato .txt, possiamo aprirli su Python utilizzando il comando

```python
f = open("path", 'r')
file_txt = f.read()
```

Dove "path" è il percorso dove si trova il file (rispetto alla cartella in cui ci troviamo). Se quindi siamo già nella cartella in cui si trova il file, ci basterà inserire il nome di quest'ultimo.

Una volta caricato in questo modo, il file viene trattato come se fosse una stringa. Ma questo non è sempre l'ideale, a volte è preferibile caricare il file diviso già per righe. Ad esempio, ogni riga potrebbe essere una frase che vogliamo analizzare separatamente, e in questo caso il codice sarà:

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
