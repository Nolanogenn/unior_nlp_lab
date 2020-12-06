# Frequenza delle parole e delle collocazioni

# Distribuzione di frequenza delle parole 

Uno dei metodi più immediati per cercare di analizzare automaticamente il contenuto di un testo è di calcolare la **distribuzione di frequenza** delle parole: ovvero, dato un corpus, si calcola con quanta frequenza appare un determinato **type**. Possiamo quindi contare direttamente i **type**, e chiederci se quelli che compaiono con maggiore frequenza siano "più importanti" rispetto agli altri.

NLTK offre un modo semplice per calcolare queste distribuzioni.

```python
import nltk
import string

testo = """I segreti di Twin Peaks (Twin Peaks) è una serie televisiva statunitense ideata da David Lynch e Mark Frost.\n
          Fu trasmessa in due stagioni dal canale televisivo ABC, dall'8 aprile 1990 al 10 giugno 1991.\n
          Durante il periodo di messa in onda, grazie alla sua singolarità e al distacco stilistico rispetto ai programmi dell'epoca, la serie divenne presto un cult, reclutando una vasta schiera di fan.\n
          A distanza di decenni, è ancora considerata una delle più influenti nella storia della fiction televisiva ed ha influenzato moltissime serie successive, 
          come ad esempio Lost, True Detective, Fargo, I Soprano, X-Files, Black Mirror, Riverdale, Hannibal, Wayward Pines e molte altre, nonché il videogioco di culto    EarthBound.[1][2].\n
          Il successo del format ebbe un peso enorme sulle produzioni televisive successive al 1991, tanto da poter dividere la storia della televisione in un prima e un dopo I segreti di Twin Peaks,[1]\n"""

punctuations = string.punctuation # definiamo il filtro per eliminare la punteggiatura
transformation = str.maketrans(string.punctuation, ' '*len(string.punctuation)) # definiamo la funzione di trasformazione per trasformare i segni di interpunzione in spazi
testo = testo.transate(transformation) #applichiamo la funzione di trasformazione al testo

testo = testo.lower() # rendiamo il testo in minuscolo

tokens = nltk.word_tokenize(testo) # tokenizziamo il testo

fdist = nltk.FreqDist(testo) # creiamo la distribuzione di frequenza dei token nel testo

#il modulo fdist di nltk offre tutta una serie di strumenti per stampare i risultati

print(fdist.most_common(50))
```

**Domande:** 
1. Come possiamo migliorare i risultati? 
2. Come possiamo stampare in una forma meglio leggibile i token più frequenti?

Ci sono diversi problemi però con il metodo illustrato. Un primo problema riguarda il tipo di frequenza utilizzato: 
- il conteggio puro delle parole non è abbastanza per cogliere la differenza tra testi. Un testo con un maggior numero di token, infatti, avrà sempre un'occorrenza maggiore delle parole più frequenti. Non per questo esse sono *discriminative*;
- il conteggio delle parole prese singolarmente non ci fa capire l'uso che se ne fa delle parole. In un ipotetico corpus, questo metodo darebbe un unico valore al termine "comune", che si tratti di comune=organo amministrativo o comune=aggettivo.

Esistono diverse soluzioni a entrambi i problemi. Iniziamo a vedere come ampliare il contesto di studio focalizzandoci non sulle singole parole, ma sulle co-occorrenze (**ngrammi**). 

# Distribuzione di frequenza degli ngrammi



## esercizi applicando freq dist a corpus
