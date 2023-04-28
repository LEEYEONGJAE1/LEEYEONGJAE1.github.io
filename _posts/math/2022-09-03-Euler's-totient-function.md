---
layout: post
title: Euler's totient function
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
그냥 구하기
```c++
int phi(int n) {
    int ret = n;
    for (int i = 2; i * i <= n; i++) {
        if (n % i == 0) {
            ret = ret / i * (i - 1);
        }
        while (n % i == 0) {
            n /= i;
        }
    }
    if (n > 1) ret = ret / n * (n - 1);
    return ret;
}
```
