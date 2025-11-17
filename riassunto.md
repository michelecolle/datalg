# 1.Nozioni di base
## Notazione formale
Un probelma computazionale é formato da un insieme di coppie (istanza, soluzione) dove istanze e soluzioni provengono dai rispettivi domini.

Un problema computazionale é costituito da:
  - Istanze $I\in D(I)$
  - Soluzioni $S\in D(S)$
  - Relazione $\Pi\in D(\Pi)\sube D(I)\times D(S)$  

Dove $D(I)$ e $D(S)$ sono i dominii di $I$ ed $S$, notare che $D(\Pi)$ é un sottoinsieme in quanto non é detto che i dominii di istanze e soluzioni siano esauriti da $\Pi$ (per esempio nella divisione tra interi $D(I) = N\times N$ ma alle infinite istanze con zero al denominatore non é associato nessun elemento di $\Pi$)

## Complessitá nel tempo
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
$\lfloor\log_a b\rfloor := n$ approssimabile a $b/(a^n) \leq 1$, ovvero al numero di volte che devo dividere $B$ per $a$ per ottenere 1 come risultato.
$$log_a b = c \Rightarrow b = a^c \Rightarrow b/a^c=1 $$

### nota di calcolo: 
Per determinare la complessitá proporzionale si trova prima $O(\cdot)$ che vale per tutti i casi e poi $\Omega(\cdot)$ al caso pessimo, se sono uguali allora la complessitá é proporzionale a $\Theta(\cdot)$.  

## Proprietà degli Ordini di Grandezza

Queste proprietà descrivono il comportamento asintotico delle funzioni (complessità).

$$\max\{f(n), g(n)\} \in \Theta (f(n) + g(n))$$


$$\sum_{i=0}^{k} a_i n^i \in \Theta(n^k) \quad \text{se } a_k > 0$$

$$\log_b n \in \Theta (\log_a n) \quad \text{se } a, b > 1$$
**Conseguenza:** La base costante del logaritmo si omette ($\Theta(\log n)$).


$$n^k \in o (a^n) \quad \text{se } k > 0, a > 1$$
**Significato:** La funzione esponenziale domina (cresce strettamente più velocemente).


$$(\log_b n)^k \in o(n^h) \quad \text{se } b > 1, h, k > 0$$
**Significato:** La funzione polinomiale domina (cresce strettamente più velocemente).

## Formule Chiave per Somme (Complessità Asintotica)

* **Somma Aritmetica (Lineare):**
    $$\sum_{i=1}^{n} i = \frac{n(n+1)}{2} \in \Theta(n^2)$$

* **Somma di Quadrati:**
    $$\sum_{i=1}^{n} i^2 = \frac{n(n+1)(2n+1)}{6} \in \Theta(n^3)$$

* **Somma Serie Geometrica (a > 1):**
    $$\sum_{i=0}^{n} a^i = \frac{a^{n+1} - 1}{a - 1} \in \Theta(a^n)$$

* **Caso Specifico (a=2):**
    $$\sum_{i=0}^{n} 2^i = 2^{n+1} - 1 \in \Theta(2^n)$$

* **Somma Serie Geometrica (Convergenza, $0 < a < 1$):**
    $$\sum_{i=0}^{\infty} a^i = \frac{1}{1 - a} \in \Theta(1)$$

* **Somma Armonica:**
    $$\sum_{i=1}^{n} \frac{1}{i} = H_n \approx \ln n \in \Theta(\log n)$$

## Terminologia della Complessità Asintotica

* **Logaritmica:** $\Theta(\log n)$  Base 2 o costante $> 1$.
* **Polilogaritmica:** $\Theta((\log n)^c)$ $c > 0$ costante.
* **Lineare:** $\Theta(n)$
* **Quadratica:** $\Theta(n^2)$
* **Cubica:** $\Theta(n^3)$
* **Polinomiale:** $\Theta(n^c)$ $c > 0$ costante.
* **Esponenziale:** $\Omega(a^n)$ $a > 1$ costante.

## Correttezza di un algoritmo
**Terminazione** Va dimostrato che l'algoritmo termina (non procede all'infinito)
**Segmenti** Dimostrare che a partire dallo stato iniziale si raggiungono in
successione gli stati specificati per la fine di ogni segmento. In
particolare, lo stato che deve valere alla fine dell’ultimo segmento
deve coincidere (o implicare) lo stato finale desiderato.  
**Segmenti notevoli:** cicli (for, while, repeat-until)

Un **invariante** per un ciclo é una proprietá espressa in funzione delle
variabili usate nel ciclo, che descrive lo stato in cui si trova l'esecuzione
alla fine di una generica iterazione del ciclo.

### Correttezza di un ciclo tramite invariante
Per dimostrare che alla fine del ciclo vale una certa proprietá L, si
individua un opportuno invariante e si dimostra che:
 - Esso vale all’inizio del ciclo (subito prima che il ciclo inizi).
 - Esso vale alla fine di ciascuna iterazione. Si dimostra in modo
induttivo provando che se vale alla fine di una generica iterazione,
vale alla fine della successiva.
 -  Alla fine dell’ultima iterazione, l'invariante implica la proprietá L (in
alcuni casi coincide con essa).


### Formula di Binet per Fibonacci

La successione di Fibonacci $F(n)$ è definita dalla ricorrenza $F(n) = F(n-1) + F(n-2)$, con $F(0)=0$ e $F(1)=1$.

### 1. Equazione Caratteristica
Per risolvere la ricorrenza si assume una soluzione della forma $\lambda^n$, che porta all'equazione caratteristica:
$$\lambda^2 - \lambda - 1 = 0$$

### 2. Radici
Le due radici sono il **Rapporto Aureo** ($\Phi$) e la sua coniugata ($\hat{\Phi}$):
* **$\Phi$** (Golden Ratio): $$\Phi = \frac{1 + \sqrt{5}}{2} \approx 1.618$$
* **$\hat{\Phi}$**: $$\hat{\Phi} = \frac{1 - \sqrt{5}}{2} \approx -0.618$$

### 3. Formula Chiusa (Formula di Binet)
La formula chiusa per $F(n)$ (dimostrata usando i casi base $F(0)$ e $F(1)$) è:
$$F(n) = \frac{1}{\sqrt{5}} \left( \Phi^n - \hat{\Phi}^n \right)$$

### 4. Ordine di Grandezza
Poiché $|\hat{\Phi}| < 1$, il termine $\hat{\Phi}^n$ tende a zero rapidamente. La crescita è dominata dal termine $\Phi^n$.
$$\text{Risultato: } F(n) \in \Theta (\Phi^n)$$
La successione di Fibonacci ha quindi una **complessità esponenziale**.

### Algoritmi descritti nelle slide
``` java
Algoritmo arrayMax(A)
Input: array A[0 ÷ n − 1] di n ≥ 1 interi
Output: max intero in A
currMax ← A[0];
for i ← 1 to n − 1 do
    if (currMax < A[i]) then currMax ← A[i];
return currMax
```
complessitá arrayMax $\Theta(n)$
``` java
Algoritmo prefixAverages1
for i ← 0 to n − 1 do
    a ← 0;
    for j ← 0 to i do
        a ← a + X[j];
    A[i] ← a/(i+1);
return A
``` 
complessitá prefixAverages1 $\Theta(n^2)$

``` java
Algoritmo prefixAverages2
s ← 0;
for i ← 0 to n − 1 do
    s ← s + X[i];
    A[i] ← s/(i+1);
return A
``` 
complessitá prefixAverages2 $\Theta(n)$

``` java
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
Pittoricamente sposto i numeri fino a che non raggiungo un numero minore di quello corrente (curr).   
complessitá InsertionSort $\Theta(n^2)$
``` java
Algoritmo linearSum(A,n)
Input: array A, intero n ≥ 1
Output: Pn−1
i=0 A[i]
if (n = 1) then return A[0];
else return linearSum(A,n − 1)+A[n − 1];
``` 
complessitá linearSum $\Theta(n)$
``` java
Algoritmo reverseArray(A,i,j)
Input: array A, indici i, j ≥ 0
Output: array A con gli elementi in A[i ÷ j] ribaltati
if (i < j) then
    swap(A[i],A[j]);
    reverseArray(A,i + 1,j − 1)
return
``` 
complessitá reverseArray $\Theta(n)$
``` java
Algoritmo power(x,n)
Input: x ∈ R e n ≥ 0 intero
Output: p(x, n)
if (n = 0) then return 1;
if (n dispari) then
    y ←power(x,(n − 1)/2);
    return x · y · y;
else
    y ←power(x,n/2);
    return y · y
``` 
complessitá power $\Theta(log(n))$ in quanto continuo a dividere per due (vedi precedente definizione di logaritmo)
``` java
Algoritmo powerFib(n)
Input: intero n ≥ 0
Output: F(n)
Φ ←(1 + √5)/2;
Φˆ←(1 − √5)/2;
return (power(Φ, n) − power(Φˆ, n))/√5
``` 
complessitá powerFib $\Theta(log(n))$, utilizzando un implementazione ricorsiva naive ho $O(2^n) mentre con un implementazione iterativa con memorizzazione avrei $O(n)$.
# 2.Alberi
## Alberi generali
 ## 🌳 Terminologia degli Alberi Radicati (Rooted Trees)

### 1. Definizione di Albero Radicato
Un albero radicato $T$ non vuoto soddisfa le seguenti proprietà:
* Esiste un nodo speciale **radice** ($r \in T$).
* Ogni nodo $v \ne r$ ha un **padre** $u$ **unico**.
* Ogni nodo $v \ne r$ è **discendente** della radice (risalendo i padri si arriva sempre a $r$).

### 2. Definizione Ricorsiva
Un albero radicato $T$ è partizionato come:
$$T = \{r\} \cup T_1 \cup T_2 \cup \dots \cup T_k$$
dove $r$ è la radice con figli $u_1, \dots, u_k$, e ogni $T_i$ è un albero non vuoto radicato nel figlio $u_i$.

---

### 3. Altre Definizioni Chiave

| Termine | Definizione |
| :--- | :--- |
| **Antenato** di $y$ | $x=y$ o $x$ è antenato del padre di $y$. |
| **Discendente** di $y$ | $y$ è antenato di $x$. |
| **Nodo Interno** | Nodo con $\ge 1$ figli. |
| **Nodo Esterno (Foglia)** | Nodo senza figli. |
| **Sottoalbero** $T_v$ | Albero formato da tutti i discendenti di $v$ (incluso $v$). |
| **Albero Ordinato** | Per ogni nodo interno, è definito un ordinamento lineare tra i suoi figli. |

---

### 4. Misure di Profondità e Altezza

| Misura | Definizione 1 (Non Ricorsiva) | Definizione 2 (Ricorsiva) |
| :--- | :--- | :--- |
| **Profondità** $\text{depth}_T(v)$ | Numero di archi da $r$ a $v$. $|Antenati(v)| - 1$. | $0$ se $v=r$, altrimenti $1 + \text{depth}_T(\text{padre}(v))$. |
| **Altezza** $\text{height}_T(v)$ | Lunghezza del cammino più lungo da $v$ a una foglia. | $0$ se $v$ è foglia, altrimenti $1 + \max_{w \text{ figlio di } v} (\text{height}_T(w))$. |
| **Altezza di $T$** $\text{height}(T)$ | $\text{height}_T(r)$, altezza della radice. |

**Livello $i$:** L'insieme dei nodi a profondità $i$.

**Proposizione:** L'altezza di un albero $T$ è uguale alla massima profondità tra tutte le foglie:
$$\text{height}(T) = \max_{v \in T: v \text{ foglia}} (\text{depth}_T(v))$$

```mermaid
graph TD
    subgraph Misure
        A[Altezza: max(Profondità delle foglie) = 3]
        P[Profondità: distanza dal nodo alla radice (A) = 0, 1, 2, 3]
    end

    A((Radice))
    subgraph Livello 0
        A
    end

    subgraph Livello 1
        B(Nodo)
        C(Nodo)
    end
    A --> B
    A --> C
    
    subgraph Livello 2
        D(Nodo)
        E(Foglia)
        F(Foglia)
    end
    B --> D
    B --> E
    C --> F

    subgraph Livello 3
        G(Foglia)
    end
    D --> G

    %% Definizioni Visive
    style A fill:#D0F0C0,stroke:#3C8000,stroke-width:2px,font-weight:bold
    style G fill:#FFD700,stroke:#B8860B,font-weight:bold
    
    linkStyle 0 stroke-width:3px,stroke:blue,stroke-dasharray: 5 5;
    linkStyle 1 stroke-width:3px,stroke:blue,stroke-dasharray: 5 5;
    
    linkStyle 3 stroke-width:3px,stroke:red,stroke-dasharray: 5 5;
    linkStyle 4 stroke-width:3px,stroke:red,stroke-dasharray: 5 5;
    linkStyle 5 stroke-width:3px,stroke:red,stroke-dasharray: 5 5;

    %% Annotazioni (non visibili direttamente sul diagramma ma utili per la spiegazione)
    P1[Profondità(G) = 3]
    A -->|depth=1| B
    B -->|depth=2| D
    D -->|depth=3| G
    
    classDef depth color:blue
    classDef height color:red
```