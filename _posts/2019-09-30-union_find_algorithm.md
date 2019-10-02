---
title: "Union find algorithm"
date: 2019-09-30 00:41:00 -0400
categories: algorithm graph disjoint-set
---

집합의 원소들을 교집합이 없는 상호 배타적인 부분 집합들로 분류하는 것을 목적으로 한다.(disjoint set)  
Tree 구조 Graph로 구현하는 것이 가장 효과적이다.  

연산  
MakeSet(node) : node를 유일한 원소로 갖는 집합 생성. 전 원소에 걸쳐 수행함으로써 초기화.    
Union(node1, node2) : node1이 속한 집합과 node2가 속한 집합을 합침.  
Find(node) : node가 속한 집합을 찾아낸다. (Root node 반환.)  
