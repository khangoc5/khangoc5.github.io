---
layout: post
title:  "Sieve of Eratosthenes"
date:   2020-11-04 20:50:00 +0700
categories: CPP Competitive-Programming
---

Sieve of Eratosthenes - Sàn nguyên tố (@chemthan).

```cpp
namespace Sieve {
    vector<bool> ispr;
    vector<int> prs;
    void work(int n) {
        int k = sqrt(n) + 2;
        while (k * k > n) k--;
        vector<bool> f(k + 1, 1);
        f[0] = f[1] = 0;
        ispr.resize(n + 1);
        ispr.shrink_to_fit();
        prs.clear();
        for (int i = 2; i <= k; i++) if (f[i]) {
            for (int j = i * i; j <= k; j += i) {
                f[j] = 0;
            }
            ispr[i] = 1;
            prs.push_back(i);
        }
        vector<int> g(k + 1);
        int c = (int) prs.size();
        for (int i = k + 1; i <= n; i += k) {
            int j = min(i + k - 1, n);
            for (int u = 0; u < c; u++) {
                int p = prs[u];
                for (int q = (i + p - 1) / p * p; q <= j; q += p) {
                    g[q - i] = i;
                }
            }
            for (int u = i; u <= j; u++) if (g[u - i] < i) {
                ispr[u] = 1;
                prs.push_back(u);
            }
        }
    }
}
```