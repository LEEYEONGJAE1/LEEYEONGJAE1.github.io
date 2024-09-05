---
layout: post
title: Check whether a graph is bipartite
implementation: true
published: true
use_math: true
---

```c++
#include<bits/stdc++.h>
using namespace std;
typedef vector<int> vi;
typedef vector<vi> vvi;
int main(){
	int n,m;
	cin>>n>>m;
	vvi edge;
	edge.assign(n+1,vi());
	for(int i=0;i<m;i++){
		int u,v;
		cin>>u>>v;
		edge[u].push_back(v);
		edge[v].push_back(u);
	}
	vi side(n + 1, -1);
	int is_bipartite = 1;
	queue<int> q;
	for (int st = 1; st <= n; ++st)
	{
		if (side[st] == -1)
		{
			q.push(st);
			side[st] = 0;
			while (!q.empty())
			{
				int v = q.front();
				q.pop();
				for (int u : edge[v])
				{
					if (side[u] == -1)
					{
						side[u] = side[v] ^ 1;
						q.push(u);
					}
					else
						is_bipartite &= side[u] != side[v];
				}
			}
		}
	}
    cout<< is_bipartite<<"\n";
}   
/*
input:
4 4
1 2
2 3
3 4
4 1
output:
1

input:
3 3
1 2
2 3
3 1
output:
0
*/
```

---

reference:

- [https://cp-algorithms.com/graph/bipartite-check.html](https://cp-algorithms.com/graph/bipartite-check.html)

