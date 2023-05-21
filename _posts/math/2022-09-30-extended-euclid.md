---
layout: post
title: Extended Euclid Algorithm
use_math: true
math : true
published: true
---
# 확장 유클리드 알고리즘

### description

$ax+by=gcd(a,b)$의 배수 를 만족하는 $(x,y)$를 구하는 알고리즘

### usage

1. 그냥 사용법 그대로 $(x,y)$구하기
2. 모듈러 연산의 역원 구하기
3. $\dots$(추가 예정)

### x,y 구하기

```c++
int eea(int a, int b, int& x, int& y) {
    if (b == 0) {
        x = 1;
        y = 0;
        return a;
    }
    int x1, y1;
    int d = eea(b, a % b, x1, y1);
    x = y1;
    y = x1 - y1 * (a / b);
    return d;
}
```

reference: [https://cp-algorithms.com/algebra/extended-euclid-algorithm.html#algorithm](https://cp-algorithms.com/algebra/extended-euclid-algorithm.html#algorithm)

### 모듈러 연산 역원 구하기

서로소인 $a$와 $p$가 주어졌을 때,

$ax= 1(\mod p)$인 $x$가 $a$의 모듈러 역원이 된다. (곱해서 1이 되기 때문에)

확장 유클리드 알고리즘은 $ax+py=1$(gcd(a,p)=1)일때 $(x,y)$를 구해주는데, 

이때 구한 $(x,y)$를 $(x',y')$라고 하면

$ax'+py'=1$이 된다.

양변에 $\mod p$를 하면

$ax'=1 (\mod p)$가 되므로 

구한 $x'$가 모듈러 역원이 된다. 

```c++
int eea(int a, int b, int& x, int& y) {
    if (b == 0) {
        x = 1;
        y = 0;
        return a;
    }
    int x1, y1;
    int d = eea(b, a % b, x1, y1);
    x = y1;
    y = x1 - y1 * (a / b);
    return d;
}
int inv(int a,int p){
    int x,y;
    eea(a,p,x,y);
    while(x<0)x+=p;
    return x;
}
```

