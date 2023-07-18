---
layout: post
implementation: true
published: true
use_math: true
---

# 삼분탐색

## unimodal function

![](https://media.geeksforgeeks.org/wp-content/uploads/unimodal.jpeg)

Unimodal Function이란?:

함수 $f(x)$는 어떤 $m$값에 대해 $x \leq m$인 $x$에서 monotonically increasing(단조 증가)하고, $x \geq m$인 $x$에서 monotonically decreasing(단조 감소)하고, 함수 $f(x)$에서 최댓값이 $f(m)$ 이고 local maximum값이 존재하지 않을 때 unimodal이다. (반대도 가능)

## 삼분탐색

**unimodal**한 함수 $f(x)$의 $[l,r]$구간에서 최댓값(최솟값)을 찾는 방법이다. 

### 구현

int 범위에서
```cpp
int lo = L, hi = R;
while(hi-lo >= 3){
        int p = (lo*2 + hi)/3, q = (lo + hi*2)/3;
        if(f(p) <= f(q)) hi = q;
        else lo = p;
}
// 최종 구간 [lo, hi] 안에서 최솟값을 찾아냄
long long result = INF;
for(int i = lo; i <= hi; ++i)
    result = min(f(i), result);
//[출처] 삼분 탐색(Ternary Search)|작성자 라이
```

---

double 범위에서
```c++
double ternary_search(double l, double r) {
    double eps = 1e-9;              //set the error limit here
    while (r - l > eps) {
        double m1 = l + (r - l) / 3;
        double m2 = r - (r - l) / 3;
        double f1 = f(m1);      //evaluates the function at m1
        double f2 = f(m2);      //evaluates the function at m2
        if (f1 < f2)
            l = m1;
        else
            r = m2;
    }
    return f(l);                    //return the maximum of f(x) in [l, r]
}
```

---

reference: 
* [https://www.geeksforgeeks.org/mathematics-unimodal-functions-bimodal-functions/](https://www.geeksforgeeks.org/mathematics-unimodal-functions-bimodal-functions/)
* [https://cp-algorithms.com/num_methods/ternary_search.html](https://cp-algorithms.com/num_methods/ternary_search.html)
* [https://blog.naver.com/kks227/221432986308](https://blog.naver.com/kks227/221432986308)