---
title: PAT-A 1012. The Best Rank (25)
categories: PAT-A
date: 2017-01-16 10:00:14
tags:
---
# 传送门
[https://www.patest.cn/contests/pat-a-practise/1012](https://www.patest.cn/contests/pat-a-practise/1012)
<!--more-->
# 题目
> To evaluate the performance of our first year CS majored students, we consider their grades of three courses only: C - C Programming Language, M - Mathematics (Calculus or Linear Algebra), and E - English. At the mean time, we encourage students by emphasizing on their best ranks -- that is, among the four ranks with respect to the three courses and the average grade, we print the best rank for each student.
For example, The grades of C, M, E and A - Average of 4 students are given as the following:

> StudentID|C|M|E|A
-|-|-|-|-
310101|98|85|88|90
310102|70|95|88|84
310103|82|87|94|88
310104|91|91|91|91
Then the best ranks for all the students are No.1 since the 1st one has done the best in C Programming Language, while the 2nd one in Mathematics, the 3rd one in English, and the last one in average.
**Input**
Each input file contains one test case. Each case starts with a line containing 2 numbers N and M (<=2000), which are the total number of students, and the number of students who would check their ranks, respectively. Then N lines follow, each contains a student ID which is a string of 6 digits, followed by the three integer grades (in the range of [0, 100]) of that student in the order of C, M and E. Then there are M lines, each containing a student ID.
**Output**
For each of the M students, print in one line the best rank for him/her, and the symbol of the corresponding rank, separated by a space.
The priorities of the ranking methods are ordered as A > C > M > E. Hence if there are two or more ways for a student to obtain the same best rank, output the one with the highest priority.
If a student is not on the grading list, simply output "N/A".
**Sample Input**
5 6
310101 98 85 88
310102 70 95 88
310103 82 87 94
310104 91 91 91
310105 85 90 90
310101
310102
310103
310104
310105
999999
**Sample Output**
1 C
1 M
1 E
1 A
3 A
N/A

# 分析
先理解本题题意：
本题要求的是学生的最佳排名，怎么叫最佳排名呢？例如：C排第3，M排第1，那么输出的就是1 M，如果有并列情况，按照A > C > M > E的优先级处理。

因为studentId和排名，以及studentId和课程，满足key-value关系，所以这里选用map来解题。若使用数组的话，太耗费空间。

开始先定义结构体数组，存储studentId和各类课程成绩以及总分（平均分也可以），然后读入数据。
接着，按照A > C > M > E的顺序为结构体数组排序，要单独写4个排序函数，每次排序后遍历数组，若排名比之前科目的排名靠前，则将数组的下标作为排名放到map里面，更新排名。（这里会出现问题，后面会详细说）
最后，按照输入的studentId，从map里面取出最佳排名和对应课程名输出即可，若未找到改学生，则输出N/A。

遇到的问题：
要考虑到学生成绩相同的情况，也就是并列排名时，学生的排名应为：
1 2 3 3 5，而不是：1 2 3 4 5。如果单纯用数组的下标作为排名的话会出现问题，我想到的解决方法是引入两个变量，用来计算当前排名以及当前分数。
若后面学生分数和前面学生分数一致（即后面学生分数 = 当前分数），则后面学生的排名也要和前面学生排名保持一致（即后面学生排名 = 当前学生排名）。
若不一致，则更新当前的排名 = 数组下标，更新当前的分数 = 学生分数。

# 源代码

	//C/C++实现
	#include <iostream>
	#include <string>
	#include <vector>
	#include <algorithm>
	#include <map>

	using namespace std;

	struct student{
		int id;
		int C;
		int M;
		int E;
		int sum;
	};

	bool sortByA(const student& a, const student& b){
		return a.sum > b.sum;
	}

	bool sortByC(const student& a, const student& b){
		return a.C > b.C;
	}

	bool sortByM(const student& a, const student& b){
		return a.M > b.M;
	}

	bool sortByE(const student& a, const student& b){
		return a.E > b.E;
	}

	int main(){
		int n, m;
		scanf("%d %d", &n, &m);
		vector<student> v;
		for(int i = 0; i < n; ++i){
			student s;
			cin >> s.id >> s.C >> s.M >> s.E;
			s.sum = s.C + s.M + s.E;
			v.push_back(s);
		}
		map<int, int> mRank;
		map<int, char> mCourse;
		int currentRank, currentScore;
		//sort by A(sum)
		sort(v.begin(), v.end(), sortByA);
		currentRank = -1, currentScore = -1;
		for(int i = 0; i < v.size(); ++i){
			if(v[i].sum != currentScore){
				currentRank = i + 1;
			}
			mRank[v[i].id] = currentRank;
			mCourse[v[i].id] = 'A';
			currentScore = v[i].sum;
		}
		//sort by C
		sort(v.begin(), v.end(), sortByC);
		currentRank = -1, currentScore = -1;
		for(int i = 0; i < v.size(); ++i){
			if(v[i].C != currentScore){
				currentRank = i + 1;
			}
			if(currentRank < mRank[v[i].id]){
				mRank[v[i].id] = currentRank;
				mCourse[v[i].id] = 'C';
			}
			currentScore = v[i].C;
		}
		//sort by M
		sort(v.begin(), v.end(), sortByM);
		currentRank = -1, currentScore = -1;
		for(int i = 0; i < v.size(); ++i){
			if(v[i].M != currentScore){
				currentRank = i + 1;
			}
			if(currentRank < mRank[v[i].id]){
				mRank[v[i].id] = currentRank;
				mCourse[v[i].id] = 'M';
			}
			currentScore = v[i].M;
		}
		//sort by E
		sort(v.begin(), v.end(), sortByE);
		currentRank = -1, currentScore = -1;
		for(int i = 0; i < v.size(); ++i){
			if(v[i].E != currentScore){
				currentRank = i + 1;
			}
			if(currentRank < mRank[v[i].id]){
				mRank[v[i].id] = i + 1;
				mCourse[v[i].id] = 'E';
			}
			currentScore = v[i].E;
		}
		//output
		int tmp;
		for(int i = 0; i < m; ++i){
			scanf("%d", &tmp);
			if(mRank.count(tmp)){
				printf("%d %c\n", mRank[tmp], mCourse[tmp]);
			}
			else{
				printf("N/A\n");
			}
		}
		return 0;
	}