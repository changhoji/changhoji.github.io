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
int adj[10][10];

adj[i][j] = 1 (i정점에서 j정점으로 가는 간선이 존재)
          = 0 (그런 간선이 존재하지 않음)
~~~

**예시**

<Graph indexType="custom" height="400" width="400" nodes={[{label:0,center:{x:248.4,y:157.7}},{label:1,center:{x:236.7,y:286.7}},{label:2,center:{x:172.9,y:155.7}},{label:3,center:{x:138.1,y:223.4}},{label:4,center:{x:208.4,y:220.1}},{label:5,center:{x:281.8,y:225.4}}]} edges={[{source:0,target:2},{source:0,target:4},{source:0,target:5},{source:1,target:4},{source:1,target:5},{source:2,target:3},{source:2,target:4},{source:4,target:5}]} />

위 그래프에 대한 인접행렬은 다음과 같이 표현할 수 있습니다.

| \ | 1 | 2 | 3 | 4 |
|---|---|---|---|---|
| 1 | 
| 2 |
| 3 |
| 4 |

### 인접리스트



---

## **탐색**
