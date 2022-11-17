---
layout: post
title: extended euclid algorithm
use_math: true
math : true
published: true
---
# 확장 유클리드 알고리즘(미완)

### description

ㅇㅇㅇ

### code
```c++
pl egcd(ll a,ll b){
    if(b==0) return {1,0};
    else{
      pl t=egcd(b,a%b);
      return egcd(t.second,t.first-(a/b)*t.second);
    }
}
```
