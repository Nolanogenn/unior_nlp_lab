# Preprocessamento testuale

In questa sede faremo uso di diverse tecniche e strumenti per processare i testi di cui ci occuperemo. In particolare, faremo uso della libreria aggiuntiva NLTK.

Come per le altre librerie utilizzate, abbiamo bisogno innanzitutto di installarla con il comando
```
pip install nltk
```
E poi importarla su python
```python
import nltk
```

In questa lezione ci occuperemo nella pratica delle possibili fasi di processamento testuale, ovvero *rimozione di punteggiatura e stop-word* e *tokenizzazione*. /
**NB:** non è detto che queste fasi ci siano sempre in ogni progetto, né tantomeno che siano necessarie affinche il testo sia pronto per essere analizzato. Non sempre le stopword vengono eliminate; e allo stesso modo la semplice tokenizzazione non è sempre quello che ci serve, ma conviene migliorarla con strumenti che lavorano a livelli più bassi della singola parola, come l'algoritmo BPE.

Prima di tutto caricare il corpus scelto su Python.

Una volta fatto ciò, testiamo gli strumenti sulle singole frasi prima di utilizzarle su tutto il progetto.

## Tokenizzazione

Per tokenizzazione si intende la suddivsione del testo in esame in unità minori e si parlerà quindi di sentence tokenization qualora si suddivida il testo in frasi, e word tokenization qualora si suddivida il testo in lessemi. Un primo modo di suddividere un testo in frasi l'abbiamo già visto nel comando readlines. 

È possibile inoltre utilizzare NLTK
```python
from nltk.tokenize import sent_tokenize
#importiamo la funzione sent_tokenize

text = "Questo è il corso di NLP dell'Orientale. Questo corso è molto interessante. Mi sto divertendo da morire."
sentences = sent_tokenize(text)
print(sentences)
#notare che si tratta di una lista di frasi, per cui vale tutto ciò che è stato detto sulle liste
```
Il secondo tipo di tokenizzazione riguarda la suddivisione in lessemi. Nelle lingue che utilizzano lo spazio per dividere le parole è particolarmente facile effettuare questo tipo di suddivisione, anche senza librerie aggiuntive:
```python
text = "Studiare all'Orientale mi fa riflettere sulle decisioni della mia vita"
tokens = text.split()
#il comando sopra descritto accetta una stringa in input
#e come otuput ha una lista degli elementi della stringa
#tra parentesi possiamo inserire il carattere su cui dividere la stringa
#di default se non inseriamo nessun carattere il comando dividerà sugli spazi
```
Notare che il codice sopra descritto non suddivide bene in parole. È necessario eliminare l'apostrofo e sostituirlo con uno spazio affinché la tokenizzazione sia completa.


## Eliminazione di punteggiatura 

L'idea alla base del processo di eliminazione della punteggiatura è di utilizzare una stringa di punteggiatura come 'filtro' sul testo da cui vogliamo eliminare segni di interpunzione.

```python
import string

punctuations = string.punctuation
```
In questo caso *punctuations* è una stringa di segni d'interpunzione. Questo significa che, modificandola (aggiungendo o eliminando caratteri al suo interno) sarà possibile anche applicare un filtro diverso al testo, e eliminare un numero maggiore o minore di caratteri.

L'applicazione del filtro avviene attraverso la definizione di una funzione di trasformazione:

```python
frase_prova = corpus[0]

transformation = str.maketrans(string.punctuation, ' '*len(string.punctuation))
#questo codice crea una funzione di trasformazione per cui
#data una stringa in input, come output dà la stessa stringa 
#ma con i segni di punteggiatura sostituiti da spazi

frase_no_punctuation = frase_prova.transate(transformation)
#così facendo si applica la funzione che abbiamo appena definito
#con la nostra frase come input

print(frase_no_punctuation)
```
## Eliminazione delle stop-word

L'eliminazione delle stop-word è essenziale per alcuni tipi di analisi testuale dove avere parole che si ripetono con troppa frequenza potrebbe creare rumore, come può essere il semplice calcolo della frequenza delle parole e degli n-grammi. 

NLTK offre una lista di stop-word per diverse lingue che può essere poi utilizzata come filtro sul testo da modificare. È possibile modificare questo filtro utilizzando tutte le operazioni che si possono usare su una lista.

```python
import nltk
from nltk.corpus import stopword

stop_words = stopword.words('italian')
#la stringa tra parentesi indica la lingua le cui stop-word vogliamo rimuovere

print(stop_words)
```
Esistono diversi modi di applicare questo filtro a una stringa. Uno di questi modi verrà descritto di seguito:
```python

testo = "Questo è un testo di prova del corso di NLP"
testo_no_stop_word = [] #definiamo una lista vuota che andremo a riempire con i token che non sono stop-word

tokens = testo.split() #dividiamo la stringa in token

for t in tokens:
  if t not in stop_words: # la condizione è vera se il token NON è nella lista di stop-word
    testo_no_stop_word.append(t)
    
print(test_no_stop_word)    
```

## Esercizio

Caricato un corpus, dividerlo prima in frasi, dividere le frasi in token ed eliminare la punteggiatura.

Calcolare:
- quanti frasi ci sono nel corpus;
- quanti token ci sono nel corpus;
- quanti type ci sono nel corpus;
- valore ttr in percentuale.



