---
title: PAT-A 1019. General Palindromic Number (20)
categories: PAT-A
date: 2017-02-13 23:58:02
tags:
---
# 传送门
[https://www.patest.cn/contests/pat-a-practise/1019](https://www.patest.cn/contests/pat-a-practise/1019)
<!--more-->
# 题目
> A number that will be the same when it is written forwards or backwards is known as a Palindromic Number. For example, 1234321 is a palindromic number. All single digit numbers are palindromic numbers.
Although palindromic numbers are most often considered in the decimal system, the concept of palindromicity can be applied to the natural numbers in any numeral system. Consider a number N > 0 in base b >= 2, where it is written in standard notation with k+1 digits ai as the sum of (aibi) for i from 0 to k. Here, as usual, 0 <= ai < b for all i and ak is non-zero. Then N is palindromic if and only if ai = ak-i for all i. Zero is written 0 in any base and is also palindromic by definition.
Given any non-negative decimal integer N and a base b, you are supposed to tell if N is a palindromic number in base b.
**Input Specification:**
Each input file contains one test case. Each case consists of two non-negative numbers N and b, where 0 <= N <= 109 is the decimal number and 2 <= b <= 109 is the base. The numbers are separated by a space.
**Output Specification:**
For each test case, first print in one line "Yes" if N is a palindromic number in base b, or "No" if not. Then in the next line, print N as the number in base b in the form "ak ak-1 ... a0". Notice that there must be no extra space at the end of output.
**Sample Input 1:**
27 2
**Sample Output 1:**
Yes
1 1 0 1 1
**Sample Input 2:**
121 5
**Sample Output 2:**
No
4 4 1

# 分析
题意：
根据输入的N和b，将其转换为b进制的数，然后判断转换后的数是否回文，并输出转换后的数，每位空1格。

因为进制可能会很大，所以会出现每位数字很大的情况，所以考虑用一个数组放置进制转换后每位的数字，转换完成后，对称比较其大小是否一致，若比较过程中出现不一致则认定不是回文数，反之则是回文数。

注意：若数字只有一位则认定是回文数，另外还要单独考虑输入N=0的情况是否输出正确。

# 源代码

    #include <iostream>
    #include <vector>

    using namespace std;

    int main(){
        int n, b;
        scanf("%d %d", &n, &b);
        vector<int> v;
        if(n == 0){ // input: 0 x
            printf("Yes\n0");
            return 0;
        }
        while(n){
            int rest = n % b;
            v.push_back(rest);
            n /= b;
        }
        int size = v.size();
        if(size == 1){ // All single digit numbers are palindromic numbers
            printf("Yes\n%d", v[0]);
        }
        else{
            bool ifPalindromic = true;
            for(int i = 0; i < size / 2; ++i){
                if(v[i] != v[size - 1 - i]){
                    ifPalindromic = false;
                    break;
                }
            }
            ifPalindromic ? printf("Yes\n") : printf("No\n");
            printf("%d", v[size - 1]);
            for(int i = size - 2; i >= 0; --i){
                printf(" %d", v[i]);
            }
        }
        return 0;
    }