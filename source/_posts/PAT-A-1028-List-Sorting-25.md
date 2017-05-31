---
title: PAT-A 1028. List Sorting (25)
categories: PAT-A
date: 2017-02-13 23:58:36
tags:
---
# 传送门
[https://www.patest.cn/contests/pat-a-practise/1028](https://www.patest.cn/contests/pat-a-practise/1028)
<!--more-->
# 题目
> Excel can sort records according to any column. Now you are supposed to imitate this function.
**Input**
Each input file contains one test case. For each case, the first line contains two integers N (<=100000) and C, where N is the number of records and C is the column that you are supposed to sort the records with. Then N lines follow, each contains a record of a student. A student's record consists of his or her distinct ID (a 6-digit number), name (a string with no more than 8 characters without space), and grade (an integer between 0 and 100, inclusive).
**Output**
For each test case, output the sorting result in N lines. That is, if C = 1 then the records must be sorted in increasing order according to ID's; if C = 2 then the records must be sorted in non-decreasing order according to names; and if C = 3 then the records must be sorted in non-decreasing order according to grades. If there are several students who have the same name or grade, they must be sorted according to their ID's in increasing order.
**Sample Input 1**
3 1
000007 James 85
000010 Amy 90
000001 Zoe 60
**Sample Output 1**
000001 Zoe 60
000007 James 85
000010 Amy 90
**Sample Input 2**
4 2
000007 James 85
000010 Amy 90
000001 Zoe 60
000002 James 98
**Sample Output 2**
000010 Amy 90
000002 James 98
000007 James 85
000001 Zoe 60
**Sample Input 3**
4 3
000007 James 85
000010 Amy 90
000001 Zoe 60
000002 James 90
**Sample Output 3**
000001 Zoe 60
000007 James 85
000002 James 90
000010 Amy 90

# 分析
题意：
首先输入两个数N和c，N是接下来输入的数据条数，c是排序方式。
c=1用ID升序；c=2用姓名升序；c=3用成绩升序。
若姓名或成绩相同，用ID升序排列（ID唯一）。

用的是结构体数组处理，然后用sort()排序，单独写3种排序方式按需调用即可。

注意：输入输出能用scanf/printf就别用cin/cout，会超时。

# 源代码

    #include <iostream>
    #include <string>
    #include <vector>
    #include <algorithm>

    using namespace std;

    struct student{
        int id;
        string name;
        int grade;
    };

    bool sortById(const student& a, const student& b){
        return a.id < b.id;
    }

    bool sortByName(const student& a, const student& b){
        if (a.name == b.name){
            return a.id < b.id;
        }
        else{
            return a.name < b.name;
        }
    }

    bool sortByGrade(const student& a, const student& b){
        if (a.grade == b.grade){
            return a.id < b.id;
        }
        else{
            return a.grade < b.grade;
        }
    }

    int main(){
        int n, c;
        scanf("%d %d", &n, &c);
        vector<struct student> v(n);
        for (int i = 0; i < n; ++i){
            scanf("%d", &v[i].id);
            cin >> v[i].name;
            scanf("%d", &v[i].grade);
        }
        if (1 == c){
            sort(v.begin(), v.end(), sortById);
        }
        else if (2 == c){
            sort(v.begin(), v.end(), sortByName);
        }
        else if (3 == c){
            sort(v.begin(), v.end(), sortByGrade);
        }
        for (int i = 0; i < n; ++i){
            printf("%06d ", v[i].id);
            cout << v[i].name;
            printf(" %d\n", v[i].grade);
        }
        return 0;
    }