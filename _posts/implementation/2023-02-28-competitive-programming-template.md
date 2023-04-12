---
layout: post
title: Competitive Programming Template
implementation: true
published: true
use_math: true
---
```c++
#include<bits/stdc++.h>
using namespace std;
#define all(x) (x).begin(), (x).end()

typedef long long ll;
typedef pair<ll, ll> pl;
typedef vector<ll> vl;
typedef vector<pl> vp;
ll gcd(ll m, ll n) { if (n == 0) return m; return gcd(n, m % n); }
ll lcm(ll m, ll n) { return m * n / gcd(m, n); }
ll dx[4] = { 1,0,-1,0 }, dy[4] = { 0,1,0,-1 };

ll mod = 998244353;
ll mul(ll x, ll y) { return (x * y) % mod; }
ll pw(ll x, ll y) { ll z = 1; while (y) { if (y & 1) { z = mul(z, x); }x = mul(x, x); y >>= 1; }return z; }

void solve() {

}
int main() {
ios_base::sync_with_stdio(0); cin.tie(0); cout.tie(0);
ll tc = 1;
cin >> tc;
while (tc--) solve();
exit(0);
}
```
~202303
```c++
#include<bits/stdc++.h>
using namespace std;
#define int long long
#define all(x) (x).begin(), (x).end()
typedef pair<int, int> pii;
typedef vector<int> vi;
typedef vector<pii> vp;

void init() {

}
void solve(){

}
int32_t main() {
    ios_base::sync_with_stdio(0); cin.tie(0); cout.tie(0);
    int tc = 1;
    cin >> tc;
    init();
    while (tc--) solve();
    exit(0);
}
```
202304~