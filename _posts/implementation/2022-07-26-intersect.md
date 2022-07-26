---
layout: post
title: "Intersect"
implementation: true
published: true
use_math: true
---

### 절댓값 구역 교차

[이 문제](https://codeforces.com/contest/1711/problem/D)에서 등장

![이미지](\assets\images\codeforces\1711\D-1.png){: width="30%" height="30%"}

저렇게 생긴 주황색 구역 교차
```c++
pl getIntersect(pl p1, pl p2) {
    ll tx = max(p1.first + p1.second, p2.first + p2.second);
    ll ty = max(p1.second - p1.first, p2.second - p2.first);
    return { (tx - ty) / 2,(tx + ty) / 2 };
}
```