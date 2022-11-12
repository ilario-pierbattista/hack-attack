# Getting started

Iniziamo con il setup di un ambiente di sviluppo minimale. L'obiettivo è avere a portata di mano lo strumento più semplice per fare esperimenti, esercizi, eseguire e scrivere script utili.
Avere un ambiente funzionante e intuitivo è importante per imparare. Se avessimo a che fare con un ambiente che genera frustrazione, saremo sempre meno invogliati ad utilizzarlo, abbandonando gradualmente lo studio.
Questa è la mia proposta, ma ognuno ha i suoi gusti e con il tempo trova il suo setup preferito.

## Installare PyCharm

Scaricalo da qui. Scegli la community edition: è gratis e ha tutte le funzionalità che servono per iniziare.

https://www.jetbrains.com/pycharm/download

PyCharm è un IDE evoluto che offre:
- Controllo di sintassi: se scrivi qualcosa che non è formalmente valido, te lo segnalerà.
- Autocompletamento del codice: nomi di funzioni, di variabili, di parametri.
- Analisi statica del codice: se scrivi qualcosa di palesemente insensato, te lo segnalerà.

Perchè usarlo: per poter minimizzare l'errore umano, concentrandosi sulle cose che contano realmente.

Un IDE è comunque uno strumento complesso. Per non perderti nei suoi meandri, dai anche un'occhiata a [questa pagina](https://www.jetbrains.com/pycharm/learn/).

In PyCharm troverai una versione integrata dell'interprete, per cui sarai già pronto ad eseguire qualche script.

## Hello World

Tutti i corsi di programmazione iniziano così. 
Riscrivi il codice nell'IDE ed eseguilo. Che cosa succede?

```python
print("Hello World")
```

## Calcolatrice

Iniziamo a lavorare con un po' di numeri e variabili.

Lo script inizia con due assegnazioni di **valore** (3, 4) a **variabili** (x, y).
Si possono vedere le variabili come dei contenitori di valori.

Ricopia e osserva come cambia l'esecuzione cambiando qualche numero.
```python
x = 3
y = 4

print(x + y)
print(x - y)
print(x * y)
print(x / y)
```

L'interprete legge il codice riga per riga, sequenzialmente.
Ricopia ed esegui il seguente script. Leggi l'errore: perchè non funziona?
```python
x = 2
y = x + z
z = 3
```

## Tipi
Se sommi 3 mele e 2 mele hai 5 mele. Puoi sommare 2 mele e 3 pecore?

In Python il tipo di una variabile non è qualcosa di statico.
Al contrario è determinato dal tipo del valore che contiene.
La stessa cosa non si applica a tutti i linguaggi, alcuni sono molto più rigidi.

Nonostante il tipo delle variabili non sia predeterminato, bisogna comunque tenerne in considerazione.

Esegui questo script. Che considerazioni trai?

```python
x = 3
y = 4
a = "hello"
b = "world"

print(type(x))
print(type(y))
print(type(a))

z = x + y
c = a + b

print(z)
print(type(z))

print(c)
print(type(c))

# Queste daranno errore. Perchè?
ax = a + x
yb = y + b
```