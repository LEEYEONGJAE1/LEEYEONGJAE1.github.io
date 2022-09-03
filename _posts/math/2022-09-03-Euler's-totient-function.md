---
layout: post
title: Euler's totient function 오일러 피 함수 
math: true
published: true
use_math: true
---
# 오일러 피 함수

### 오일러 피 함수란?
$\phi(n)=$1이상 n이하의 정수 중 n과 서로소인 수의 개수

### 소스 코드
$1 \leq i \leq n$인 $i$에 대해 $\phi(i)$를 $O(n\log{n})$으로 구하기
```cpp
for (int i = 1; i <= n; ++i) {
    phi[i] += i;
    for (int j = 2 * i; j <= n; j += i) {
        phi[j] -= phi[i];
    }
}
```
