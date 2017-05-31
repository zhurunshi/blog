---
title: PAT-A 1023. Have Fun with Numbers (20)
categories: PAT-A
date: 2017-02-13 23:58:19
tags:
---
# 传送门
[https://www.patest.cn/contests/pat-a-practise/1023](https://www.patest.cn/contests/pat-a-practise/1023)
<!--more-->
# 题目
> Notice that the number 123456789 is a 9-digit number consisting exactly the numbers from 1 to 9, with no duplication. Double it we will obtain 246913578, which happens to be another 9-digit number consisting exactly the numbers from 1 to 9, only in a different permutation. Check to see the result if we double it again!
Now you are suppose to check if there are more numbers with this property. That is, double a given number with k digits, you are to tell if the resulting number consists of only a permutation of the digits in the original number.
**Input Specification:**
Each input file contains one test case. Each case contains one positive integer with no more than 20 digits.
**Output Specification:**
For each test case, first print in a line "Yes" if doubling the input number gives a number that consists of only a permutation of the digits in the original number, or "No" if not. Then in the next line, print the doubled number.
**Sample Input:**
1234567899
**Sample Output:**
Yes
2469135798

# 分析
题意：
根据输入数字，先判断其1-9出现的次数，然后将其乘以二，再计算之后数字中1-9出现的次数，是否与之前一致，若一致输出Yes，反之输出No，接着再输出乘以二后的数字。

因为题目中规定，输出数字不超过20位，考虑最大情况20位，而查了下资料发现long long的范围最多是支持18位，所以题目要考查的肯定是编写模拟手算乘法这个点

我用了carry变量作为进位，每次相乘后要再加上进位，然后对10取余作为每位的数，将除以10的结果作为进位保存，以便更高位运算，这里要注意最高位计算完成后还可能有进位情况，要考虑到。

# 源代码

    #include <iostream>
    #include <string>
    #include <vector>

    using namespace std;

    int countOld[11], countNew[11];

    int main(){
        string s1;
        cin >> s1;
        for(int i = 0; i < s1.size(); ++i){
            ++countOld[(int)(s1[i] - '0')];
        }
        // * 2
        vector<int> v;
        const int NUM = 2;
        int carry = 0;
        for(int i = s1.size() - 1; i >= 0; --i){
            int tmp = (s1[i] - '0') * NUM + carry;
            carry = tmp / 10;
            v.push_back(tmp % 10);
        }
        if(carry){ //最高位进位情况 
            v.push_back(carry);
        }
        // count
        for(int i = 0; i < v.size(); ++i){
            ++countNew[v[i]];
        }
        bool ifEquals = true;
        for(int i = 0; i < 11; ++i){
            if(countOld[i] != countNew[i]){
                ifEquals = false;
                break;
            }
        }
        ifEquals ? printf("Yes\n") : printf("No\n");
        for(int i = v.size() - 1; i >= 0; --i){
            printf("%d", v[i]);
        }
        return 0;
    }