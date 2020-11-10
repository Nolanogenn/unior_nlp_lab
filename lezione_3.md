## Librerie

Le librerie offrono funzionalità aggiuntive, e sono indispensabili per lavorare con Python. 
Per poter utilizzare una libreria già esistente c'è bisogno di seguire due passaggi fondamentali:

- **installare** la libreria 
- **importare** la libreria nel codice che stiamo utilizzando

Una terza opportunità è quella di creare proprie librerie, ma in questo corso ci focalizzeremo principalmente su tre librerie già esistenti: **Pandas**, **Json** e **NLTK**.
Delle tre, **json** viene scaricata con Python, per cui può essere sempre importata senza essere installata precedentemente. 

## Installare librerie

Per installare una libreria si utilizza lo strumento **pip**, già utilizzato per installare Jupyter Lab. La procedura da seguire è la seguente:

1. Aprire il menù **Start** e scrivi nella barra della ricerca **cmd**. Aprire **Prompt dei Comandi**
2. Scrivere il comando **pip install** seguito dal nome della libreria che vogliamo isntallare
3. Aspettare che finisca l'operazione
4. Ben fatto!

Prima di proseguire, seguendo le istruzioni installiamo le librerie **pandas** e **nltk**.

**NB: A causa di un bug su windows, prima di poter utilizzare nltk bisogna anche installare la versione 1.19.3 della libreria numpy. si può fare utilizzando il seguente codice:**
***- pip install numpy==1.19.3***

# Importare librerie

Prima di utilizzare una libreria, è necessario *importarla* all'interno del codice che stiamo utilizzando. Il comando da utilizzare è:

```python
import pandas
```

In questo caso abbiamo semplicemente importato la libreria pandas e tutti i comandi a essa legata. Per evitare però di dover scrivere ogni volta *pandas* prima di invocare un comando, si può utilizzare il codice

```python
import pandas as pd
```
Che ci permette di usare l'*alias* pd al posto di *pandas*. Ci sono alcune convenzioni generalmente accettare per quanto riguarda le librerie più utilizate, ad esempio

```python
import pandas as pd
import numpy as np

```
Ma ciò non toglie che è possibile importare una libreria utilizzando un *alias* arbitrario. Questo significa anche che dobbiamo stare attenti agli *alias* scelti!
In questa lezione vedremo i comandi relativi alle due librerie **json** e **pandas** per importare database.

