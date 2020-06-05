---
layout: post
title:  "C++ Bitwise-tricks"
date:   2020-06-05 09:38:00 +0700
categories: Bitwise-Tricks CPP Competitive-Programming
---

Các tricks của C++ dựa trên bitwise trong Lập trình thi đấu (C++ 11).

**1. Kiểm tra số chẳn hay số lẻ:**\n
*Cách kiểm tra này chỉ thực sự hữu hiệu khi số cần kiếm tra là rất lớn.*
```cpp
if(num & 1) {
    printf("ODD");
} else {
    printf("EVEN");
}
```
**Ví dụ :**\n
Input: num = 5\n
Output: ODD\n
**Giải thích :**\n
Số 5 được viết dưới dạng nhị phân là 101. Vì vậy khi ta thực hiện phép toán 101 & 1 thì ta sẽ nhận được một số khác 0.\n
Thật vậy:\n
&nbsp;&nbsp;&nbsp;&nbsp;0101\n
&nbsp;&nbsp;&\n
&nbsp;&nbsp;&nbsp;&nbsp;0001\n
&nbsp;&nbsp;&nbsp;&nbsp;====\n
&nbsp;&nbsp;&nbsp;&nbsp;0001

**2. Nhân và chia nhanh cho 2:**
```cpp
    num = num << 1; //~ Nhân num với 2  
    num = num >> 1; //~ Chia num với 2
```
**3. Swap(a, b):**
```cpp
    a^=b, b^=a, a^=b;
```
**4. Kiểm tra x có thể viết thành 2 mũ được không ?**
```cpp
bool isPowerOfTwo(int x) { 
    return x && (!(x&(x-1))); 
} 
```




