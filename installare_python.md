1.[Windows](#windows)
2.[Mac OS](#mac)

## Windows <a name="windows"></a>

1. Andare su https://www.python.org/ e andare nella finestra Downloads
2. Scaricare Python 3.9.0
3. Far partire l'installer .exe **SPUNTARE "ADD PYTHON TO PATH"**
4. Ben fatto!

Per testare se l'installazione è andata a buon fine:
1. Aprire il menù **Start** e scrivi nella barra della ricerca **cmd**. Aprire **Prompt dei Comandi**
2. Scrivere **py** e premere Invio 
3. Dovrebbe comparire la schermata mostrata di seguito:
![](https://i.ibb.co/827SRZK/py-successful.png)

Nel caso non funzionasse, provare a scrivere **python** o **python3** e inviare.

Ora bisogna controllare se anche **pip** (lo strumento utilizzato da Python per installare e organizzare le librerie esterne) è stato installato con successo.
Notare innanzitutto la riga si apre con *>>>*. Significa che siamo su Python, e dobbiamo tornare al prompt dei comandi premendo **CTRL+Z** e poi **INVIO**. 

Una volta fatto questo, come prima scrivere **pip -V** e premere invio. Dovrebbe comparire la seguente schermata:
![](https://i.ibb.co/ssVGWVp/pip-successful.png)

Se è andato tutto come previsto, ben fatto! Manca un ultimo passaggio: installare JupyterLab. Questo strumento permette di avere un'interfaccia grafica
quando si usa Python, rendendo il lavoro più intuitivo.

C'è però prima bisogno di scaricare **Microsoft Visual C++ 14.0**, scaricabile dal link https://go.microsoft.com/fwlink/?LinkId=691126. Far partire il file scaricato e aspettare finisca.

In seguito, dal **Prompt dei Comandi**, scrivere il comando **pip install jupyterlab**. Questo comando tornerà molto utile in futuro, perché è il comando necessario
per scaricare le librerie su Python. Aspettare che finisca l'installazione.

**Ben fatto!**

### Testare i codici

1. Aprire il menù **Start** e scrivi nella barra della ricerca **cmd**. Aprire **Prompt dei Comandi**
2. Scrivere **py** e premere Invio
3. Benvenuto/a in Python!

Questo strumento è utile per testare piccole parti di codice, ma non permette di salvare o modificare il codice.

### Creare un foglio Notebook su cui lavorare

1. Aprire il menù **Start** e scrivi nella barra della ricerca **cmd**. Aprire **Prompt dei Comandi**
2. Srivere **jupyter lab** e premere Invio
3. Appariranno molte scritte. Cercare l'url che inizia con **http://localhost:8888/** e andare all'indirizzo segnato
4. Creare un **notebook** Python 3

Oltre a offrire un'interfaccia grafica, JupyterLab permette di salvare il codice e di modificarlo in caso di errori. 

## Mac OS <a name="mac"></a>
