# Statement ed espressioni

Gli elementi di un linguaggio di programmazione possono essere divisi in due categorie:

- espressioni
- statement

Nella categoria delle **espressioni** ricadono tutte le stringhe valide che, una volta interpretate ed eseguite restituiscono un valore come risultato.

```python
3 + 5
```

Gli **statement** sono tutte le altre stringhe valide che, una volta interpretate ed eseguite, NON restituiscono un valore, ma hanno effetti differenti (assegnazioni di variabile, modifiche al flusso di esecuzione delle istruzioni, definizioni di funzioni e classi).

```python
x = 2
```

Un programma si compone di statement ed espressioni. Ad esempio.

```python
x = 2
y = x * 3
```

Prima riga: `2` è formalmente un'espressione. `x = 2` è lo statement che assegna il valore `2` alla variabile `x`. Nella sua forma più generica: `<variabile> = <espressione>`.

Seconda riga: `3` è formalmente un'espressione. Anche `x` è un'espressione: viene formalmente restituito in fase di esecuzione il valore contenuto all'interno della variabile. `x * 3` è ancora un'espressione, che moltiplica il valore contenuto in `x` per `3` e lo restituisce (nella sua forma più generica: `<espressione> * <espressione>`). `y = x * 3` forma uno statement di assegnazione, si riconduce alla forma generica `<variabile> = <espressione>`.

Interpretazione ed esecuzione di questo script seguono il seguente flusso.

```
> x = 2
 - Interpreto lo statement <variabile> = <espressione>
 - Definisce la variabile x e vi assegna il valore 2
> y = x * 3
 - Interpreto lo statement <variabile> = <espressione>
 - Definisce la variabile y e vi assegna il valore dell'espressione x * 3.
    - x * 3: interpreto l'espressione <espressione> * <espressione>
    - x * 3: qual è il valore dell'espressione?
      Moltiplica il valore dell'espressione a sinistra 
      per il valore dell'espressione a destra.
        - x: interpreto <espressione>
            - vado a prendere il valore assegnato alla variabile. È 1.
        - 3: interpreto <espressione>
            - è già un valore, è 3.
    - Il risultato è 6.
 - Il valore assegnato a y è 6.
```

Il progesso appena visto da vicino prende il nome di valutazione (o espansione) delle espressioni. È caratteristica comune di molti linguaggi di programmazione mettere in pratica la valutazione **eager** delle espressioni, ovvero nell'esatto momento in cui la stringa di codice viene interpretata ed eseguita.
Python mette in pratica la valutazione eager.

Esistono alcune rare eccezioni nelle quali i linguaggi applicano la valutazione **lazy**, ovvero il risultato delle espressioni viene effettivamente valutato solo nel momento in cui il risultato stesso deve essere consumato e non prima (es: stampa a video).


## Statement condizionale: if

Iniziamo con una caratteristica fondamentale dei programmi: fare operazioni differenti sulla base di alcune condizioni.

Iniziamo con il capire se un numero è pari o dispari.
```python
# a % b restituisce il resto della divisione intera tra a e b
# 10 % 2 restituisce 0 (10/2 fa 5 con resto 0)
# 11 % 3 restituisce 2 (11/3 fa 3 con resto 2)
if(10 % 2 == 0):
    print("10 è pari")
else:
    print("10 è dispari")

if(11 % 2 == 0):
    print("11 è pari")
else:
    print("11 è dispari")
```

La struttura generale di questo statement è (tra parentesi quadre si trovano gli elementi opzionali, in questo caso il ramo `else`, che è sempre opzionale):

```
if(<condizione>):
    <statement>
[else:
    <statement>
]
```

E che cos'è una condizione? Un particolare caso di espressione che può restituire solo valori [**booleani**](https://it.wikipedia.org/wiki/Algebra_di_Boole).

```
condizione: True | False
```

`True` e `False` sono gli unici valori possibili per il tipo `bool`. Prova ad eseguire:

```python
type(True)
type(False)
```

Le condizioni possono essere complicate e composte a piacere.
Così come abbiamo operatori per i numeri (+, -, /, *, %, ecc) e operatori per le stringhe (+, ecc), ci sono operatori per i valori booleani.

Gli [operatori booleani](https://docs.python.org/3/reference/expressions.html#boolean-operations) sono `and`, `or`, `not`. Le seguenti tabelle descrivono il loro funzionamento utilizzando le tavole di verità.

### And
Combina due valori booleani. Assume valore `True` solo quando **entrambi** gli input sono `True`.

| `a and b` | `a` | `b` |
| --- | --- | --- |
| False | False | False |
| False | True | False |
| False | False | True |
| True | True | True |

### Or
Combina due valori booleani. Assume valore `True` solo quando **almeno uno** gli input è `True`.

| `a or b` | `a` | `b` |
| --- | --- | --- |
| False | False | False |
| True | True | False |
| True | False | True |
| True | True | True |

### Not
Inverte un valore booleano.

| `not a` | `a` |
| --- | --- |
| True  | False |
| False | True |

### Comparazione

Gli operatori di comparazione formano un'espressione che compara due valori generici e restituisce un valore booleano.
I più comuni ed usati sono i [comparatori aritmetici](https://docs.python.org/3/reference/expressions.html#comparisons). Abbiamo visto prima l'operatore `==` che verifica l'uguaglianza del valori a sinistra e a destra dell'operatore.

Una veloce tabella riassuntiva dei comparatori aritmetici:

| Comparatore | Valore | 
| --- | --- |
| `a == b` | True se `a` e `b` contengono lo stesso valore, False altrimenti |
| `a > b` | True se il valore di `a` è strettamente maggiore del valore di `b`, False altrimenti |
| `a >= b` | True e il valore di `a` è maggiore o uguale a quello di `b`, False altrimenti |
| `a < b` | True se il valore di `a` è strettamente minore del valore di `b`, False altrimenti, False altrimenti | 
| `a <= b` | True se il valore di `a` è minore o uguale al valore di `b`, False altrimenti |

### Esercizi

1. Abbiamo visto prima come testare se un numero è pari o dispari.
    - Riscrivi lo stesso programma parametrizzando il numero da testare con una variabile a cui assegnerai un valore fisso.
    - Oltre a stampare se pari o dispari, stampa anche il numero che è stato testato.
    - Trova il modo di usare `input()` ([qui la documentazione](https://docs.python.org/3/library/functions.html#input)) per chiedere all'utente il numero da testare, anzichè scriverlo staticamente nel codice.

2. Scrivi un programma che richiede in input un numero e stampa `CHECK PASSED` solo se il numero è contemporaneamente divisibile per 2, per 3 e per 5. Altrimenti stampa `CHECK FAILED`.

3. Scrivi un programma che:
    1. Richiede in input un numero maggiore di 0, altrimenti stampa un messaggio di errore.
    2. Richiede in input un secondo numero compreso tra 0 (incluso) e il primo numero (escluso).
    3. Moltiplica i due numeri e stampa il risultato.

4. Scrivi un programma che:
    1. Richiede in input un primo numero.
    2. Richiede in input un secondo numero. Deve essere strettamente maggiore del primo, altrimenti deve stampare un errore.
    3. Richiede in input un terzo numero.
    4. Stampa "ESCLUSO" se non è incluso nell'intervallo numerico determinato dai primi due numeri (estremi inclusi), "INCLUSO" altrimento.


## Funzioni e procedure

Affrontiamo l'argomento da un punto di vista molto pratico: funzioni e procedure permettono di raggruppare porzioni di codice e costruire su di esse delle **astrazioni**.

Cosa distingue una funzione da una procedura? Entrambe accettano uno, nessuno o molteplici parametri in ingresso (argomenti). Le funzioni restituiscono (`return`) un valore, mentre le procedure non restituiscono nulla. Le procedure vengono definite ed invocate per godere dei loro **side-effect**, come ad esempio la stampa di una stringa, mentre le funzioni vengono definite ed invocate per godere della computazione del loro valore di ritorno.

Questa distinzione è per lo più concettuale. Nella maggior parte dei linguaggi di programmazione (Python tra questi) non vi sono differenze formali tra definire una procedura e definire una funzione.
Ancora, in Python, così come nella maggior parte dei linguaggi, non vengono fatti rispetto alla purezza della funzione (una **funzione pura** è una funzione priva di side-effect), per cui è sicuramente possibile definire funzioni che, ad esempio, stampano stringhe, scrivono su file, accedono ai database.

In termini progettuali, è bene tenere a mente un principio fondamentale: all'interno del corpo della funzione si dovrebbe sempre mantenere lo stesso livello di astrazione.
Non si dovrebbe mai mischiare operazioni ad alto livello di astrazione, con operazioni ad un più basso livello di astrazione. Torneremo a tempo debito su questo punto.

La sintassi per la definizione di funzioni e procedure in Python ha la seguente forma.

```python
def <nomeFunzione>([<argomento1>], [<argomento2>], ..., [<argomentoN>]):
    <corpo>
```

In questa psuedo-notazione le parentesi quadre indicano l'opzionalità: uno, nessuno o molteplici argomenti.
Questa sintassi non esprime nulla riguardo al valore di ritorno, a sottolineare il fatto che non vi sia differenza formale tra funzioni e procedure nel linguaggio.

La funzione e la procedura di seguito hanno la stessa struttura sintattica.
Sappiamo che la prima è una funzione perchè c'è esplicitamente `return restoDivisioneIntera2 == 0` al termine del corpo.

```python
def isEven(x):
    restoDivisioneIntera2 = x % 2
    return restoDivisioneIntera2 == 0
```

```python
def hello(who):
    print("Hello, ", who)
```

Di qui in avanti userò il termine funzione per riferirmi al costrutto del linguaggio e non farò distinzioni tra funzioni e procedure, salvo contraria indicazione.

### Scope delle variabili

```python
def double(x):
    return x * 2

x = 3
print("x: ", x)
print("double(x): ", double(x))
print("x again: ", x)
```

### Esercizi

## References

- https://docs.python.org/3/reference/expressions.html
- https://it.wikipedia.org/wiki/Algebra_di_Boole
