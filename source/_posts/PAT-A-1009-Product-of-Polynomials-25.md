---
title: PAT-A 1009. Product of Polynomials (25)
categories: PAT-A
date: 2017-01-16 09:48:48
tags:
---
# 传送门
[https://www.patest.cn/contests/pat-a-practise/1009](https://www.patest.cn/contests/pat-a-practise/1009)
<!--more-->
# 题目
> This time, you are supposed to find A\*B where A and B are two polynomials.
**Input Specification:**
Each input file contains one test case. Each case occupies 2 lines, and each line contains the information of a polynomial: K N1 aN1 N2 aN2 ... NK aNK, where K is the number of nonzero terms in the polynomial, Ni and aNi (i=1, 2, ..., K) are the exponents and coefficients, respectively. It is given that 1 <= K <= 10, 0 <= NK < ... < N2 < N1 <=1000.
**Output Specification:**
For each test case you should output the product of A and B in one line, with the same format as the input. Notice that there must be NO extra space at the end of each line. Please be accurate up to 1 decimal place.
**Sample Input**
2 1 2.4 0 3.2
2 2 1.5 1 0.5
**Sample Output**
3 3 3.6 2 6.0 1 1.6

# 分析
1.因为只有两个变量，所以没用结构体数组，用的pair代替，以first为指数，second为系数。
2.遍历两个多项式，每次获得临时的指数和系数，根据指数，将系数加到对应下标的数组里，每次记录一下最大指数，便于后面统计多项式的项数。
3.最后格式化输出结果即可。

# 源代码

	//C/C++实现
	#include <iostream>
	#include <vector>

	using namespace std;

	double res[2001]; //result polynomial

	int main(){
		int n;
		scanf("%d", &n);
		vector<pair<int, double>> v1(n); //the first polynomial
		for(int i = 0; i < n; ++i){
			scanf("%d %lf", &v1[i].first, &v1[i].second);
		}
		//input the second polynomial
		scanf("%d", &n);
		vector<pair<int, double>> v2(n); //the second polynomial
		for(int i = 0; i < n; ++i){
			scanf("%d %lf", &v2[i].first, &v2[i].second);
		}
		//compute
		int tmp_exp;
		double tmp_coef;
		int max_exp = 0;
		for(int i = 0; i < v1.size(); ++i){
			for(int j = 0; j < v2.size(); ++j){
				tmp_exp = v1[i].first + v2[j].first;
				tmp_coef = v1[i].second * v2[j].second;
				max_exp = (tmp_exp > max_exp) ? tmp_exp : max_exp;
				res[tmp_exp] += tmp_coef;
			}
		}
		//output
		int count = 0;
		for(int i = max_exp; i >= 0; --i){
			if(res[i] != (double)0){
				++count;
			}
		}
		printf("%d", count);
		for(int i = max_exp; i >= 0; --i){
			if(res[i] != (double)0){
				printf(" %d %.1f", i, res[i]);
			}
		}
	}