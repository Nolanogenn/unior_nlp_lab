# Frequenza delle parole e delle collocazioni

# Distribuzione di frequenza delle parole 

Uno dei metodi più immediati per cercare di analizzare automaticamente il contenuto di un testo è di calcolare la **distribuzione di frequenza** delle parole: ovvero, dato un corpus, si calcola con quanta frequenza appare un determinato **type**. Possiamo quindi contare direttamente i **type**, e chiederci se quelli che compaiono con maggiore frequenza siano "più importanti" rispetto agli altri.

NLTK offre un modo semplice per calcolare queste distribuzioni.

```python
import nltk
from nltk import * # l'asterisco, o stella di Kleene, permette di importare tutti i sottomoduli di una libreria
import string

testo_twinpeaks = """I segreti di Twin Peaks (Twin Peaks) è una serie televisiva statunitense ideata da David Lynch e Mark Frost.\n
          Fu trasmessa in due stagioni dal canale televisivo ABC, dall'8 aprile 1990 al 10 giugno 1991.\n
          Durante il periodo di messa in onda, grazie alla sua singolarità e al distacco stilistico rispetto ai programmi dell'epoca, la serie divenne presto un cult, reclutando una vasta schiera di fan.\n
          A distanza di decenni, è ancora considerata una delle più influenti nella storia della fiction televisiva ed ha influenzato moltissime serie successive, 
          come ad esempio Lost, True Detective, Fargo, I Soprano, X-Files, Black Mirror, Riverdale, Hannibal, Wayward Pines e molte altre, nonché il videogioco di culto    EarthBound.[1][2].\n
          Il successo del format ebbe un peso enorme sulle produzioni televisive successive al 1991, tanto da poter dividere la storia della televisione in un prima e un dopo I segreti di Twin Peaks,[1]\n"""

punctuations = string.punctuation # definiamo il filtro per eliminare la punteggiatura
transformation = str.maketrans(string.punctuation, ' '*len(string.punctuation)) # definiamo la funzione di trasformazione per trasformare i segni di interpunzione in spazi
testo_twinpeaks = testo_twinpeaks.transate(transformation) #applichiamo la funzione di trasformazione al testo

testo_twinpeaks = testo_twinpeaks.lower() # rendiamo il testo in minuscolo

tokens_twinpeaks = nltk.word_tokenize(testo_twinpeaks) # tokenizziamo il testo

fdist = nltk.FreqDist(tokens_twinpeaks) # creiamo la distribuzione di frequenza dei token nel testo

#il modulo fdist di nltk offre tutta una serie di strumenti per stampare i risultati

print(fdist.most_common(50))
```

**Domande:** 
1. Come possiamo migliorare i risultati? 
2. Come possiamo stampare in una forma meglio leggibile i token più frequenti?

Ci sono diversi problemi però con il metodo illustrato. Un primo problema riguarda il tipo di frequenza utilizzato: 
- il conteggio puro delle parole non è abbastanza per cogliere la differenza tra testi. Un testo con un maggior numero di token, infatti, avrà sempre un'occorrenza maggiore delle parole più frequenti. Non per questo esse sono *discriminative*;
- il conteggio delle parole prese singolarmente non ci fa capire l'uso che se ne fa delle parole. In un ipotetico corpus, questo metodo darebbe un unico valore al termine "comune", che si tratti di comune=organo amministrativo o comune=aggettivo.

Esistono diverse soluzioni a entrambi i problemi. Iniziamo a vedere come ampliare il contesto di studio focalizzandoci non sulle singole parole, ma sulle co-occorrenze (**n-grammi**). 

# Distribuzione di frequenza degli n-grammi

***You shall know a word by the company it keeps.*** \
-John Rupert Firt

Un **n-gramma** è definito come una sequenza di n elementi. Nel nostro caso, quindi, si tratterà di una sequenza di n parole, e si chiamerà **digramma** (*bigram*) con n=2 o **trigramma** (*trigram*) con n=3. Con n > 3 si parlerà semplicemente di n-gramma. 

Il concetto è dunque quello di utilizzare come unità di analisi non la parola ma un'unità più grande, comprendendo quindi tutte le combinazioni di parole che appaiono insieme.

Anche in questo caso, possiamo utilizzare NLTK.

```python

measures = nltk.collocation.BigramAssocMeasures() # raccoglie le metriche per calcolare la frequenza degli n-grammi

finder = BigramCollocationFinder.from_words(token_twinpeaks) # trova tutti i bigrammi nel testo tokenizzato
finder.apply_fre_filter(5) # filtra i bigrammi eliminando quelli che appaiono meno di 5 volte
scored = finder.score_ngrams(measures.raw_freq) # crea una lista ordinando i digrammi trovati per raw freq

print(scored)
```
**Domande:**
- come possiamo stampare i dati in maniera più leggibile?

Anche in questo caso, però, la frequenza non è una metrica statisticamente interessante. Come abbiamo visto, però, NLTK ci dà la possibilità di modificare il valore con cui ordina i digrammi nelle parentesi tonde (*opzioni*) di **score_ngrams**. Le più utilizzate sono:

- raw_freq: frequenza, calcolata come (num.occorrenze n-gramma)/(lunghezza del testo in token);
- pmi: pointwise mutual information, che prende in considerazione la frequenza dell'n-gramma e degli elementi presi separatamente.

**Domande:**
- stampando i bigrammi ordinati per raw_freq, come stampare il numero di occorrenze?

Tra le due opzioni, pmi è maggiormente informativa, in quanto non prende in considerazione la sola occorrenza dell'**n-gramma**. 

NLTK offre inoltre la possibilità di calcolare la frequenza dei trigrammi, utilizzando il codice:

```python
finder_trigram = TrigramCollocationFinder.from_words(token_twinpeaks)
finder_trigram.apply_freq_filter(5)

scored_trigram= finder_trigram.score_ngrams(measures.pmi)

print(scored_trigram)
```

## Esercizi

1. caricare e preprocessare il testo usando il corpus scelto;
2. mostrare le prime 10 parole per frequenza;
3. stampare i primi 10 digrammi per pmi e raw_freq e confrontarli. Quali differenze ci sono?
4. stampare i primi 10 trigrammi per pmi e raw_freq e confrontarli. Quali differenze ci sono?
5. paragonare la lista delle parole più frequenti con gli n-grammi più frequenti. Si riscontra qualcosa di interessante?
6. **BONUS**: per ognuna delle prime 5 parole per frequenza, stampare i primi 5 digrammi per pmi in cui la parola compare nella prima posizione 
