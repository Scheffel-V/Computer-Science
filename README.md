# Computer-Science
## Resumo sobre Ciência da Computação

### Sumário
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


### Estruturas de Dados
Uma **estrutura de dados** é uma coleção de valores e operações sobre tais valores. É uma implementação concreta de um **tipo abstrato de dado (TAD)**. Existem estruturas de dados comumente utilizadas como filas, pilhas, grafos, mas poderiamos definir uma estrutura de dados genérica para representar, por exemplo, uma *pessoa*:
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

#### Filas
Uma fila é uma coleção de elementos encadeados cuja ideia principal é que só podemos _inserir um novo elemento no **final**_ da fila e só podemos _retirar um elemento do **início**_ da fila. Dessa forma, uma fila é baseada no princípio **FIFO**, que significa **First In, First Out**.
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

#### Pilhas
Uma pilha é uma coleção de elementos encadeados cuja ideia principal é que só podemos _inserir um novo elemento no **final**_ da pilha e só podemos _retirar um elemento do **final**_ da fila. Dessa forma, uma pilha é baseada no princípio **FILO**, que singifica **First In, Last Out**.
Exemplo em python:
```python
pilha = [10, 20, 30, 40, 50]
pilha.append(60) # Insere um elemento no final da pilha
print pilha
>>> [10, 20, 30, 40, 50, 60]
pilha.pop() # Remove o último elemento da pilha
print pilha
>>> [10, 20, 30, 40, 50]
```
* Complexidade da operação append(): **O(1)**
* Complexidade da operação pop(): **O(1)**

É possível implementar uma fila com duas pilhas da seguinte forma:
*Toda vez que um elemento for inserido, ele é inserido normalmente na primeira pilha. 
*Toda vez que um elemento for retirado, todos os elementos da primeira pilha são colocados na segunda pilha, de forma que o último elemento da segunda pilha seja o primeiro da primeira. Então, o último elemento da segunda pilha é retirado através da operação .pop(). Depois disso, precisamos retornar todos os elementos da segunda pilha para a primeira pilha.
```python
stack1 = Stack()
stack2 = Stack()

## append(e) method:
def append(e):
   stack1.append(e)
   
##pop(0) method:
def pop(i):
  while not stack1.isEmpty():
    element = stack1.pop()
    stack2.append(element)
  
  elementToReturn = stack2.pop()
  
  while not stack2.isEmpty():
    element = stack2.pop()
    stack1.append(element)
  
  return elementToReturn
```
* Complexidade da operação append(): **O(1)**
* Complexidade da operação pop(0): **O(n)**

#### Hash

#### Árvores

#### Grafos

#### Dicionários

### Sorts

#### QuickSort

#### MergeSort

#### HeapSort
