## Esercizio pag 1: InsertionSort

``` python
Algoritmo InsertionSort(S)
input Sequenza S[0 . . . n-1] di n chiavi
output Sequenza S ordinata in senso crescente

for i ←− 1 to n-1 do {
curr ←− S[i]
j ←− i-1
while ((j ≥ 0) AND (S[j]> curr)) do {
S[j+1] ←− S[j]
j ←− j-1
}
S[j+1] ←− curr
}
```

1. Trovare delle opportune funzioni f1(n), f2(n) e f3(n) tali che le
seguenti affermazioni siano vere, per una qualche costante c > 0 e
per n abbastanza grande.

• Per ciascuna istanza di taglia n l’algoritmo esegue ≤ cf1(n)
operazioni.

• Per ciascuna istanza di taglia n l’algoritmo esegue ≥ cf2(n)
operazioni.

• Esiste una istanza di taglia n per la quale l’algoritmo esegue
≥ cf3(n) operazioni.

La funzione f1(n) deve essere la piu piccola possibile, mentre le
funzioni f2(n) e f3(n) devono essere le pi`u grandi possibili.

2. Sia `t_IS(n)` la complessita al caso pessimo dell’algoritmo. Sfruttando
le affermazioni del punto precedente trovare un upper bound O (·) e
un lower bound Ω (·) per `t_IS(n)`.
