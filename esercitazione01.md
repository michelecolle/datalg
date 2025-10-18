## Esercizio 1
**algoritmo** sumMul
**input** A, B array di dimensione n ed m
**output** prodotto matriciale tra a e una matrice m x n di vettori b identici
```
sum <- 0
for i <- 0 to n-1 do
  for j <- 0 to m-1 do
    sum += A[i]*B[j]
return sum
```
## Esercizio 2
**algoritmo** IndexOfSequential
**input** A array di interi ordinati di dimensione n, x: intero
**output** indice i tale che A[i] = x se x appartiene ad A, -1 altrimenti
```
for i <- 0 to n-1 do
  if A[i] > x return -1
  if A[i] = x return i
return -1
```

**algoritmo** IndexOfRecursive
**input** A array di interi ordinati di dimensione n, x: intero
**output** indice i tale che A[i] = x se x appartiene ad A, -1 altrimenti
```
def isBigger(A, x, i)
  if A
  
```
