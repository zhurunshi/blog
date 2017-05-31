---
title: PAT-A 1036. Boys vs Girls (25)
categories: PAT-A
date: 2017-02-13 23:58:50
tags:
---
# 传送门
[https://www.patest.cn/contests/pat-a-practise/1036](https://www.patest.cn/contests/pat-a-practise/1036)
<!--more-->
# 题目
> This time you are asked to tell the difference between the lowest grade of all the male students and the highest grade of all the female students.
**Input Specification:**
Each input file contains one test case. Each case contains a positive integer N, followed by N lines of student information. Each line contains a student's name, gender, ID and grade, separated by a space, where name and ID are strings of no more than 10 characters with no space, gender is either F (female) or M (male), and grade is an integer between 0 and 100. It is guaranteed that all the grades are distinct.
**Output Specification:**
For each test case, output in 3 lines. The first line gives the name and ID of the female student with the highest grade, and the second line gives that of the male student with the lowest grade. The third line gives the difference gradeF-gradeM. If one such kind of student is missing, output "Absent" in the corresponding line, and output "NA" in the third line instead.
**Sample Input 1:**
3
Joe M Math990112 89
Mike M CS991301 100
Mary F EE990830 95
**Sample Output 1:**
Mary EE990830
Joe Math990112
6
**Sample Input 2:**
1
Jean M AA980920 60
**Sample Output 2:**
Absent
Jean AA980920
NA

# 分析

这道题要根据输入的学生信息，找出成绩最好的女生和成绩最差的男生（为什么？？？），然后输出其姓名和学号，最后输出女生最好成绩与男生最差成绩的差值。

不需要存每一次输入的学生信息，若为女生且成绩比原先最高成绩高，则更新为该学生的信息；若为男生且成绩比原先最低成绩低，则更新为该学生的信息。

若未出现某一性别的学生，则输出Absent，然后最后一行输出NA。

# 源代码

    #include <iostream>
    #include <string>

    using namespace std;

    struct student{
        string name;
        string id;
        int grade;
    };

    int main(){
        int n;
        scanf("%d", &n);
        string tmpName;
        char tmpGender;
        string tmpId;
        int tmpGrade;
        struct student male;
        male.grade = 101;
        struct student female;
        female.grade = -1;
        for(int i = 0; i < n; ++i){
            cin >> tmpName >> tmpGender >> tmpId >> tmpGrade;
            if(tmpGender == 'M'){
                if(tmpGrade < male.grade){
                    male.name = tmpName;
                    male.id = tmpId;
                    male.grade = tmpGrade;
                }
            }
            else if(tmpGender == 'F'){
                if(tmpGrade > female.grade){
                    female.name = tmpName;
                    female.id = tmpId;
                    female.grade = tmpGrade;
                }
            }
        }
        if(female.grade == -1){
            printf("Absent\n");
        }
        else{
            cout << female.name << " " << female.id << endl;
        }
        if(male.grade == 101){
            printf("Absent\n");
        }
        else{
            cout << male.name << " " << male.id << endl;
        }
        if(female.grade == -1 || male.grade == 101){
            printf("NA");
        }
        else{
            printf("%d", female.grade - male.grade);
        }
        return 0;
    }