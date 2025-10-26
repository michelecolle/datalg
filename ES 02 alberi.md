# Esercizi — Alberi (senza soluzioni)

Nota: il documento contiene solo gli enunciati degli esercizi. NON sono fornite soluzioni.

---

1. Esercizio (heightBad)  
Si supponga di calcolare l’altezza di un albero T di n nodi invocando l’algoritmo depth(T, v) da ciascuna foglia v di T e restituendo come altezza la massima profondità ottenuta.  
Dimostrare che tale strategia ha una complessità, nel caso pessimo, di Ω(n^2).  
(Riferimento: algoritmo `heightBad` in [GTG14], esercizio C-8.27.)

---

2. Esercizio (Lowest Common Ancestor — C-8.50 [GTG14])  
Sia T un albero. Dati due nodi v, w ∈ T si definisce il Lowest Common Ancestor di v e w (LCA(v,w)) come l’antenato comune più profondo.  
Progettare un algoritmo efficiente per trovare LCA(v,w) e analizzarne la complessità.  
(Osservazione: un antenato comune esiste sempre ed è la radice.)

---

3. Esercizio (MaximalSet — albero binario proprio)  
Si consideri un albero binario proprio T dove ciascun nodo v contiene un intero v.val ≥ 0. Un nodo v ∈ T si dice massimale se v.val ≥ u.val per ogni u antenato di v (la radice è sempre massimale).  
1. Progettare in pseudocodice un algoritmo ricorsivo `MaximalSet` che, per ogni nodo v, imposta un flag binario `v.maximal` a 1 se v è massimale, a 0 altrimenti. Alla fine dell’algoritmo il campo `maximal` di tutti i nodi deve risultare impostato.  
2. Analizzare la complessità dell’algoritmo progettato.

---

4. Esercizio (relazione tra foglie e nodi interni)  
Dimostrare che in un albero non vuoto T con n nodi di cui m foglie, dove ogni nodo interno ha almeno 2 figli, si ha che m ≥ n − m + 1.

---

5. Esercizio (preorderNext / inorderNext / postorderNext — C-8.41 [GTG14])  
Progettare tre algoritmi iterativi `preorderNext(v)`, `inorderNext(v)` e `postorderNext(v)` che, dato un nodo v di un albero binario proprio T, restituiscano il nodo visitato dopo v nella visita di T rispettivamente in preorder, inorder e postorder, o `null` se v è l’ultimo nodo visitato. Analizzarne la complessità.

---

6. Esercizio (allLiveAncestors)  
Si consideri un albero T in cui ogni nodo `v` contiene un valore binario restituito da `v.getElement()`; si dice `alive` se tale valore è `1`, e `dead` se esso è `0`.  
Progettare un algoritmo ricorsivo `allLiveAncestors` che per ogni nodo `v ∈ T` memorizzi in un campo `v.liveAncestors` il numero di antenati `alive` di `v`. Analizzare la complessità dell’algoritmo.

---

7. Esercizio (memorizzare l’altezza in ciascun nodo)  
Progettare un algoritmo che, dato un albero `T`, per ciascun nodo `v ∈ T` memorizzi la sua altezza in un campo `v.height`. Analizzarne la complessità.

---

8. Esercizio (All3Balanced)  
Sia T un albero binario proprio dove ogni nodo v ∈ T contiene un valore binario. Un nodo v ∈ T si dice 3-balanced se |n0(v) − n1(v)| ≤ 3, dove n0(v) e n1(v) denotano il numero di 0 (n0(v)) e 1 (n1(v)) nel sottoalbero Tv.  
Si progetti in pseudocodice un algoritmo ricorsivo `All3Balanced` per determinare se tutti i nodi di T sono 3-balanced, con complessità lineare nel numero di nodi di T.

---

9. Esercizio (albero di sensori: maxOnHeight)  
Un albero di sensori è un albero binario proprio T i cui nodi rappresentano sensori. Ciascun sensore v ∈ T ha un flag `v.ON` che vale 1 se il sensore è acceso, e 0 se è spento. Si vuole progettare un algoritmo ricorsivo `maxOnHeight` che, dato un albero di sensori T, restituisca la massima altezza di un sensore acceso. Se tutti i sensori sono spenti, l’algoritmo restituisce -1.  
1. Descrivere tramite pseudocodice la generica invocazione di `maxOnHeight`, specificandone con attenzione l’input e l’output.  
2. Analizzare la complessità di `maxOnHeight`.

---

10. Esercizio (valutare un Parse Tree)  
Progettare e analizzare un algoritmo che, dato un Parse Tree T associato a un’espressione aritmetica (operatori binari, foglie con costanti/variabili), restituisce il valore della espressione E associata a T, assumendo che i valori di costanti e variabili siano noti.

---

11. Esercizio (valutare espressione in postfissa)  
Progettare e analizzare un algoritmo che, data una lista che rappresenta una espressione E in notazione postfissa, restituisce il valore di E, assumendo che i valori di costanti e variabili siano noti.

---

12. Esercizio (heightSum)  
Si vuole progettare un algoritmo ricorsivo `heightSum` per calcolare la somma delle altezze di tutti i nodi di un albero binario proprio T. Detta `heightSum(T,v)` la generica invocazione su un nodo v ∈ T, per risolvere il problema si eseguirà `heightSum(T,T.root())`.  
1. Descrivere tramite pseudocodice `heightSum(T,v)`, specificandone con attenzione l’input e l’output.  
2. Analizzare la complessità di `heightSum(T,T.root())` in funzione del numero n di nodi in T.

---

13. Esercizio (esistenza di alberi propri con altezza Θ(√n))  
Dimostrare che per ogni n > 0 dispari esiste un albero binario proprio con n nodi e altezza h ∈ Θ(√n).

---

14. Esercizio (deepLeaf)  
Si vuole progettare un algoritmo ricorsivo `deepLeaf` per trovare la foglia più profonda in un albero binario proprio T.  
1. Descrivere tramite pseudocodice la generica invocazione di `deepLeaf`, specificandone con attenzione l’input e l’output.  
2. Analizzare la complessità di `deepLeaf`.

---

15. Esercizio (infix — disegno dell’albero della ricorsione)  
Dato un Parse Tree T e l’algoritmo `infix(T,v,L)` che genera la notazione infissa (come descritto nelle note), disegnare l’albero della ricorsione relativo all’esecuzione di `infix` sul Parse Tree fornito e determinare la lista L di uscita.

---

16. Esercizio (complessità di inorder / infix / postfix)  
Analizzare la complessità degli algoritmi di visita:  
- `inorder(T.root())`  
- `infix(T,T.root(),L)` per la generazione della notazione infissa  
- `postfix(T,T.root(),L)` per la generazione della notazione postfissa  
(Indicare il costo in funzione del numero di nodi n di T.)

---

17. Esercizio (dati di visita: preorder → postorder)  
Si supponga che la visita in preorder di un albero ordinato di 6 nodi incontri i nodi nell’ordine A B C D E F. Dire quali delle seguenti sequenze possono rappresentare la visita in postorder dello stesso albero (motivando la risposta e disegnando l’albero):  
- B A F E C D  
- C D B F E A  
- C D A E F B

Per ogni sequenza possibile, disegnare un albero ordinato che la realizzi; per le sequenze impossibili, motivarne l’impossibilità.

---

18. Esercizio (analisi costo di chiamate ridondanti)  
Si consideri di calcolare l’altezza di un albero T invocando l’algoritmo `depth(v)` da ciascuna foglia v di T (già incluso in 1). Discutere l’inefficienza di chiamate ridondanti nelle soluzioni ricorsive naive e collegarlo all’analisi asintotica.

---

19. Esercizio (varie proprietà degli alberi binari propri)  
Riassumere e dimostrare le proprietà classiche per un albero binario proprio non vuoto con n nodi, m foglie e altezza h:  
- m = n − m + 1  
- h + 1 ≤ m ≤ 2^h  
- h ≤ n − m ≤ 2^h − 1  
- 2^h + 1 ≤ n ≤ 2^(h+1) − 1  
- log2(n + 1) − 1 ≤ h ≤ (n−1)/2

---

20. Esercizio (allDepths)  
Progettare un algoritmo `allDepths` che, dato un albero T, calcoli la profondità di ogni nodo v ∈ T e la memorizzi in un campo `v.depth`.  
Idea: utilizzare una visita in preorder che imposti `v.depth = 0` per la radice e per ogni figlio `u` imposti `u.depth = v.depth + 1` prima di visitare i figli di `u`.  
Descrivere il pseudocodice e analizzarne la complessità.

---

21. Esercizio (diskSpace)  
Si consideri un file system gerarchico la cui struttura è rappresentata da un albero T dove i nodi interni corrispondono alle cartelle e i nodi foglia ai file. Ogni nodo v ha un campo `v.loc-size` che memorizza lo spazio occupato dal nodo, escludendo quello dei discendenti.  
Progettare un algoritmo `diskSpace` che: dato un tale T calcoli, per ogni nodo v ∈ T, lo spazio aggregato occupato dai suoi discendenti e lo memorizzi in un campo `v.aggr-size`.  
Descrivere il pseudocodice (suggerimento: visita in postorder) e analizzarne la complessità.

---
