---
title: PAT-A 1001. A+B Format (20)
categories: PAT-A
date: 2016-11-12 23:27:03
tags:
---
# 传送门
[https://www.patest.cn/contests/pat-a-practise/1001](https://www.patest.cn/contests/pat-a-practise/1001)
<!--more-->
# 题目
> Calculate a + b and output the sum in standard format -- that is, the digits must be separated into groups of three by commas (unless there are less than four digits).
**Input**
Each input file contains one test case. Each case contains a pair of integers a and b where -1000000 <= a, b <= 1000000. The numbers are separated by a space.
**Output**
For each test case, you should output the sum of a and b in one line. The sum must be written in the standard format.
**Sample Input**
-1000000 9
**Sample Output**
-999,991

# 分析
我可能用的方法比较麻烦，但是简单粗暴，比较好想，就是先将结果转化成字符串，然后从末尾压栈，压满三个数就压进一个逗号，需要注意的是，**如果首位数字是第三位，则不压入逗号**。

# 源代码

	//C/C++实现
	#include <iostream>
	#include <sstream>
	#include <stack>

	using namespace std;

	int main(){
		int a, b, sum;
		scanf("%d %d", &a, &b);
		sum = a + b;
		stringstream ss;
		string result;
		ss << sum;
		ss >> result;
		stack<char> s;
		if(sum < 0){ // minus
			int count = 0;
			for(int i = result.size() - 1; i >= 1; --i){
				++count;
				s.push(result[i]);
				if(count == 3){
					count = 0;
					if(i != 1){
						s.push(',');
					}
				}
			}
			s.push('-');
		}
		else{
			int count = 0;
			for(int i = result.size() - 1; i >= 0; --i){
				++count;
				s.push(result[i]);
				if(count == 3){
					count = 0;
					if(i != 0){
						s.push(',');
					}
				}
			}
		}
		while(!s.empty()){
			printf("%c", s.top());
			s.pop();
		}
		printf("\n");
		return 0;
	}