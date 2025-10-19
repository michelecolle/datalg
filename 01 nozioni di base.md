# Nozioni di Base

### Recap ordini di grandezza

- **Big O:**  
  $f(n) \in O(g(n))$ se $\exists n_0 \mid f(n) \leq g(n) \quad \forall n > n_0$

- **Omega:**  
  $f(n) \in \Omega(g(n))$ se $\exists n_0 \mid f(n) \geq g(n) \quad \forall n > n_0$

- **Theta:**  
  $f(n) \in \Theta(g(n))$ se $f(n) \in \Omega(g(n))$ e $f(n) \in O(g(n))$, quindi se $f(n)$ è proporzionale a $g(n)$.

- **Small o:**  
  $f(n) \in o(g(n))$ se $\lim_{n \to \infty}\frac{f(n)}{g(n)} =0$, quindi $f(n)$ é asintoticamente più piccolo di $g(n)$ 

### Approssimazione logaritmo
- NB: $\log_a B := n$ approssimabile a $B/(a^n) \leq 1$, ovvero al numero di volte che devo dividere $B$ per $a$ per ottenere 1 come risultato.


---

## Domande

- Capire come stimare la complessità, soprattutto per $O(\log n)$.
---

## Esercizi da fare

- Fare gli altri due esercizi a pag 78...

---

## Esercizi già svolti

### Correttezza tramite invariante pag 78

**Esercizio:** Lunghezza massimo segmento di 1

- **Definizione:**  
  - $L$: lunghezza del massimo segmento di 1.
  - Invariante: siano $L_k$ le lunghezze dei segmenti di 1 presenti (posso prendere tutti i segmenti di 1 anche più volte).
  - In $S_j = S[1 \text{ to } j]$ con $j < i$, allora $\max = \max\{L_k\}$.

- **Dimostrazione dell'invariante:**
  1. Inizio: per $i=1$, $j=0$, $\max=0$ (vero).
  2. Supponendo l'invariante vero per la generica iterazione $i$, all'interazione $i+1$:
     - Caso $S[i+1] = 1$ e $curr > \max$: assegno $\max \leftarrow curr$, quindi l'invariante è vero.
     - Caso $S[i+1] = 0$: il massimo segmento non può essere più lungo di quello del caso $i$-esimo, quindi l'invariante vale.
  3. Fine ciclo: il ciclo for ha una fine fissata ed $L$ e l'invariante sono veri per le motivazioni precedenti.

---

### Maggioranza assoluta (Pag. 103)

**Problema:**  
Sia $A$ un array di $n$ interi arbitrari. Progettare e analizzare un algoritmo che trova, se esiste, l’intero che occorre in $A$ almeno $\lfloor n/2 \rfloor + 1$ volte (maggioranza assoluta). L’algoritmo deve avere complessità $O(n)$.

- **Versione 1:** Assumere $A$ ordinato (facile)
- **Versione 2:** Nessuna assunzione su $A$ (difficile)

#### Versione 1: Array ordinato

**Input:** $A$ (array di interi ordinati)  
**Output:** Intero di maggioranza assoluta se esiste, altrimenti $-1$

```python
n = len(A)
lmin = floor(n/2)
cnt, v = 0, None
for i in range(n):
    if v == A[i]:
        cnt += 1
    else:
        cnt = 1
        v = A[i]
    if cnt > lmin:
        return v
return -1
```

**Invariante:**  
- $cnt$ è minore o uguale alla lunghezza del segmento più lungo di interi uguali e $cnt \leq lmin$.

**Casi:**
- Array vuoto: ritorna $-1$
- Array con un solo numero: ritorna il numero
- Se $A[i] == v$: incremento $cnt$ e controllo l’invariante
- Se $A[i] \neq v$: $cnt$ torna a 1, nuovo segmento
- Fine ciclo: restituisce $-1$ oppure il valore cercato
- Complessità $O(n)$

---

#### Versione 2: Array arbitrario

**Input:** $A$ (array di interi arbitrari)  
**Output:** Intero di maggioranza assoluta se esiste, altrimenti $-1$

```python
n = len(A)
lmin = floor(n/2)
intList, lenList = [], []
for i in range(n):
    idx = intList.index(A[i]) # se non presente, index() restituisce -1
    if idx != -1:
        lenList[idx] += 1
        if lenList[idx] > lmin:
            return intList[idx]
    else:
        intList.append(A[i])
        lenList.append(1)
return -1
```

- **Nota:** Non sicuro che la complessità sia $O(n)$ per la chiamata a `indexOf`.
