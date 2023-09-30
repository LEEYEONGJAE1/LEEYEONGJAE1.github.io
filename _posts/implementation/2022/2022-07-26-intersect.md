---
layout: post
implementation: true
published: true
use_math: true
---

### 절댓값 구역 교차

[이 문제](https://codeforces.com/contest/1711/problem/D)에서 등장

[이 문제](https://codeforces.com/contest/1730/problem/B)에서도 사용함

![이미지](\assets\images\codeforces\1711\D-1.png){: width="30%" height="30%"}

저렇게 생긴 주황색 구역 교차

---
c++
```c++
pl getIntersect(pl p1, pl p2) {
    ll tx = max(p1.first + p1.second, p2.first + p2.second);
    ll ty = max(p1.second - p1.first, p2.second - p2.first);
    return { (tx - ty) / 2,(tx + ty) / 2 };
}
```
---
python
```python
def getIntersect(a,b):
    tx = max( a[0] + a[1], b[0] + b[1] );
    ty = max( a[1] - a[0], b[1] - b[0] );
    return  ((tx - ty) / 2,(tx + ty) / 2) ;
```