---
layout: post
title:  "Segment Tree: Sum, Min, Max"
date:   2020-07-19 15:10:00 +0700
categories: CPP DSA Tree Competitive-Programming
---
Segment Tree

``cpp
#include <bits/stdc++.h>
using namespace std;

typedef long long ll;
typedef vector<int> vi;
typedef vector<ll> vl;
typedef pair<int, int> ii;
typedef vector<ii> vp;

// @author: khangtq1
struct SegmentTree {
    // #define m first
    // #define c second
    vl sums;
    int size;

    /*
    ii single(int x) {
        return {x, 1};
    }

    ii merge(ii a, ii b) {

    }
    */

    void init(int n) {
        size = 1;
        while(size < n) size *= 2;
        sums.assign(2 * size, 0LL);
    }

    void build(vi &a, int x, int lx, int rx) {

    }

    void build(vi &a) {

    }

    void set(int i, int v, int x, int lx, int rx) {

    }

    void set(int i, int v) {

    }

    void sum(int l, int r, int x, int lx, int rx) {

    }

    void sum(int l, int r) {

    }
};

int main() {
    ios::sync_with_stdio(false);
    SegmentTree st;
    int n;
    cin >> n;
    st.init(n);
    vi a(n);
    for(int i = 0; i < n; ++i)
        cin >> a[i];
    st.build(a);
    return 0;
}
```
