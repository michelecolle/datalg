# Esercizi — Alberi (senza soluzioni)

Nota: il documento contiene solo gli enunciati degli esercizi. NON sono fornite soluzioni.

---

## 1. Esercizio (heightBad)  
Si supponga di calcolare l’altezza di un albero T di n nodi invocando l’algoritmo depth(T, v) da ciascuna foglia v di T e restituendo come altezza la massima profondità ottenuta.  
Dimostrare che tale strategia ha una complessità, nel caso pessimo, di Ω(n^2).  
(Riferimento: algoritmo `heightBad` in [GTG14], esercizio C-8.27.)

### risposta:
**Algoritmo** heightBad(T, v)  
**input** albero T nodo v  
**output** hmax  
``` alg
hmax <- 0
forall w in T.children(v) do:
    if(T.IsExternal(W))
        hmax <- max(hmax, T.depth(W))
return hmax
```
**prima chiamata** heightBad(T, T.root())  
### Complessitá
Pensando a un albero binario prprio completamente sbilanciato ho n/2 foglie e per ogni foglia di profonditá d depth ha complessitá d quindi $f(n) \leq \Sigma_{v_i \in leafs}d_i\leq\Sigma_{i=0}^{m=n/2}i\leq m(m+1)/2\in O(n^2)$  
Pensando ad un albero lineare per n/2 nodi e con n/2 foglie attaccate all'ultimo nodo si ha che $f(n) \geq \Sigma_{i=0}^{m=n/2}n/2 \in \Omega(n^2)$

---

## 2. Esercizio (Lowest Common Ancestor — C-8.50 [GTG14])  
Sia T un albero. Dati due nodi v, w ∈ T si definisce il Lowest Common Ancestor di v e w (LCA(v,w)) come l’antenato comune più profondo.  
Progettare un algoritmo efficiente per trovare LCA(v,w) e analizzarne la complessità.  
(Osservazione: un antenato comune esiste sempre ed è la radice.)
### Risposta1
**Algoritmo:** LCA1(T,v,w)
**Input:** Nodi v e w
**Output:** nodo LCA
``` python

def CheckBranch(k, w):
    contains <- false
    if k.IsRoot contains <- true
    if k == w contains <- true
    if k.IsLeaf() 
        contains <- false
    else
        foreach j in v.children() do
            contains <- contains or CheckBranch(j,w)
    return contains

found = false
t <- v
CheckBranch(t,w)
while not found do
    t <- v.parent
    found = CheckBranch(t,w)

return t
```
Insomma, molto meglio la soluzione del prof
---

## 3. Esercizio (MaximalSet — albero binario proprio)  
Si consideri un albero binario proprio T dove ciascun nodo v contiene un intero v.val ≥ 0. Un nodo v ∈ T si dice massimale se v.val ≥ u.val per ogni u antenato di v (la radice è sempre massimale).  
1. Progettare in pseudocodice un algoritmo ricorsivo `MaximalSet` che, per ogni nodo v, imposta un flag binario `v.maximal` a 1 se v è massimale, a 0 altrimenti. Alla fine dell’algoritmo il campo `maximal` di tutti i nodi deve risultare impostato.  
2. Analizzare la complessità dell’algoritmo progettato.

### Risposta:
nota: la radice é sempre massimale perché non ha antenati, quindi indipendentemente da root.val non viene confrontato con nessun altro valore.  
**Algoritmo:** MaximalSet(T,v)  
**Input:** Albero T e nodo v, v ha un flag intero $v.val\geq 0$   preassegnato  
**Output:** Albero T con flag v.maximal a 1 se il nodo é massimale, 0 altrimenti  
``` py
#visita in preorder
if T.IsRoot(v) than 
    v.maximal = 1
else
    #assegno a k il primo antenato massimale
    k <- T.parent(v)
    while not k.maximal
        k <- T.parent(k)
    v.maximal = v.val >= k.val ? 1 : 0

for w in T.childern(v)
    MaximalSet(w)
```
**Chiamata iniziale:** MaximalSet(T, T.root())  
**Complessitá:**   
ricordando che la profonditá per un albero generale ha complessitá $\Theta(n)$
 - maggiorante: $f(n)\leq\Sigma_{v\in T}T.depth(v)\leq\Sigma_n n=n^2\in O(n^2)$
 - minorante: $g(n)\geq\Sigma_{v\in T}T.depth(v)\geq\Sigma_{i=0}^n i\in \Omega(n^2)$  
 dunque la complessitá é proporzionale a $\Theta(n^2)$

### Soluzione: 
Si arriva a complessitá $O(n)$ passando all'algoritmo un valore $m$ ovvero il valore del massimante del ramo.

---

## 4. Esercizio (relazione tra foglie e nodi interni)  
Dimostrare che in un albero non vuoto T con n nodi di cui m foglie, dove ogni nodo interno ha almeno 2 figli, si ha che m ≥ n − m + 1.

---

## 5. Esercizio (preorderNext / inorderNext / postorderNext — C-8.41 [GTG14])  
Progettare tre algoritmi iterativi `preorderNext(v)`, `inorderNext(v)` e `postorderNext(v)` che, dato un nodo v di un albero binario proprio T, restituiscano il nodo visitato dopo v nella visita di T rispettivamente in preorder, inorder e postorder, o `null` se v è l’ultimo nodo visitato. Analizzarne la complessità.

---

## 6. Esercizio (allLiveAncestors)  
Si consideri un albero T in cui ogni nodo `v` contiene un valore binario restituito da `v.getElement()`; si dice `alive` se tale valore è `1`, e `dead` se esso è `0`.  
Progettare un algoritmo ricorsivo `allLiveAncestors` che per ogni nodo `v ∈ T` memorizzi in un campo `v.liveAncestors` il numero di antenati `alive` di `v`. Analizzare la complessità dell’algoritmo.

### Risposta:
**Algoritmo:** allLiveAncestors(T, v)  
**Input:** albero T e nodo v  
**Ouput:** al nodo v e a tutti i suoi discendenti viene settata la proprietá liveAncestor al numero di antenati vivi di v  
``` c#
//visita in preorder
v.liveAncestors <- v.alive
if not T.IsRoot(v) than
    v.liveAncestors += T.GetParent(v).liveAncestors
foreach w in T.childern(v) do
    allLiveAncestors(t, w)
```
**prima chiamata:** allLiveAncestor(T,T.GetRoot())  
**complessitá:** é una visita in preorder quindi eredita la complessitá di quest'ultima: $O(n)$

---

## 7. Esercizio (memorizzare l’altezza in ciascun nodo)  
Progettare un algoritmo che, dato un albero `T`, per ciascun nodo `v ∈ T` memorizzi la sua altezza in un campo `v.height`. Analizzarne la complessità.

---

## 8. Esercizio (All3Balanced)  
Sia T un albero binario proprio dove ogni nodo v ∈ T contiene un valore binario. Un nodo v ∈ T si dice 3-balanced se |n0(v) − n1(v)| ≤ 3, dove n0(v) e n1(v) denotano il numero di 0 (n0(v)) e 1 (n1(v)) nel sottoalbero Tv.  
Si progetti in pseudocodice un algoritmo ricorsivo `All3Balanced` per determinare se tutti i nodi di T sono 3-balanced, con complessità lineare nel numero di nodi di T.

---

## 9. Esercizio (albero di sensori: maxOnHeight)  
Un albero di sensori è un albero binario proprio T i cui nodi rappresentano sensori. Ciascun sensore v ∈ T ha un flag `v.ON` che vale 1 se il sensore è acceso, e 0 se è spento. Si vuole progettare un algoritmo ricorsivo `maxOnHeight` che, dato un albero di sensori T, restituisca la massima altezza di un sensore acceso. Se tutti i sensori sono spenti, l’algoritmo restituisce -1.  
1. Descrivere tramite pseudocodice la generica invocazione di `maxOnHeight`, specificandone con attenzione l’input e l’output.  
2. Analizzare la complessità di `maxOnHeight`.

### Risposta:
Descrizione, l'algoritmo partirá da root ed inizierá una discesa a livelli dell'albero, in modo che il primo sensore acceso trovato sia anche il piu alto, si suppone la presenza di un parametro di altezza per ogni nodo

**algoritmo** maxOnHeight(T,q, h)
**input** albero binario proprio T coda di nodi q di altezza h
**ouput** intero h massima altezza o -1 se tutti i sensori sono spenti

``` 
if q.empty return -1
q1 = new queue()
while q.HasNext() do:
    v = q.pop()
    if v.ON return h
    if v.hasChildren
        q1.enqueue(v.left)
        q1.enqueue(v.right)
    return maxOnHeight(T,q1, h-1)
```
**start** maxOnHeight(T,[T.root],T.maxHeight)

#### Analisi
**proprietá L:** il valore ritornato é la massima altezza di un sensore attivo
**invariante:** Gli elementi della coda q sono tutti alla stessa altezza, per ogni passo del ciclo tutti i sensori estratti da q sono spenti tranne al piu il sensore iesimo
**complessitá:** $\Theta(n)$ al caso pessimo

---

## 10. Esercizio (valutare un Parse Tree)  
Progettare e analizzare un algoritmo che, dato un Parse Tree T associato a un’espressione aritmetica (operatori binari, foglie con costanti/variabili), restituisce il valore della espressione E associata a T, assumendo che i valori di costanti e variabili siano noti.

---

## 11. Esercizio (valutare espressione in postfissa)  
Progettare e analizzare un algoritmo che, data una lista che rappresenta una espressione E in notazione postfissa, restituisce il valore di E, assumendo che i valori di costanti e variabili siano noti.

---

## 12. Esercizio (heightSum)  
Si vuole progettare un algoritmo ricorsivo `heightSum` per calcolare la somma delle altezze di tutti i nodi di un albero binario proprio T. Detta `heightSum(T,v)` la generica invocazione su un nodo v ∈ T, per risolvere il problema si eseguirà `heightSum(T,T.root())`.  
1. Descrivere tramite pseudocodice `heightSum(T,v)`, specificandone con attenzione l’input e l’output.  
2. Analizzare la complessità di `heightSum(T,T.root())` in funzione del numero n di nodi in T.

---

## 13. Esercizio (esistenza di alberi propri con altezza Θ(√n))  
Dimostrare che per ogni n > 0 dispari esiste un albero binario proprio con n nodi e altezza h ∈ Θ(√n).

---

## 14. Esercizio (deepLeaf)  
Si vuole progettare un algoritmo ricorsivo `deepLeaf` per trovare la foglia più profonda in un albero binario proprio T.  
1. Descrivere tramite pseudocodice la generica invocazione di `deepLeaf`, specificandone con attenzione l’input e l’output.  
2. Analizzare la complessità di `deepLeaf`.

---

## 15. Esercizio (infix — disegno dell’albero della ricorsione)  
Dato un Parse Tree T e l’algoritmo `infix(T,v,L)` che genera la notazione infissa (come descritto nelle note), disegnare l’albero della ricorsione relativo all’esecuzione di `infix` sul Parse Tree fornito e determinare la lista L di uscita.

---

## 16. Esercizio (complessità di inorder / infix / postfix)  
Analizzare la complessità degli algoritmi di visita:  
- `inorder(T.root())`  
- `infix(T,T.root(),L)` per la generazione della notazione infissa  
- `postfix(T,T.root(),L)` per la generazione della notazione postfissa  
(Indicare il costo in funzione del numero di nodi n di T.)

---

## 17. Esercizio (dati di visita: preorder → postorder)  
Si supponga che la visita in preorder di un albero ordinato di 6 nodi incontri i nodi nell’ordine A B C D E F. Dire quali delle seguenti sequenze possono rappresentare la visita in postorder dello stesso albero (motivando la risposta e disegnando l’albero):  
- B A F E C D  
- C D B F E A  
- C D A E F B

Per ogni sequenza possibile, disegnare un albero ordinato che la realizzi; per le sequenze impossibili, motivarne l’impossibilità.

---

## 18. Esercizio (analisi costo di chiamate ridondanti)  
Si consideri di calcolare l’altezza di un albero T invocando l’algoritmo `depth(v)` da ciascuna foglia v di T (già incluso in 1). Discutere l’inefficienza di chiamate ridondanti nelle soluzioni ricorsive naive e collegarlo all’analisi asintotica.

---

## 19. Esercizio (varie proprietà degli alberi binari propri)  
Riassumere e dimostrare le proprietà classiche per un albero binario proprio non vuoto con n nodi, m foglie e altezza h:  
- m = n − m + 1  
- h + 1 ≤ m ≤ 2^h  
- h ≤ n − m ≤ 2^h − 1  
- 2^h + 1 ≤ n ≤ 2^(h+1) − 1  
- log2(n + 1) − 1 ≤ h ≤ (n−1)/2

---

## 20. Esercizio (allDepths)  
Progettare un algoritmo `allDepths` che, dato un albero T, calcoli la profondità di ogni nodo v ∈ T e la memorizzi in un campo `v.depth`.  
Idea: utilizzare una visita in preorder che imposti `v.depth = 0` per la radice e per ogni figlio `u` imposti `u.depth = v.depth + 1` prima di visitare i figli di `u`.  
Descrivere il pseudocodice e analizzarne la complessità.

---

## 21. Esercizio (diskSpace)  
Si consideri un file system gerarchico la cui struttura è rappresentata da un albero T dove i nodi interni corrispondono alle cartelle e i nodi foglia ai file. Ogni nodo v ha un campo `v.loc-size` che memorizza lo spazio occupato dal nodo, escludendo quello dei discendenti.  
Progettare un algoritmo `diskSpace` che: dato un tale T calcoli, per ogni nodo v ∈ T, lo spazio aggregato occupato dai suoi discendenti e lo memorizzi in un campo `v.aggr-size`.  
Descrivere il pseudocodice (suggerimento: visita in postorder) e analizzarne la complessità.

---
