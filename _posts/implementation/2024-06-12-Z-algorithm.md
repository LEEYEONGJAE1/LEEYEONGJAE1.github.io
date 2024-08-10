---
layout: post
title: Z algorithm
implementation: true
published: true
use_math: true
---
# Z Algorithm

주어진 문자열 $S$의 prefix와 $S_i$에서 시작하는 substring과 최대 몇 개까지 같은지 나타내는 $Z$를 $O(n)$의 시간복잡도로 구해주는 알고리즘  

$S_0 = S_i, S_1=S_{i+1}, \dots, S_{Z_i} = S_{i+Z_i}$인 $Z_i$의 최댓값

```c++
vector<int> Z;
void f(string str) {
    int n = str.length();
    Z.clear();
    Z.resize(n);
    int L, R, k;
    L = R = 0;
    for (int i = 1; i < n; ++i) {
        if (i > R) {
            L = R = i;
            while (R < n && str[R - L] == str[R])
                R++;
            Z[i] = R - L;
            R--;
        }
        else {
            k = i - L;
            if (Z[k] < R - i + 1) Z[i] = Z[k];
            else {
                L = i;
                while (R < n && str[R - L] == str[R])
                    R++;
                Z[i] = R - L;
                R--;
            }
        }
    }
}
```

reference: 
* [Z algorithm (Linear time pattern searching Algorithm) ](https://www.geeksforgeeks.org/z-algorithm-linear-time-pattern-searching-algorithm/)