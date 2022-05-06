---
layout: post
title: 알고리즘 & 자료구조 - 그래프(Graph)
categories: Algorithm-DataStructure
tags: graph
---

## **개념**

그래프는 1개 이상의 정점 (vertex / node)들과 0개 이상의 간선 (edge)들로 이루어진 자료구조입니다. 

<img src = "https://github.com/changhoji/changhoji.github.io/blob/main/assets/images/graph/undirected-graph.png?raw=true" width = "30%" height = "70%" alt="undirected graph">

~~~
정점: A, B, C
간선: 2개 (A와 B를 잇는 간선, A와 A를 잇는 간선)
~~~

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

~~~
degree of vertex: 정점에 연결된 간선의 개수

in-degree (deg-): 해당 정점이 도착지인 간선의 개수

out-degree (deg+): 해당 정점이 출발지인 간선의 개수
~~~

ex) [그림(1)](#그래프의-종류)에서 degree of A = 3, degree of B = 1

ex) [그림(2)](#그래프의-종류)에서 deg<sup>-</sup>(A) = 1, deg<sup>+</sup>(A) = 2, deg<sup>-</sup>(B) = 1, deg<sup>+</sup>(B) = 0

---

## **표현**

### 1. 인접행렬

그래프가 n개의 정점을 가질 때 n*n의 2차원 배열을 생성해 정보를 저장합니다.

~~~
int adjMatrix[10][10];

adjMatrix[i][j] = 1 (i정점에서 j정점으로 가는 간선이 존재)
          = 0 (그런 간선이 존재하지 않음)
~~~

**예시**

<img src = "https://github.com/changhoji/changhoji.github.io/blob/main/assets/images/graph/adj-matrix.png?raw=true" width="50%">

위 그래프에 대한 인접행렬은 다음과 같이 표현할 수 있습니다.

| \ | 1 | 2 | 3 | 4 | 5 |
|---|---|---|---|---|---|
| 1 | 0 | 0 | 1 | 0 | 1 |
| 2 | 0 | 0 | 0 | 0 | 1 |
| 3 | 1 | 0 | 0 | 1 | 1 |
| 4 | 0 | 0 | 1 | 0 | 0 |
| 5 | 1 | 1 | 1 | 0 | 0 |

~~~
방향 그래프도 같은 방식으로 표현할 수 있습니다.

가중 그래프의 경우 간선이 존재하면 그 간선의 가중치를 1 대신 적어서 표현할 수 있습니다.
~~~

### 2. 인접리스트

인접행렬로 표현하면 특정 정점 사이에 간선이 존재하는지 바로 알 수 있다는 장점이 있지만, 아무래도 메모리를 많이 사용한다는 단점이 있습니다. 

인접리스트는 해당 정점에서 이웃한 정점들을 저장하고, 이를 표현하기 위해 vector를 사용할 수 있습니다.

~~~
vector<int> adjList[5];

adjMatrix[1][3] = 1 이면 -> adjList[1].push_back(3); 과 같이 처리합니다.
~~~

위 표를 인접리스트로 나타내면 다음과 같습니다.

| adjList[i] |   |   |   |
|:---:|---|---|---|
| 1 | 3 | 5 |
| 2 | 5 |
| 3 | 1 | 4 | 5 |
| 4 | 3 |
| 5 | 1 | 2 | 3 |

adjMatrix에서 값이 0이던 부분을 생략하므로 메모리와 순회 시간을 아낄 수 있습니다.

~~~
가중 그래프에서는 vector<int> adjList[5]; 대신

vector<pair<int, int>> adjList[5]; 와 같이 선언하고

vector에 들어가는 pair의 first를 연결된 정점의 번호로, second를 간선의 가중치로 표현할 수 있습니다.
~~~

---

## **탐색**

### 1. DFS

### 2. BFS
