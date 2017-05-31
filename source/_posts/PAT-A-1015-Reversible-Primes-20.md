---
title: PAT-A 1015. Reversible Primes (20)
categories: PAT-A
date: 2017-01-16 10:07:13
tags:
---
# 传送门
[https://www.patest.cn/contests/pat-a-practise/1015](https://www.patest.cn/contests/pat-a-practise/1015)
<!--more-->
# 题目
> *A reversible prime* in any number system is a prime whose "reverse" in that number system is also a prime. For example in the decimal system 73 is a reversible prime because its reverse 37 is also a prime.
Now given any two positive integers N (< 10^5) and D (1 < D <= 10), you are supposed to tell if N is a reversible prime with radix D.
**Input Specification:**
The input file consists of several test cases. Each case occupies a line which contains two integers N and D. The input is finished by a negative N.
**Output Specification:**
For each test case, print in one line "Yes" if N is a reversible prime with radix D, or "No" if not.
**Sample Input:**
73 10
23 2
23 10
-2
**Sample Output:**
Yes
Yes
No

# 分析
题意：
给出一个10进制数N和进制D，先化成给定进制D的数，然后翻转，再化成10进制数N'进行验证其是否是质数（素数），若翻转前的数N和翻转后的数N'均为质数，则输出Yes，否则，输出No。

我单独写了一个翻转的函数，先计算出10进制N的D进制数，然后再计算翻转后D进制数的10进制数N'，最后用开始建立好的质数表来判断其是否为质数，最后按要求输出即可。

# 源代码

	//C/C++实现
	#include <iostream>
	#include <vector>
	#include <cmath>

	using namespace std;

	bool isNotPrime[100000] = {true, true};

	int reverse(int n, int d){
		int tmp = n;
		vector<int> v;
		while(tmp){
			v.push_back(tmp % d);
			tmp /= d;
		}
		int count = 0, sum = 0, size = v.size();
		for(int i = 0; i < size; ++i){
			sum += v[i] * pow(d, size - i - 1);
		}
		return sum;
	}

	int main(){
		//create prime table
		for(int i = 2; i < 50000; ++i){
			for(int j = 2; i * j < 100000; ++j){
				isNotPrime[i * j] = true;
			}
		}
		int n, d;
		scanf("%d", &n);
		while(n > 0){
			scanf("%d", &d);
			if(!isNotPrime[n] && !isNotPrime[reverse(n, d)]){
				printf("Yes\n");
			}
			else{
				printf("No\n");
			}
			scanf("%d", &n);
		}
		return 0;
	}
