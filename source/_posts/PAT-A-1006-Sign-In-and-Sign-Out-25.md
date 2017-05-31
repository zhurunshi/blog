---
title: PAT-A 1006. Sign In and Sign Out (25)
categories: PAT-A
date: 2017-01-16 09:41:32
tags:
---
# 传送门
[https://www.patest.cn/contests/pat-a-practise/1006](https://www.patest.cn/contests/pat-a-practise/1006)
<!--more-->
# 题目
> At the beginning of every day, the first person who signs in the computer room will unlock the door, and the last one who signs out will lock the door. Given the records of signing in's and out's, you are supposed to find the ones who have unlocked and locked the door on that day.
**Input Specification:**
Each input file contains one test case. Each case contains the records for one day. The case starts with a positive integer M, which is the total number of records, followed by M lines, each in the format:
ID_number Sign_in_time Sign_out_time
where times are given in the format HH:MM:SS, and ID number is a string with no more than 15 characters.
**Output Specification:**
For each test case, output in one line the ID numbers of the persons who have unlocked and locked the door on that day. The two ID numbers must be separated by one space.
Note: It is guaranteed that the records are consistent. That is, the sign in time must be earlier than the sign out time for each person, and there are no two persons sign in or out at the same moment.
**Sample Input:**
3
CS301111 15:30:28 17:00:10
SC3021234 08:00:00 11:25:25
CS301133 21:45:00 21:58:40
**Sample Output:**
SC3021234 CS301133

# 分析
先读入数据，每读入一行数据，就判断其是否大于当前最大时间，或者小于当前最小时间。若大于或小于记录的时间，则更新最大或最小时间，并且更新id，最后输出最小时间的id以及最大时间的id即可。

# 源代码

	//C/C++实现
	#include <iostream>
	#include <string>
	#include <vector>

	using namespace std;

	int main(){
		int n;
		scanf("%d", &n);
		string id;
		string tmp;
		int min_h = 23, min_m = 59, min_s = 59;
		int max_h = 0, max_m = 0, max_s = 0;
		int tmp_h, tmp_m, tmp_s;
		string min_id, max_id;
		for(int i = 0; i < n; ++i){
			cin >> id;
			cin >> tmp;
			tmp_h = (tmp[0] - '0') * 10 + (tmp[1] - '0');
			tmp_m = (tmp[3] - '0') * 10 + (tmp[4] - '0');
			tmp_s = (tmp[6] - '0') * 10 + (tmp[7] - '0');
			if(tmp_h < min_h){
				min_id = id;
				min_h = tmp_h;
				min_m = tmp_m;
				min_s = tmp_s;
			}
			else if(tmp_h == min_h){
				if(tmp_m < min_m){
					min_id = id;
					min_h = tmp_h;
					min_m = tmp_m;
					min_s = tmp_s;
				}
				else if(tmp_m == min_m){
					if(tmp_s < min_s){
						min_id = id;
						min_h = tmp_h;
						min_m = tmp_m;
						min_s = tmp_s;
					}
				}
			}
			cin >> tmp;
			tmp_h = (tmp[0] - '0') * 10 + (tmp[1] - '0');
			tmp_m = (tmp[3] - '0') * 10 + (tmp[4] - '0');
			tmp_s = (tmp[6] - '0') * 10 + (tmp[7] - '0');
			if(tmp_h > max_h){
				max_id = id;
				max_h = tmp_h;
				max_m = tmp_m;
				max_s = tmp_s;
			}
			else if(tmp_h == max_h){
				if(tmp_m > max_m){
					max_id = id;
					max_h = tmp_h;
					max_m = tmp_m;
					max_s = tmp_s;
				}
				else if(tmp_m == max_m){
					if(tmp_s > max_s){
						max_id = id;
						max_h = tmp_h;
						max_m = tmp_m;
						max_s = tmp_s;
					}
				}
			}
		}
		cout << min_id << " " << max_id;
	}