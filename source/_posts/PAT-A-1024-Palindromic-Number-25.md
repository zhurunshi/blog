---
title: PAT-A 1024. Palindromic Number (25)
categories: PAT-A
date: 2017-02-13 23:58:23
tags:
---
# 传送门
[https://www.patest.cn/contests/pat-a-practise/1024](https://www.patest.cn/contests/pat-a-practise/1024)
<!--more-->
# 题目
> A number that will be the same when it is written forwards or backwards is known as a Palindromic Number. For example, 1234321 is a palindromic number. All single digit numbers are palindromic numbers.
Non-palindromic numbers can be paired with palindromic ones via a series of operations. First, the non-palindromic number is reversed and the result is added to the original number. If the result is not a palindromic number, this is repeated until it gives a palindromic number. For example, if we start from 67, we can obtain a palindromic number in 2 steps: 67 + 76 = 143, and 143 + 341 = 484.
Given any positive integer N, you are supposed to find its paired palindromic number and the number of steps taken to find it.
**Input Specification:**
Each input file contains one test case. Each case consists of two positive numbers N and K, where N (<= 10^10) is the initial numer and K (<= 100) is the maximum number of steps. The numbers are separated by a space.
**Output Specification:**
For each test case, output two numbers, one in each line. The first number is the paired palindromic number of N, and the second number is the number of steps taken to find the palindromic number. If the palindromic number is not found after K steps, just output the number obtained at the Kth step and K instead.
**Sample Input 1:**
67 3
**Sample Output 1:**
484
2
**Sample Input 2:**
69 3
**Sample Output 2:**
1353
3

# 分析

题意是要与自身字符串的倒序相加，在给定运算次数范围内，直到和字符串满足回文的特点停止，若次数到达给定范围限制，仍不满足回文，也将停止，并将最终的和字符串输出，以及其间经过的运算次数。

先单独写了一个判断回文的函数，用于判断是否满足条件；
然后写了字符串与自身的倒叙字符串相加的函数，里面包含了模拟笔算加法的实现；
最后在for循环中根据ifPalindromic方法作为条件，反复调用add方法，直至循环结束或出现回文数终止，输出结果。

# 源代码

    #include <iostream>
    #include <string>
    #include <sstream>
    #include <algorithm>

    using namespace std;

    bool ifPalindromic(string s){
        int size = s.size();
        if(size == 1){
            return true;
        }
        else{
            for(int i = 0; i < size / 2; ++i){
                if(s[i] != s[size - 1 - i]){
                    return false;
                }
            }
            return true;
        }
    }

    string add(string s){
        string tmp = s;
        reverse(s.begin(), s.end());
        string result = "";
        int carry = 0;
        int i = tmp.size() - 1, j = s.size() - 1;
        while(i >= 0 && j >= 0){
            int a, b;
            a = (i < 0 ? 0 : tmp[i--] - '0');
            b = (j < 0 ? 0 : s[j--] - '0');
            int sum = a + b + carry;
            result = (char)(sum % 10 + '0') + result;
            carry = sum / 10;
        }
        if(carry){
            result = (char)(carry + '0') + result;
        }
        return result;
    }

    int main(){
        long long n;
        int k;
        scanf("%lld %d", &n, &k);
        int step = -1;
        stringstream ss;
        string s;
        ss << n;
        ss >> s;
        int i = 0;
        for(; i < k; ++i){
            if(!ifPalindromic(s)){
                s = add(s);
            }
            else{
                step = i;
                break;
            }
        }
        cout << s << endl;
        printf("%d", step == -1 ? i : step);
        return 0;
    }