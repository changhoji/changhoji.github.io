---
layout: post
title: 알고리즘 & 자료구조 - 그래프(Graph)
categories: Algorithm-DataStructure
tags: graph
---

## **개념**

그래프는 1개 이상의 정점 (vertex / node)들과 0개 이상의 간선 (edge)들로 이루어진 자료구조입니다. 

<img src = "https://github.com/changhoji/changhoji.github.io/blob/main/assets/images/graph/undirected-graph.png?raw=true" width = "30%" height = "70%" alt="undirected graph">


- 정점: A, B, C
- 간선: 2개 (A와 B를 잇는 간선, A와 A를 잇는 간선)


---



## **그래프의 종류**
- Undirected Graph (무방향 그래프): 방향이 없는 간선들로 이루어진 그래프

<img src = "https://github.com/changhoji/changhoji.github.io/blob/main/assets/images/graph/undirected-graph.png?raw=true" width = "30%" height = "70%" alt="undirected graph"> (1)

- Directed Graph (방향 그래프): 간선에 방향이 존재하는 그래프

<img src = "https://github.com/changhoji/changhoji.github.io/blob/main/assets/images/graph/directed-graph.png?raw=true" width = "30%"> (2)

- Weighted Graph (가중 그래프): 간선에 가중치가 존재하는 그래프 (Undirected Graph도 Weighted Graph가 될 수 있음)

<img src = "https://github.com/changhoji/changhoji.github.io/blob/main/assets/images/graph/weighted-graph.png?raw=true" width = "30%"> (3)

- 그 외에 simple graph, multigraphs, pseudo graph 등이 존재합니다.

---

## **정점의 degree**

- degree of vertex: 정점에 연결된 간선의 개수
- in-degree (deg<sup>-</sup>): 해당 정점이 도착지인 간선의 개수
- out-degree (deg<sup>+</sup>): 해당 정점이 출발지인 간선의 개수

ex) [그림(1)](#그래프의-종류)에서 degree of A = 3, degree of B = 1

ex) [그림(2)](#그래프의-종류)에서 deg<sup>-</sup>(A) = 1, deg<sup>+</sup>(A) = 2, deg<sup>-</sup>(B) = 1, deg<sup>+</sup>(B) = 0

---


즉 진행하면서 더이상 갈 곳이 없을 때까지 탐색한 뒤, 다시 뒤로 돌아오는 방식이기 때문에 스택, 재귀를 이용해 구현할 수 있습니다.  

---

스택을 이용할 때 작동 방식에 대해 알아보겠습니다. (오른쪽을 top으로 생각하겠습니다.)

주의할 점은 stack에 정점 번호를 push할 때가 아닌 **pop할 때** 그 정점을 탐색합니다.

시작 노드를 스택에 push합니다.  
| 1 |
|---|

<image src = "https://github.com/changhoji/changhoji.github.io/blob/main/assets/images/graph/DFS/1.png?raw=true" width="70%">

stack에서 pop을 하고(1) 그곳에서 연결된 정점들(2, 4, 5)을 stack에 push합니다.

이때 2, 4, 5 순서대로 push하지 않고 5, 4, 2 순서대로 push하는 이유는 그림의 순서대로 탐색하게 하기 위해서 입니다. (2, 4, 5 순서대로 push해도 dfs를 하는데는 문제 없습니다.)  

| 5 | 4 | 2 |
|---|---|---|

<image src = "https://github.com/changhoji/changhoji.github.io/blob/main/assets/images/graph/DFS/2.png?raw=true" width="70%">

stack에서 pop을 하고(2) 그곳에서 연결된 정점(3)을 stack에 push합니다.  

| 5 | 4 | 3 |
|---|---|---|


<image src = "https://github.com/changhoji/changhoji.github.io/blob/main/assets/images/graph/DFS/3.png?raw=true" width="70%">

stack에서 pop을 합니다. (3)

다만 이때 3번 정점에서 더 갈 수 있는 정점이 없기 때문에 push하지 않습니다.  

| 5 | 4 |
|---|---|

<image src = "https://github.com/changhoji/changhoji.github.io/blob/main/assets/images/graph/DFS/4.png?raw=true" width="70%">

stack에서 pop을 합니다. (4)

다만 이때 4번 정점에서 더 갈 수 있는 정점이 없기 때문에 push하지 않습니다.  

| 5 |
|---|

<image src = "https://github.com/changhoji/changhoji.github.io/blob/main/assets/images/graph/DFS/5.png?raw=true" width="70%">

stack에서 pop을 하고(5) 그곳에서 연결된 정점(6)을 stack에 push합니다.  

| 6 |
|---|

<image src = "https://github.com/changhoji/changhoji.github.io/blob/main/assets/images/graph/DFS/6.png?raw=true" width="70%">

stack에서 pop을 하고(6) 그곳에서 연결된 정점(7)을 stack에 push합니다.  

| 7 |
|---|

<image src = "https://github.com/changhoji/changhoji.github.io/blob/main/assets/images/graph/DFS/7.png?raw=true" width="70%">

stack에서 pop을 합니다. stack을 다 비웠기 때문에 탐색을 종료합니다.  

---

### DFS 코드

<details>
<summary> DFS_STACK_CODE </summary>

<div markdown="1">

```C++
#include <iostream>
#include <stack>
#define MAX_NODE 50
using namespace std;

int N;
bool visited[MAX_NODE+1] = { false,};
int adjMatrix[MAX_NODE+1][MAX_NODE+1] = { 0,};

~~~
//N 입력받기
//adjMatrix 설정
~~~

void DFS(int start) {
    stack<int> s;

    s.push(start);
    visited[start] = true;
    
    while (!s.empty()) {
        int cur = s.top();
        s.pop();

        cout << cur << " ";

        for (int i = N; i >= 1; i--) { //다음 방문할 정점 살펴보기
            if (adjMatrix[cur][i] == 1 && visited[i] == false) {
                visited[i] = true;
                s.push(i);
            }
        }
    }
}
```
</div>
</details>


또는 재귀로 구현할 수도 있습니다.

<details>
<summary> DFS_RECURSION_CODE </summary>

<div markdown = "1">

```C++
#include <iostream>
#define MAX_NODE 50
using namespace std;

int N;
bool visited[MAX_NODE+1] = { false,};
int adjMatrix[MAX_NODE+1][MAX_NODE+1] = { 0,};

~~~
//N 입력받기
//adjMatrix 설정
~~~

void DFS(int start) {
    cout << start << ' ';
    visited[start] = true;
    
    for (int i = 1; i <= N; i++) { //i=다음 방문할 정점
        if (visited[i]) continue;  //이미 방문했거나
        if (!adjMatrix[start][i]) continue;  //연결되어있지 않으면 건너뛰기

        DFS(i);
    }
}
```

</div>
</details>






### 2. BFS
