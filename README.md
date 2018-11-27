# Computer-Science
## Resumo sobre Ciência da Computação

#### Sumário
1. Estruturas de Dados
   1. Filas
   2. Pilhas
   3. Hash
   4. Árvores
   5. Grafos
   6. Dicionários

2. Sorts
   1. QuickSort
   2. MergeSort
   3. HeapSort


#### Estruturas de Dados
Uma **estrutura de dados** é uma coleção de valores e operações sobre tais valores. É uma implementação concreta de um **tipo abstrato de dado (TAD)**. Por exemplo, poderiamos definir uma estrutura de dados para representar uma *pessoa*, em pseudo-código, da seguinte forma:
```
Pessoa = {
  Nome
  Idade
  Altura
}

realizarAniversario(Pessoa pessoa1) = {
  pessoa1.Idade = pessoa1.Idade + 1
}
```

###### Filas
Uma fila é uma coleção de elementos encadeados cuja ideia principal é que só podemos _inserir um novo elemento no **final**_ da fila e só podemos _retirar um elemento do **inicio**_ da fila. Dessa forma, uma fila é uma estrutura do tipo **FIFO**, que significa **First In, First Out**.
Exemplo em python:
```python
fila = [10, 20, 30, 40, 50]
fila.append(60) # Insere um elemento no final da fila
print fila
>>> [10, 20, 30, 40, 50, 60]
fila.pop(0) # Remove o primeiro elemento da fila
print fila
>>> [20, 30, 40, 50, 60]
```

###### Pilhas

###### Hash

###### Árvores

###### Grafos

###### Dicionários

#### Sorts

###### QuickSort

###### MergeSort

###### HeapSort
