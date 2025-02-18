---
title: "冷门的STL相关知识"
date: 2025-02-10T21:08:22+08:00
draft: false
tags: ["MISC"]
---

## 接口

求某几个数字中的最大元素我们可能会使用``max()``进行求解，而对于STL中有特殊的
```C++
vector<int> vi = {4, 5, 3, 1, 6, 2};
int top = *max_element(vi.begin(), vi.end());
int bottom = *min_element(vi.begin(), vi.end());
```
STL中的元素还可以进行在某个初始值基础上的累加操作：
```C++
int sum_vi = accumulate(vi.begin(), vi.end(), 0);
```

关于查找：
```C++
int val = find(vec.begin(), vec,end(), target);
```

## bitset
bitset 可以使用初始值初始化也可以使用字符串进行初始化：
```C++
std::bitset<8> bs("01010001");
std::bitset<8> bs(22);
```
bitset自带置1，置0，反转操作
```C++
bs[2] = 1;
bs.set(4);
bs.reset(2);
bs.flip(3);
bs.flip();
```
``count()``：返回 1 的个数  
``size()``：返回位数  
``test(pos)``：检查某一位是否为1  
``all()``：检查是否所有位都为1  
``any()``：检查是否有任何一位为1  
``none()``：检查是否所有位都为0  

也可以使用``to_ulong()`` ``to_ullong()`` ``to_string()``进行类型转换  

bitset可以直接进行位操作  

## Lambda

```C++
auto init = []() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);
    cout.tie(nullptr);
    return 'c';
}();
```
做力扣的时候突然发现的一段未知的玩意儿，一查发现其实是一个lambda函数定义，第一行中的``[]()``表示不捕获，不传参，函数体中，第一行关闭stdio与iostream的同步操作，后两行解除cin与cout的缓冲区绑定，最后的一个``()``表示立即执行  