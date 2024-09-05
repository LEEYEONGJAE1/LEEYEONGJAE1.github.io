---
layout: post
title: Fenwick Tree
implementation: true
published: true
use_math: true
--- 

### point update, range query
```c++
#include <bits/stdc++.h>
using namespace std;

// Method to calculate prefix sum till index idx
int sum(int idx, vector<int>& F)
{
    int runningSum = 0;
    // Summing up all the partial sums
    while (idx > 0) {
        runningSum += F[idx];
        int rightMostSetBit = (idx & (-idx));
        idx -= rightMostSetBit;
    }
    return runningSum;
}

// Method to update the array by adding X to index idx
void add(int idx, int X, vector<int>& F)
{
    while (idx < F.size()) {
        F[idx] += X;
        int rightMostSetBit = (idx & (-idx));
        idx += rightMostSetBit;
    }
}

// Method to calculate range sum from index l to r
int rangeQuery(int l, int r, vector<int>& F)
{
    return sum(r, F) - sum(l - 1, F);
}

int main()
{
    int n = 5;

    // 1 - based indexing
    vector<int> arr{ -1e9, 1, 2, 3, 4, 5 };
    // Initially all the values of Fenwick tree are 0
    vector<int> F(n + 1, 0);

    // Build the fenwick tree
    for (int i = 1; i <= n; i++) {
        add(i, arr[i], F);
    }

    // query the sum from index 1 to 3
    cout << rangeQuery(1, 3, F) << "\n";
    // query the sum from index 2 to 5
    cout << rangeQuery(2, 5, F) << "\n";

    // Update element at index i to X
    int i = 3;
    int X = 7;
    // We have passed X - arr[i] to the add method, because
    // add method simply adds a number at a particular index
    // so if we need to update the element, we need to pass
    // the difference between the ith element and X to add
    // method
    add(i, X - arr[i], F);

    // query the sum from index 1 to 3
    cout << rangeQuery(1, 3, F) << "\n";
    // query the sum from 2 to 5
    cout << rangeQuery(2, 5, F) << "\n";

    return 0;
}
```

###  query in 2d array
```c++
struct FenwickTree2D {
    vector<vector<int>> bit;
    int n, m;

    // init(...) { ... }

    int sum(int x, int y) {
        int ret = 0;
        for (int i = x; i >= 0; i = (i & (i + 1)) - 1)
            for (int j = y; j >= 0; j = (j & (j + 1)) - 1)
                ret += bit[i][j];
        return ret;
    }

    void add(int x, int y, int delta) {
        for (int i = x; i < n; i = i | (i + 1))
            for (int j = y; j < m; j = j | (j + 1))
                bit[i][j] += delta;
    }
};
```

### range update, point query

```c++
#include<bits/stdc++.h>
using namespace std;

vector<int> BITree;
void updateBIT(vector<int>& BITree, int n, int index, int val)
{
    index = index + 1;
    while (index <= n)
    {
        BITree[index] += val;
        index += index & (-index);
    }
}

int query(vector<int>& BITree, int index)
{
    int sum = 0;
    index = index + 1;

    while (index > 0)
    {
        sum += BITree[index];
        index -= index & (-index);
    }
    return sum;
}

void update(vector<int>& BITree, int l, int r, int n, int val)
{
    updateBIT(BITree, n, l, val);
    updateBIT(BITree, n, r + 1, -val);
}

int main() {
    int n = 10;
    vector<int> a = { 1,3,2,5,6,3,3,3,3,3 };

    vector<int> tree(n + 1);
    for (int i = 0; i < n; i++) {
        if (i == 0) updateBIT(tree, n, i, a[i]);
        else updateBIT(tree, n, i, a[i] - a[i - 1]);
    }

    for (int i = 0; i < n; i++) {
        cout << query(tree, i) << " ";
    }
    cout << "\n";
    // 1 3 2 5 6 3 3 3 3 3 

    update(tree, 4, 7, n, 3);
    for (int i = 0; i < n; i++) {
        cout << query(tree, i) << " ";
    }
    cout << "\n";
    // 1 3 2 5 9 6 6 6 3 3 
}
```

### range update, range query
```c++
#include <bits/stdc++.h>
using namespace std;

int getSum(int BITree[], int index){
    int sum = 0;
    index = index + 1;
    while (index > 0) {
        sum += BITree[index];
        index -= index & (-index);
    }
    return sum;
}

void updateBIT(int BITree[], int n, int index, int val){
    index = index + 1;
    while (index <= n) {
        BITree[index] += val;
        index += index & (-index);
    }
}

int sum(int x, int BITTree1[], int BITTree2[]){
    return (getSum(BITTree1, x) * x) - getSum(BITTree2, x);
}

void updateRange(int BITTree1[], int BITTree2[], int n, int val, int l, int r){
    updateBIT(BITTree1, n, l, val);
    updateBIT(BITTree1, n, r + 1, -val);
    updateBIT(BITTree2, n, l, val * (l - 1));
    updateBIT(BITTree2, n, r + 1, -val * r);
}

int rangeSum(int l, int r, int BITTree1[], int BITTree2[]){
    return sum(r, BITTree1, BITTree2) - sum(l - 1, BITTree1, BITTree2);
}

int* constructBITree(int n)
{
    int* BITree = new int[n + 1];
    for (int i = 1; i <= n; i++)
        BITree[i] = 0;

    return BITree;
}

int main()
{
    int n = 5;

    int *BITTree1, *BITTree2;

    BITTree1 = constructBITree(n);
    BITTree2 = constructBITree(n);

    int l = 0, r = 4, val = 5;
    updateRange(BITTree1, BITTree2, n, val, l, r);
    // [5,5,5,5,5]
   
    l = 2, r = 4, val = 10;
    updateRange(BITTree1, BITTree2, n, val, l, r);
    // [5,5,15,15,15]

    l = 1, r = 4;
    cout << "Sum of elements from [" << l << "," << r << "] is ";
    cout << rangeSum(l, r, BITTree1, BITTree2) << "\n";
    
    //Sum of elements from [1,4] is 50
    return 0;
}
```
---
reference: 
* [https://www.geeksforgeeks.org/fenwick-tree-for-competitive-programming/](https://www.geeksforgeeks.org/fenwick-tree-for-competitive-programming/)
* [https://cp-algorithms.com/data_structures/fenwick.html](https://cp-algorithms.com/data_structures/fenwick.html)
* [https://www.geeksforgeeks.org/binary-indexed-tree-range-update-range-queries/](https://www.geeksforgeeks.org/binary-indexed-tree-range-update-range-queries/)
* [https://www.geeksforgeeks.org/binary-indexed-tree-range-updates-point-queries/](https://www.geeksforgeeks.org/binary-indexed-tree-range-updates-point-queries/)