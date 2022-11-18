---
layout: post
title: Miller-Rabin primality test
use_math: true
math : true
published: true
---
# 밀러 라빈 소수 판별

### description

---

페르마의 소정리:

$a$와 $p$가 서로소일때, $a^{p-1} \equiv 1 \mod p$

---

$p$가 홀수인 소수라면, $p=d \times 2^s$처럼 나타낼 수 있고,

$a^{d \times 2^s} -1 = (a^{d \times 2^{s-1}}+1)(a^{d\times 2^{s-2}}+1)\dots(a^d+1)(a^d-1) \equiv 0 \mod p$가 되므로

우측 수들 중 하나는 p으로 나눈 나머지가 0이다(=p로 나눠진다).

그래서 홀수 p와 서로소인 어떤 a에 대해 우측의 수들 중 하나 이상의 수가 p로 나눠진다면 p는 소수일 수도 있다는 것이다.(소수가 아닐 수도 있음)

그래서 여러 a에 대해 수행해서 모두 같은 결과가 나오면 소수라고 판별한다.

int 범위: 2,7,61

long long 범위: 37이하 소수

2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37
### code

```c++
ull mul(ull x,ull y,ull mod){
    x%=mod;y%=mod;
    return x*y%mod;
}
ull pw(ull x,ull y,ull mod){
    ull z=1;
    while(y){
        if(y&1){
            z=mul(z,x,mod);
        }
        x=mul(x,x,mod);
        y>>=1;
    }
    return z;
}
int aList[]={2, 7,61 };
int millerRabin(ull n,ull a){
    if(a%n==0)return 1;
    ull d=n-1;
    while(d%2==0)d/=2;
    ull tmp=pw(a,d,n);
    if(tmp==1||tmp==n-1) return 1;
    while(d<=n-1){
        d*=2;
        tmp=mul(tmp,tmp,n);
        if(tmp==n-1) return 1;
    }
    return 0;
}
/* 혹은
ll millerRabin(ll n,ll a) {
    mod = n;
    if (a % n == 0) return 1;
    ll t = n - 1;
    while (1) {
        ll num = pw(a, t);
        if (num == n - 1) {//a^t == -1 mod n
            return 1;
        }
        if (t & 1) {
            return (num == 1 || num == n - 1);
        }
        t /= 2;
    }
}
*/
int isPrime(ull n){
    for(auto a:aList){
        if(!millerRabin(n,a)){
            return 0;
        }
    }
    return 1;
}
```