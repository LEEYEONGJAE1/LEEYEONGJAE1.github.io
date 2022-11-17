---
layout: post
title: Möbius function & Mertens function
use_math: true
math : true
published: true
---
# 뫼비우스 함수

### description

$\mu(n)=$

$n$이 제곱 인수(제곱수인 인수)를 가지고 있을 경우 0,

그렇지 않을 경우 $n$의 소인수의 개수가 $k$라고 할 때, $(-1)^k$

즉, 소인수의 개수가 홀수일 경우 -1, 짝수일 경우 1

### code

```c++
mobius[1]=1;
for(int i=1;i<=n;i++){
    for(int j=i+i;j<=n;j+=i){
        mobius[j]-=mobius[i];
    }
}
```

# 메르텐스 함수

### description

1부터 n까지 제곱 인수를 가지지 않는 수(Square-free integer)의 개수를 뜻한다.
$M(n)=\sum_{k=1}^{n}{\mu(k)}$

### code

```c++
ll mertens(ll n){
    ll cnt=0;
    for(int i=1;i*i<=n;i++){
        cnt+=mobius[i]*n/(i*i);
    }
    return cnt;
}
```