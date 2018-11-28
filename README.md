# Resumo sobre Ciência da Computação

## Sumário
1. [Estruturas de Dados](https://github.com/Scheffel-V/Computer-Science#estruturas-de-dados)
   1. [Filas](https://github.com/Scheffel-V/Computer-Science#filas)
   2. [Pilhas](https://github.com/Scheffel-V/Computer-Science#pilhas)
   3. [Hash](https://github.com/Scheffel-V/Computer-Science#hash)
   4. [Árvores](https://github.com/Scheffel-V/Computer-Science#árvores)
   5. [Grafos](https://github.com/Scheffel-V/Computer-Science#grafos)
      1. [Armazenamento em Memória](https://github.com/Scheffel-V/Computer-Science#armazenamento-em-memória)
      2. [Caminho](https://github.com/Scheffel-V/Computer-Science#caminho)
      3. [Busca em Grafos](https://github.com/Scheffel-V/Computer-Science#busca-em-grafos)
      4. [Algoritmo de Dijkstra](https://github.com/Scheffel-V/Computer-Science#algoritmo-de-dijkstra)
      5. [Algoritmo de Kruskal](https://github.com/Scheffel-V/Computer-Science#algoritmo-de-kruskal)
      6. [Algoritmo de Prim](https://github.com/Scheffel-V/Computer-Science#algoritmo-de-prim)
   6. [Dicionários](https://github.com/Scheffel-V/Computer-Science#dicionários)

2. [Sorts](https://github.com/Scheffel-V/Computer-Science#sorts)
   1. [QuickSort](https://github.com/Scheffel-V/Computer-Science#quicksort)
   2. [MergeSort](https://github.com/Scheffel-V/Computer-Science#mergesort)
   3. [HeapSort](https://github.com/Scheffel-V/Computer-Science#pilhas#heapsort)


## Estruturas de Dados
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

### Filas
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
* Complexidade da operação append(): **O(1)**
* Complexidade da operação pop(0): **O(1)**

### Pilhas
Uma pilha é uma coleção de elementos encadeados cuja ideia principal é que só podemos _inserir um novo elemento no **final**_ da pilha e só podemos _retirar um elemento do **final**_ da pilha. Dessa forma, uma pilha é baseada no princípio **FILO**, que singifica **First In, Last Out**.
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

#### É possível implementar uma fila com duas pilhas da seguinte forma:
* Toda vez que um elemento for inserido, ele é inserido normalmente na primeira pilha. 
* Toda vez que um elemento for retirado, todos os elementos da primeira pilha são colocados na segunda pilha, de forma que o último elemento da segunda pilha seja o primeiro da primeira. Então, o último elemento da segunda pilha é retirado através da operação .pop(). Depois disso, precisamos retornar todos os elementos da segunda pilha para a primeira pilha.
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

### Hash

### Árvores

### Grafos
Um grafo é uma estrutura de dados, **G(V, E)**, onde **V** representa um conjunto *não-vazio* de **vértices** (também conhecidos como *nodos*), e **E** representa um subconjunto de **arestas**, que são pares de elementos do conjunto **V**.
* Arestas podem ter direção, de forma que a aresta *(V1, V2)* seja diferente da aresta *(V2, V1)*. Os grafos que possuem arestas com uma direção, são chamados de **dígrafos**.
* Arestas podem ter peso, isto é, um valor numérico associado à elas.

![Imagem do Grafo](https://raw.githubusercontent.com/Scheffel-V/Computer-Science/master/grafo.png)
> Um exemplo de um grafo não-direcionado de 6 vértices e 7 arestas.

#### Armazenamento em Memória
Há diferentes formas de armazenar o grafo na memória:
- Estruturas do tipo **lista** são frequentemente usadas em grafos *esparsos* já que exigem *menor uso da memória*.
  - Lista de adjacência: associa a *cada vértice* do grafo uma *lista* de todos os *outros vértices* com os quais ele *tem uma aresta*. 
  - Lista de incidência: armazena para *cada vértice* uma *lista* de objetos que representam as *arestas incidentes a esse vértice*.

- Estruturas do tipo **matriz** fornecem um *rápido acesso* em algumas aplicações, mas podem consumir uma *grande quantidade de memória*.
  - Matriz de incidência: linhas representando *vértices* e colunas representando *arestas*.
  - Matriz de adjacência: ambas linhas e colunas representam *vértices*. 
  - Em ambos casos um 1 indica dois objetos adjacentes e 0 indica dois objetos não adjacentes.

#### Caminho
Caminho é uma *sequência de vértices* tal que para cada um dos vértices, existe uma *aresta entre esse e o vértice seguinte*.
No grafo de exemplo, o caminho (6, 4, 5, 2) é um caminho de comprimento 3.

* Caminho euleriano: caminho que usa cada **aresta** exatamente *uma vez*. Se tal caminho existir, o grafo é chamado *traversável*.
* Caminho hamiltoniano: caminho que visita cada **vértice** exatamente *uma vez*.

**Ciclo** é um caminho que começa e acaba com o mesmo vértice. Um *ciclo simples* é um ciclo que tem *comprimento maior ou igual à 3*, e no qual o *vértice inicial* aparece uma segunda vez como *vértice final*, e todos os outros do ciclo aparecem *uma vez*.

#### Busca em Grafos
- Busca em largura (Breadth-First Search ou BFS): visitar *todos os nós do nível n*, e só **depois** ir para o nível n+1. Utilizando uma **fila**: depois que um nó é visitado, s*eus filhos são colocados no final da fila* e o nó no início da fila é visitado. Assim, os nós do nível n+1 serão visitados somente *depois* de ter visitados todos os nós do nível n. 
- Busca em profundidade (Depth-first search ou DFS): visitar *todos os filhos do nó inicial*, sempre tentanto se *aprofundar* ao máximo, até que se encontre o nó desejado. Se chegar no *último nível* (nó folha), retrocede (backtrack) e começa no próximo nó.  Numa implementação não-recursiva, *todos os nós expandidos recentemente* são adicionados a uma **pilha**, para realizar a exploração.
  - A **complexidade espacial** de um algoritmo de *busca em profundidade* é **muito menor** que a de um algoritmo de *busca em largura*. 
  - A **complexidade temporal** de *ambos algoritmos* são proporcionais ao *número de vértices somados ao número de arestas* dos grafos aos quais eles atravessam.

#### Algoritmo de Dijkstra

#### Algoritmo de Kruskal

#### Algoritmo de Prim


### Dicionários

## Sorts

### QuickSort

### MergeSort

### HeapSort
