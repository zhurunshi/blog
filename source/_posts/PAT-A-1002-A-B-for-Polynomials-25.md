---
title: PAT-A 1002. A+B for Polynomials (25)
categories: PAT-A
date: 2016-11-17 09:58:11
tags:
---
# 传送门
[https://www.patest.cn/contests/pat-a-practise/1002](https://www.patest.cn/contests/pat-a-practise/1002)
<!--more-->
# 题目
> This time, you are supposed to find A+B where A and B are two polynomials.
**Input**
Each input file contains one test case. Each case occupies 2 lines, and each line contains the information of a polynomial: K N1 aN1 N2 aN2 ... NK aNK, where K is the number of nonzero terms in the polynomial, Ni and aNi (i=1, 2, ..., K) are the exponents and coefficients, respectively. It is given that 1 <= K <= 10，0 <= NK < ... < N2 < N1 <=1000.
**Output**
For each test case you should output the sum of A and B in one line, with the same format as the input. Notice that there must be NO extra space at the end of each line. Please be accurate to 1 decimal place.
**Sample Input**
2 1 2.4 0 3.2
2 2 1.5 1 0.5
**Sample Output**
3 2 1.5 1 2.9 0 3.2

# 分析
开始想的特别多，结果发现400ms的时间循环1001个数还是很简单的，直接遍历就行。

需要注意的是：
1.输入0 0要输出一个0；
2.第一次输入没有重复的指数，直接按下标赋值到数组里面即可。

# 源代码

	//C/C++实现
	#include <iostream>

	using namespace std;

	float num[1001];

	int main(){
		int n1, n2; //项数
		float coef; //系数
		int exp; //指数
		int max_exp = -1; //最大指数
		scanf("%d", &n1);
		for(int i = 0; i < n1; ++i){
			scanf("%d %f", &exp, &coef);
			max_exp = (exp > max_exp ? exp : max_exp);
			num[exp] = coef;
		}
		scanf("%d", &n2);
		for(int i = 0; i < n2; ++i){
			scanf("%d %f", &exp, &coef);
			max_exp = (exp > max_exp ? exp : max_exp);
			num[exp] += coef;
		}
		int count = 0; //项数计算
		for(int i = 0; i <= 1000; ++i){
			if(num[i]){
				++count;
			}
		}
		printf("%d", count);
		for(int i = max_exp; i >= 0; --i){
			if(num[i] != 0){
				printf(" %d %.1f", i, num[i]);
			}
		}
		printf("\n");
		return 0;
	}