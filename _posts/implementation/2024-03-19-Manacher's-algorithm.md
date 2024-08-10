---
layout: post
title: Manacher's Algorithm
implementation: true
published: true
use_math: true
---
# Manacher's Algorithm

```cpp
vector<int> manacher_odd(string s) {
    int n = s.size();
    s = "$" + s + "^";
    vector<int> p(n + 2);
    int l = 1, r = 1;
    for (int i = 1; i <= n; i++) {
        p[i] = max({ 0LL, min({r - i, p[l + (r - i)]}) });
        while (s[i - p[i]] == s[i + p[i]]) {
            p[i]++;
        }
        if (i + p[i] > r) {
            l = i - p[i], r = i + p[i];
        }
    }
    return vector<int>(begin(p) + 1, end(p) - 1);
}
vector<int> manacher(string s) {
    string t;
    for (auto c : s) {
        t.push_back('#');
        t.push_back(c);
    }
    auto res = manacher_odd(t + "#");
    return vector<int>(begin(res) + 1, end(res) - 1);
}
vector<int> rad;
int isPalindrome(int l, int r) {
    l *= 2, r *= 2;
    int len = (r - l + 1);
    return (rad[(r + l) / 2] >= (len + 1) / 2);
}
```

---

reference: 
* [Manacher's Algorithm - Finding all sub-palindromes in $O(N)$ ](https://cp-algorithms.com/string/manacher.html)