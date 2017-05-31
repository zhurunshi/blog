---
title: PAT-A 1008. Elevator (20)
categories: PAT-A
date: 2017-01-16 09:45:43
tags:
---
# 传送门
[https://www.patest.cn/contests/pat-a-practise/1008](https://www.patest.cn/contests/pat-a-practise/1008)
<!--more-->
# 题目
> The highest building in our city has only one elevator. A request list is made up with N positive numbers. The numbers denote at which floors the elevator will stop, in specified order. It costs 6 seconds to move the elevator up one floor, and 4 seconds to move down one floor. The elevator will stay for 5 seconds at each stop.
For a given request list, you are to compute the total time spent to fulfill the requests on the list. The elevator is on the 0th floor at the beginning and does not have to return to the ground floor when the requests are fulfilled.
**Input Specification:**
Each input file contains one test case. Each case contains a positive integer N, followed by N positive numbers. All the numbers in the input are less than 100.
**Output Specification:**
For each test case, print the total time on a single line.
**Sample Input:**
3 2 3 1
**Sample Output:**
41

# 分析
题目不难，想清楚就好，代码里面写的还挺清楚的，这里就不多说了。（逃…

# 源代码

	//C/C++实现
	#include <iostream>

	using namespace std;

	int main(){
		int n;
		scanf("%d", &n);
		int floor = 0; //当前楼层，初始为0层
		int tmp; //目的楼层
		int diff; //楼层差
		int second = 0;
		for(int i = 0; i < n; ++i){
			scanf("%d", &tmp);
			diff = tmp - floor;
			floor = tmp;
			if(diff >= 0){ //上楼
				second += (diff * 6 + 5);
			}
			else{ //下楼
				second += (diff * (-4) + 5);
			}
		}
		printf("%d", second);
	}