# Algoritmo de Busca em Largura (BFS)

## Introdução
O algoritmo de Busca em Largura (BFS, do inglês Breadth-First Search) é uma técnica de travessia de grafos que explora os vizinhos de um nó antes de visitar os vizinhos dos vizinhos.

## Funcionamento
1. Começa pelo nó inicial e marca como visitado.
2. Todos os vizinhos não visitados são adicionados à fila.
3. Retira-se um nó da fila, marca-se como visitado e repete-se o processo para seus vizinhos.

## Código
O código abaixo demonstra a implementação do BFS em C++:

```cpp
#include<bits/stdc++.h>
using namespace std;

void bfs(int inicio, vector<vector<int>> &grafo, vector<bool> &no_visitado){
    queue<int> fila;
    no_visitado[inicio] = true;
    fila.push(inicio);
    
    while(!fila.empty()){
        int no_atual = fila.front();
        fila.pop();
        
        cout << no_atual << " ";
        
        for(int visinho : grafo[no_atual]){
            if(!no_visitado[visinho]){
                no_visitado[visinho] = true;
                fila.push(visinho);
            }
        }
    }
}

int main()
{
    vector<vector<int>> grafo = {{1,2}, {0,2}, {0,1,3}, {2}};
    int n = grafo.size();
    vector<bool> no_visitado(n, false);
    bfs(0, grafo, no_visitado);
    return 0;
}
