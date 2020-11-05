---
layout: post
title:  "Miller-Rabin"
date:   2020-11-05 13:10:00 +0700
categories: CPP Competitive-Programming
---

Miller-Rabin (@chemthan).

```cpp
namespace Rabin {
    template<typename num_t>
    num_t mulmod(num_t a, num_t b, num_t p) {
        a %= p; b %= p;
        num_t q = (num_t) ((long double) a * b / p);
        num_t r = a * b - q * p;
        while (r < 0) r += p;
        while (r >= p) r -= p;
        return r;
        /*
        num_t r = 0;
        int block = 1;
        num_t base = 1LL << block;
        for (; b; b >>= block) {
            r = (r + a * (b & (base - 1))) % p;
            a = a * base % p;
        }
        return r;
        */
    }
    template<typename num_t>
    num_t powmod(num_t n, num_t k, num_t p) {
        num_t r = 1;
        for (; k; k >>= 1) {
            if (k & 1) r = mulmod(r, n, p);
            n = mulmod(n, n, p);
        }
        return r;
    }
    template<typename num_t>
    int test(num_t n) {
        if (n == 2) return 1;
        if (n < 2 || !(n & 1)) return 0;
        const num_t p[9] = {2, 3, 5, 7, 11, 13, 17, 19, 23};
        num_t a, d = n - 1, mx = 4;
        int i, r, s = 0;
        while (!(d & 1)) {++s; d >>= 1;}
        for (i = 0; i < mx; i++) {
            if (n == p[i]) return 1;
            if (!(n % p[i])) return 0;
            a = powmod(p[i], d, n);
            if (a != 1) {
                for (r = 0; r < s && a != n - 1; r++) a = mulmod(a, a, n);
                if (r == s) return 0;
            }
        }
        return 1;
    }
}
```