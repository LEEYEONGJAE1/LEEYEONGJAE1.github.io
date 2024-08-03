---
layout: post
title: Ordered Set
implementation: true
published: true
use_math: true
---

### ordered set

stl의 set에는 없는 $log(n)$의 시간복잡도로 집합의 $k$번째 원소를 구해주는 기능이 있는 자료구조

```c++
#include <bits/stdc++.h>
using namespace std;

#include <ext/pb_ds/assoc_container.hpp>
#include <ext/pb_ds/tree_policy.hpp>
using namespace __gnu_pbds;
#define ordered_set tree<int, null_type, less<int>, rb_tree_tag,tree_order_statistics_node_update>

int main(){
    ordered_set X;
    X.insert(1);
    X.insert(2);
    X.insert(4);
    X.insert(8);
    X.insert(16);

    cout<<*X.find_by_order(1)<<endl; // 2
    cout<<*X.find_by_order(2)<<endl; // 4
    cout<<*X.find_by_order(4)<<endl; // 16
    cout<<(end(X)==X.find_by_order(6))<<endl; // true

    cout<<X.order_of_key(-5)<<endl;  // 0
    cout<<X.order_of_key(1)<<endl;   // 0
    cout<<X.order_of_key(3)<<endl;   // 2
    cout<<X.order_of_key(4)<<endl;   // 2
    cout<<X.order_of_key(400)<<endl; // 5
    return 0;
}
```

*아래 코드랑 같이쓰면 컴파일 에러남*

```c++
#define int long long
```

---

reference:

- [https://codeforces.com/blog/entry/11080](https://codeforces.com/blog/entry/11080)