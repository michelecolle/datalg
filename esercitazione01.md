## Esercizio 1
**algoritmo** `sumMul(A,B)`

**input** `A`, `B` array di dimensione `n` ed `m`
**output** prodotto matriciale tra a e una matrice `m x n` di vettori riga B identici
```
sum <- 0
for i <- 0 to n-1 do
  for j <- 0 to m-1 do
    sum += A[i]*B[j]
return sum
```
## Esercizio 2
**algoritmo** `IndexOfSequential(A,x)`

**input** `A` array di interi ordinati di dimensione `n`, `x` intero da cercare

**output** indice `i` tale che `A[i] = x` se `x` appartiene ad `A`, `-1` altrimenti
```
for i <- 0 to n-1 do
  if A[i] > x return -1
  if A[i] = x return i
return -1
```

**algoritmo** `IndexOfRecursive(A,x,begin,end)`

**input** `A` array di interi ordinati di dimensione `n`, `x`: intero da cercare, `(begin, end)` indici di inizio e fine della porzione dell'array in cui effettuare la ricerca. NB `begin, end in [0, n-1]` 

**output** indice `i` tale che `A[i] = x` se `x in A`, `-1` altrimenti
```
if A[begin] = x then return begin
if A[end] = x then return end
if end = begin +1 then return -1

int middle = floor((begin + end)/2) 
if A[middle]>x then IndexOfRecursive(A, x, begin, middle)
else IndexOfRecursive(A, x, middle, end)
  
```

## PS 

Mi scuso per il ritardo nella consegna, ho letto la email velocemente e non avevo capito che la consegna sarebbe stata su moodle esami.