---
layout: post
implementation: true
published: true
use_math: true
---
main에 fac_init(); 넣어야 함
```c++
#include<bits/stdc++.h>
using namespace std;
typedef long long ll;
typedef vector<ll> vl;
typedef vector<pair<ll,ll> > vp;
#define MXNUM 10000000
ll Min(ll a,ll b){
	return (a<b)?a:b;
}
ll mindiv[MXNUM + 13],val[MXNUM+13]; //mindiv[i]= mininum prime divisor of i, val[i] = the number of prime divisors of i
void fac_init() {
    for (int i = 2; i <= MXNUM; i++) mindiv[i] = i;
    for (int i = 2; i * i <= MXNUM; i++) {
        if (mindiv[i] != i) continue;
        for (int j = i; j <= MXNUM; j += i) {
            mindiv[j] = Min(mindiv[j], i);
        }
    }
    for (int i = 2; i <= MXNUM; i++) {
        int j = i / mindiv[i];
        val[i] = val[j] + (mindiv[i] != mindiv[j]);
    }
}
vl fac(ll num) {//just giving primes
    vl ret;
    ll curVal = num;
    while (curVal != 1) {
        if (ret.empty() || ret.back() != mindiv[curVal]) {
            ret.push_back(mindiv[curVal]);
        }
        curVal /= mindiv[curVal];
    }
    return ret;
}
vp fac_i(ll num){
    vp ret;
    ll curVal = num;
    while(curVal!=1){
        if (ret.empty() || ret.back().first != mindiv[curVal]) {
            ret.push_back({ mindiv[curVal],1 });
        }
        else if(ret.back().first==mindiv[curVal]){
            ret.back().second++;
        }
        curVal /= mindiv[curVal];
    }
    return ret;
}
int main(){
	fac_init();
	for(auto t:fac_i(810)){
		cout<<t.first<<" "<<t.second<<"\n";
	}
	return 0;
}
```