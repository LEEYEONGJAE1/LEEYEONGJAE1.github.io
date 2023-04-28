---
layout: post
title: Chinese Remainder Theorem
use_math: true
math : true
published: true
---
# 중국인의 나머지 정리

요약: 연립 합동식의 해가 **유일**하게 **존재**한다

## description

$m_1,m_2,\dots,m_n$이 쌍마다 모두 서로소($gcd(m_i,m_j)=1, i \neq j$)이면, 

다음 연립 합동식

$x \equiv a_1 ( \mod m_1)$

$x \equiv a_2 ( \mod m_2)$

$\vdots$

$x \equiv a_n ( \mod m_n)$

은($\mod m_1 m_2 \dots m_n$)에 대해 **유일**한 해를 갖는다.

## code

```c++
struct Congruence {
    long long a, m;
};

long long chinese_remainder_theorem(vector<Congruence> const& congruences) {
    long long M = 1;
    for (auto const& congruence : congruences) {
        M *= congruence.m;
    }

    long long solution = 0;
    for (auto const& congruence : congruences) {
        long long a_i = congruence.a;
        long long M_i = M / congruence.m;
        long long N_i = mod_inv(M_i, congruence.m);
        solution = (solution + a_i * M_i % M * N_i) % M;
    }
    return solution;
}
```
reference: [https://cp-algorithms.com/algebra/chinese-remainder-theorem.html#direct-construction](https://cp-algorithms.com/algebra/chinese-remainder-theorem.html#direct-construction)


