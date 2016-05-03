---
layout: post
title: 군집화와 KMeans
categories: [general, machine learning]
tags: [machine learning, kmeans]
fullview: false
comments: true
---


대부분 군집화 알고리즘은 수평flat 군집화와 계층hierarchical 군집화라는 두 가지 종류로 나뉜다.

수평 군집하ㅗ는 게시물을 군집 서로 간의 관계와 상관없이 군집 집합으로 나눈다. 목적은 간단하다. 같은 군집에 있는 모든 게시물은 최대한 서로 유사하게 하는 반면, 다른 군집에 있는 게시물과는 차이가 나도록 위치시키는 것이다. 수평 군집화 알고리즘은 특정 군집 개수를 알려줘야 한다.

계층 군집화는 군집 개수를 알지 못해도 상관없다. 대신에 계층 군집화는 계층을 만든다. 비슷한 게시물끼리 그룹을 만들어 하나의 군집을 만들고 다시 이 군집과 다른 군집을 그룹으로 만들어 반복적으로 하나의 군집이 남을 때까지 수행한다. 이 계층에서 원하는 군집 개수를 정할 수 있지만 효율성이 떨어진다.

<br>

# KMeans

**K평균Kmeans** 은 수평 군집화 알고리즘으로 가장 잘 사용된다. 원하는 군집의 개수 num_clusters로 초기화한 후, 소위 군집 중앙점centroids을 관리한다. 처음에, num_clusters를 선택해 속성 벡터를 중앙점으로 설정한다. 다른 모든 게시물에 대해 조사하여 현재 군집으로서 가장 가까운 중앙점을 게시물의 군집으로 지정한다. 특정 범주의 모든 게시물의 중앙으로 중앙점을 이동한다. 물론 다시 중앙점이 군집 지정을 변경해야 한다. 일부 게시물은 다른 군집에 가까워진다. 그래서 이러한 변화된 게시물에 대해 준집 지정을 갱신한다. 이 과정은 중앙점이 상당히 많이 이동하는 한 계속된다. 일정 반복 후에 움직임은 경계 아래로 내려가고 군집화되었다고 생각한다.