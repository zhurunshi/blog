---
title: PAT-A 1005. Spell It Right (20)
categories: PAT-A
date: 2017-01-16 09:39:25
tags:
---
# 传送门
[https://www.patest.cn/contests/pat-a-practise/1005](https://www.patest.cn/contests/pat-a-practise/1005)
<!--more-->
# 题目
> Given a non-negative integer N, your task is to compute the sum of all the digits of N, and output every digit of the sum in English.
**Input Specification:**
Each input file contains one test case. Each case occupies one line which contains an N (<= 10^100).
**Output Specification:**
For each test case, output in one line the digits of the sum in English words. There must be one space between two consecutive words, but no extra space at the end of a line.
**Sample Input:**
12345
**Sample Output:**
one five

# 分析
将读入的内容作为字符串，根据其顺序将各位数字相加，然后将和的每位数字按序压栈，再根据每个数字输出对应的英文单词即可。

# 源代码

	//C/C++实现
	#include <iostream>
	#include <string>
	#include <vector>

	using namespace std;

	int main(){
		string s;
		cin >> s;
		int sum = 0;
		for(int i = 0; i < s.size(); ++i){
			sum += s[i] - '0';
		}
		vector<int> v;
		if(sum != 0){
			while(sum != 0){
				v.push_back(sum % 10);
				sum /= 10;
			}
		}
		else{
			v.push_back(0);
		}
		for(int i = v.size() - 1; i >= 0; --i){
			if(i != v.size() - 1){
				printf(" ");
			}
			switch(v[i]){
				case 0: printf("zero");break;
				case 1: printf("one");break;
				case 2: printf("two");break;
				case 3: printf("three");break;
				case 4: printf("four");break;
				case 5: printf("five");break;
				case 6: printf("six");break;
				case 7: printf("seven");break;
				case 8: printf("eight");break;
				case 9: printf("nine");break;
			}
		}
	}