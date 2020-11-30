# Processamento testuale

In questa sede faremo uso di diverse tecniche e strumenti per processare i testi di cui ci occuperemo. In particolare, faremo uso della libreria aggiuntiva NLTK.

Come per le altre librerie utilizzate, abbiamo bisogno innanzitutto di installarla con il comando
```
pip install nltk
```
E poi importarla su python
```
import nltk
```

In questa lezione ci occuperemo praticamente di come si tokenizza, come si rimuovono le stop-words e come si calcola la distribuzione delle parole in un testo.

Prima di tutto caricare il corpus scelto su Python sotto forma di *lista di frasi*.

Una volta fatto ciò, testiamo gli strumenti sulle singole frasi prima di utilizzarle su tutto il progetto.

## Eliminazione di punteggiatura e stop-words

Questi due momenti vanno di pari passo, poiché entrambi hanno come input una frase e come output la stessa frase filtrata degli elementi che farebbero 'rumore', ovvero creerebbero problemi con le analisi da effettuare.

Entrambi i processi, inoltre, vengono effettuati utilizzando i comandi:

```python
import string
import nltk
from nltk.corpus import stopwords #questo comando permette di importare sottomoduli da una libreria

punctuations_list = string.punctuation
stop_words = list(stopwords.words('italian')) 

```
In entrambi i casi è possibile, inoltre, ampliare la lista di elementi da eliminare, come se si trattasse di aggiungere elementi a una stringa (nel caso di segni di interpunzione) o aggiungere elementi a una lista (nel caso delle stop words). 

Esistono diversi modi per effettuare questa fase di pulizia del testo, questo è uno dei tanti:
```python
frase_prova = corpus[0]

transformation = str.maketrans(string.punctuation, ' '*len(string.punctuation))
#questo codice crea una funzione di trasformazione per cui
#data una stringa, tutti i segni di punteggiatura vengono sostituiti da spazi



```
