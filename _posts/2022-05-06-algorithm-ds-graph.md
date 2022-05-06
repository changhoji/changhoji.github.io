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

### 인접행렬

| \ | 1 | 2 | 3 | 4 |
|---|---|---|---|---|
| 1 | 
| 2 |
| 3 |
| 4 |

### 인접리스트



---

## **탐색**
