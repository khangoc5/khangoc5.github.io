---
layout: post
title:  "C Template"
date:   2020-07-06 20:40:36 +0700
categories: C CT101-LTCB
---
Đây là code mẫu của mình khi nộp bài lên **ELSE**[else.ctu.edu.vn] hiện nay.

```cpp
/**
 *    author:  _Khang_
 *    created: 07.06.2020 20:17:57       
**/
#include <stdio.h>
#include <stdlib.h>

#define rep(x, n) for(int x = 0; x < n; x++)
#define per(x, n) for(int x = n - 1; x >= 0; x--)
typedef long long ll;

typedef int DataType;
DataType read() {
	DataType dt;
	scanf("%d", &dt);
	return dt;
}
int isPrime(int x) {	
	for(int m = 2; m * m <= x; m++) 
		if(x % m == 0)
			return 0;
	return (x > 1);	
}
DataType max(DataType a, DataType b) {
	if(a > b)
		return a;
	return b;
}
DataType min(DataType a, DataType b) {
	if(a < b)
		return a;
	return b;
}
DataType __abs(DataType a) {
	return (a < 0) ? -a : a;
}
DataType __gcd(DataType a, DataType b) {
	return b ? __gcd(b, a % b) : a;
}
DataType __lcm(DataType a, DataType b) {
	return a / __gcd(a, b) * b;
}
DataType __pow(DataType a, int b) {
	if(b == 0) 
		return 1;	
	DataType ans = __pow(a, b/2);
	if(b & 1)
		return ans * ans * a;
	return ans * ans;
}

int main() {
	int n = read();
	int a[n];
	rep(i, n) {
		a[i] = read();
	}
	rep(i, n) {
		printf("%d ", a[i]);
	}
	return 0;
}
```
