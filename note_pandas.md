## Basics 

- Aprire un file:
```python
df = pd.read_csv(‘path’) #se il file è csv
df = pd.read_excel(‘path’) #se il file è excel
df = pd.read_csv(‘path’, delimiter=’\t’) #se il file è tsv
```
- Esplorare un dataframe:

```python
print(list(df.columns)) #stampa la lista delle colonne

print(df.shape) #stampa le dimensioni del dataframe

df.head(n) #dove n è il num di righe che vogliamo vedere
df.tail(n)

df.iloc(n) stampa la nesima riga
df.iloc(n,m) stampa la mesima colona della nesima riga

df.loc[df[k] == y]] stampa tutte le righe in cui la colonna k ha valore y
```
- Ordinare i dati:

```python
df.sort_values([k]) # stampa le righe ordinandole per la colonna k

df.sort_values([k,x]) # stampa le righe ordinandole prima per la colonna k, poi per la colonna x

df.sort_values([k,x], ascending=[0,1]) # la colonna k è ordinanta in maniera discendente, la colonna x in maniera ascendente
```
- Aggiungere dati:

```python
df[j] = o #se j non esiste aggiunge una colonna con nome j e valore o, se j esiste ne cambia il valore 

df[j] = df[k] + df[x] #la colonna j avrà come valore la somma dei valore di k e di x delle diverse righe
```

- Eliminare dati:

```python
df = df.drop(columns=[k]) #elimina la colonna k
```

- Salvare il dataframe:

```python
df.to_csv('prova_dataframe.csv', index=bool, sep=’,’)
df.to_excel('prova_excel')

```

## Filtrare i dati

```python
df.loc[(df[k] == y) & (df[x] == o)] #mostra le righe in cui k == y e x == o

df.loc[(df[k] == y) | (df[x] == o)] #mostra le righe in cui k == y oppure x == o

df.loc[df[k].str.contains(str)] #trova le righe in cui la colonna k contiene str
df.loc[~df[k].str.contains(str)] #trova le righe in cui la colonna k NON contiene str

#È possibile usare regex per questo tipo di filtri
df.loc[df[k].str.contains(re, regex=True)]
```

## Conditional Changes

Df.loc[df[k] == y, k] = j
Trasforma tutti i casi in cui k = y in j

Df.loc[df[k] == y, [z,x]] = [1,2]
Se nella riga k == y, z diventa 1 e x diventa 2


## Aggregate Statistics (Groupby)


df.groupby([k]).mean() #trova le medie dei valori delle colonne raggruppando le righe per k
df.groupby([k]).mean().sort_values(x, ascending=False)

df.groupby([k,x]).count()[k] #conta le combinazioni dei valori delle colonne k e x


