## Esercizio pag 1: InsertionSort

``` python
Algoritmo InsertionSort(S)
input Sequenza S[0 . . . n-1] di n chiavi
output Sequenza S ordinata in senso crescente

for i ← 1 to n-1 do {
  curr ← S[i]
  j ← i-1
  while ((j ≥ 0) AND (S[j]> curr)) do {
    S[j+1] ← S[j]
    j ← j-1
  }
  S[j+1] ← curr
}
```

1. Trovare delle opportune funzioni f1(n), f2(n) e f3(n) tali che le
seguenti affermazioni siano vere, per una qualche costante c > 0 e
per n abbastanza grande.

• Per ciascuna istanza di taglia n l’algoritmo esegue ≤ cf1(n)
operazioni.

R: $f1(n) = n^2$ NB al caso pessimo l'algoritmo esegue $\sum_n i = \frac{n(n-1)}{2}$ iterazioni

• Per ciascuna istanza di taglia n l’algoritmo esegue ≥ cf2(n)
operazioni.

R: $f1(n) = n$;

• Esiste una istanza di taglia n per la quale l’algoritmo esegue
≥ cf3(n) operazioni.

??? sempre n?

La funzione f1(n) deve essere la piu piccola possibile, mentre le
funzioni f2(n) e f3(n) devono essere le piu grandi possibili.

2. Sia `t_IS(n)` la complessita al caso pessimo dell’algoritmo. Sfruttando
le affermazioni del punto precedente trovare un upper bound O (·) e
un lower bound Ω (·) per `t_IS(n)`.

R: f1 ed f2

Soluzioni: f1 = n f2 = n^2 f3=n^2 theta = n^2.

Domande: Non ho ben chiaro cosa si intende con i minori uguali nelle indicazioni di complessita' e il ruolo delle costanti


## Esercizio 2 pag.9 MaxSegment


Descrizione dell’algoritmo

L’algoritmo calcola la **lunghezza del più lungo segmento continuo di 1** in una sequenza binaria `S[1 … n]`.

```plaintext
Algoritmo maxSegment1
Input: Sequenza S di n bit
Output: Lunghezza del più lungo segmento continuo di 1

max ← 0
curr ← 0
for i ← 1 to n do
    if S[i] = 1 then
        curr ← curr + 1
        if curr > max then max ← curr
    else
        curr ← 0
return max
```

**Esercizio:** Lunghezza massimo segmento di 1

- **Definizione:**  
  - $L$: lunghezza del massimo segmento di 1.
  - Invariante: siano $L_k$ le lunghezze dei segmenti di 1 presenti (posso prendere tutti i segmenti di 1 anche più volte) in $S_j = S[1 \text{ to } j]$ con $j < i$, allora $\max = \max\{L_k\}$.

- **Dimostrazione dell'invariante:**
  1. Inizio: per $i=1$, $j=0$, $\max=0$ (vero).
  2. Supponendo l'invariante vero per la generica iterazione $i$, all'interazione $i+1$:
     - Caso $S[i+1] = 1$ e $curr > \max$: assegno $\max \leftarrow curr$, quindi l'invariante è vero.
     - Caso $S[i+1] = 0$: il massimo segmento non può essere più lungo di quello del caso $i$-esimo, quindi l'invariante vale.
  3. Fine ciclo: il ciclo for ha una fine fissata ed $L$ e l'invariante sono veri per le motivazioni precedenti.


Soluzioni: piu o meno ci siamo...
---

## Esercizio 3: Ricerca di una Colonna di Zeri in una Matrice n × n

Descrizione del Problema

Sia `A` una matrice `n × n` di interi, con `n ≥ 2`,  
dove righe e colonne sono numerate a partire da `0`.

### Obiettivo
1. **Scrivere un algoritmo** che restituisca l’indice `j ≥ 0` di una **colonna contenente solo zeri**, se tale colonna esiste;  
   altrimenti, restituisca `−1`.  
   L’algoritmo deve contenere **un solo ciclo**.
2. **Determinare upper e lower bound** della complessità.
3. **Dimostrare la correttezza** dell’algoritmo tramite un opportuno **invariante di ciclo**.

---
**algoritmo** ZeroColumnFinder

**input** Matrice `M` con `dim(M) = n x n`   $n\geq2$

**output** Indice di una colonna di zeri se esiste, altrimenti -1. (gli indici partono da 0)

```algorithm
len <- 0
k <- 0
while k < n x n do
  //indice riga
  i <- k%n
  //indice colonna
  j <- k/n
  
  if M(i,j) = 0
    len++
    k++
  else
    len <- 0
    k <- (j+1)*n
  if len = n
    return j;

return -1;

```

**upper bound** al massimo il ciclo esterno scorre tutta la matrice una volta dunque $O(n^2)$ mentre il 

**lowerbound** avviene quando la prima colonna e' composta di soli zeri quindi $\Omega(n)$.

**correttezza** Proprietà L: l'indice restituito é -1 oppure quello della prima colonna di zeri
Invariante: len <= massima lunghezza di una colonna di zeri dall'alto della matrice

### Soluzione:
```algorithm
i <- 0
j <- 0
while j < n do
  if i = n then return j
  if M(i,j) != 0 then 
    j++
    i <- 0
  else i++

return -1;

```

**upper bound** come sopra, $O(n^2)$

**lower bound** ATTENZIONE!! per il lower bound si cerca un minorante per l'istanza peggiore!! in questo caso è la matrice con tutti zeri tranne la riga più in basso, quindi sempre $\Omega (n^2)$ dounque ho la condizione di proporzionalità $\Theta (n^2)$.

**correttezza** Invariante: dnetro al ciclo alla cella (i,j)
 - nessuna delle colonne [0 to j-1] è composta di soli zeri
 - M[0 to i-1, j] = 0

casi: 

matrice vuota, non puó avere colonne di zeri, vera per vacuità

primo if:true - il ciclo si ferma a j che è una colonna di zeri, invariante verificato 

secondo if true - verifico la prima parte dell'invariante per la colonna j ed incremento j, sono alla posizione i = 0 percui la seconda parte dell'invariante è banalmente vera.

secondo if false - la prima parte dell'invariante è vera per le precedenti condizioni, verifico la seconda parte dell'invariante per la riga i e la incremento.