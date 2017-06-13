---
title: 秦九韶算法
date: 2017-06-13 11:09:22
categories: 算法
---
# 普通算法
f1(x) = a0 + a1x + a2x^2 + ... + an-1x^(n-1) + anx^n

	double f1(int n, double a[], double x){
		int i;
		double p = a[0];
		for (int i = 1; i <= n; ++i){
			p += (a[i] * pow(x, i));
		}
		return p;
	}
<!--more-->
# 秦九韶算法
每次把x当做公因子提取出来，然后从最里面向外计算。
f2(x) = a0 + x(a1 + x(...x(an-1 + x(an))...))

	double f2(int n, double a[], double x){
		int i;
		double p = a[n];
		for (i = n; i > 0; --i){
			p = a[i - 1] + x * p;
		}
		return p;
	}

# 速度测试

	#include <iostream>
	#include <vector>
	#include <time.h>

	#define MAXN 10 /* 多项式最大项数，即多项式阶数+1 */
	#define MAXK 1e6 /* 被测函数最大重复调用次数 */

	using namespace std;

	clock_t start, stop;
	/* clock_t是clock()函数返回的变量类型 */
	double duration;
	/* 记录函数运行时间，以秒为单位 */


	double f1(int n, double a[], double x){
		int i;
		double p = a[0];
		for (int i = 1; i <= n; ++i){
			p += (a[i] * pow(x, i));
		}
		return p;
	}

	double f2(int n, double a[], double x){
		int i;
		double p = a[n];
		for (i = n; i > 0; --i){
			p = a[i - 1] + x * p;
		}
		return p;
	}

	int main(){
		int i;
		double a[MAXN]; /* 存储多项式的系数 */
		for (i = 0; i < MAXN; ++i){
			a[i] = (double)i;
		}

		/* 不在测试范围的准备工作写在clock()调用之前 */
		start = clock(); /* 开始计时 */
		for (int j = 0; j < MAXK; ++j){
			f1(MAXN - 1, a, 1.1);
		}
		stop = clock(); /* 停止计时 */
		duration = ((double)(stop - start)) / CLK_TCK / MAXK;
		printf("f1-duration: %6.2e\n", duration);

		start = clock(); /* 开始计时 */
		for (int j = 0; j < MAXK; ++j){
			f2(MAXN - 1, a, 1.1);
		}
		stop = clock(); /* 停止计时 */
		duration = ((double)(stop - start)) / CLK_TCK / MAXK;
		printf("f2-duration: %6.2e\n", duration);
		return 0;
	}

![运行结果](http://upload-images.jianshu.io/upload_images/2319568-0ac5ff17ae7c81d0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
# 分析
**可以看出来单次运行的时间上，秦九韶算法比普通算法快了一个数量级。**