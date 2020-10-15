---
layout: post
title:  "Segment Tree for the Sum"
date:   2020-10-15 22:40:00 +0700
categories: CPP Competitive-Programming
---

Segment Tree for the Sum.

```cpp
#include <bits/stdc++.h>
using namespace std;
 
#define rep(i, a, b) for(int i = a; i < (b); ++i)
using ll = long long;
using vi = vector<int>;
 
struct SegmentTree {
 
    vector<ll> sums;
    int size;
 
    SegmentTree(int n) {
        size = 1;
        while(size < n) size <<= 1;
        sums.assign((size << 1), 0LL);
    }
 
    void set(int i, int v, int idx, int lx, int rx) {
        if(rx - lx == 1) {
            sums[idx] = v;
            return;
        }
        int mid = (lx + rx) >> 1;
        if(i < mid) {
            set(i, v, (idx << 1) + 1, lx, mid);
        } else {
            set(i, v, (idx << 1) + 2, mid, rx);
        }
        sums[idx] = sums[(idx << 1) + 1] + sums[(idx << 1) + 2];
    }
 
    ll query(int l, int r, int idx, int lx, int rx) {
        if(l >= rx || r <= lx) return 0;
        if(lx >= l && rx <= r) {
            return sums[idx];
        }
        int mid = (lx + rx) >> 1;
        ll s1 = query(l, r, (idx << 1) + 1, lx, mid);
        ll s2 = query(l, r, (idx << 1) + 2, mid, rx);
        return s1 + s2;
    }
 
};
 
int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(nullptr);
 
    int n, q;
    cin >> n >> q;
 
    SegmentTree st(n);
 
    auto Update = [&](int i, int v) -> void {
        st.set(i, v, 0, 0, st.size);
    };
    auto Query = [&](int l, int r) -> ll {
        return st.query(l, r, 0, 0, st.size);
    };
 
    vi a(n);
    rep(i, 0, n) {
        cin >> a[i];
        Update(i, a[i]);
    }
 
    while(q--) {
        int op;
        cin >> op;
        if(op == 1) {
            int i, v;
            cin >> i >> v;
            Update(i, v);
        } else if(op == 2) {
            int l, r;
            cin >> l >> r;
            cout << Query(l, r) << "\n";
        }
    }
 
    return 0;
}
```