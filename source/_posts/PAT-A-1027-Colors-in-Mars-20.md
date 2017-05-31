---
title: PAT-A 1027. Colors in Mars (20)
categories: PAT-A
date: 2017-02-13 23:58:26
tags:
---
# 传送门
[https://www.patest.cn/contests/pat-a-practise/1027](https://www.patest.cn/contests/pat-a-practise/1027)
<!--more-->
# 题目
> People in Mars represent the colors in their computers in a similar way as the Earth people. That is, a color is represented by a 6-digit number, where the first 2 digits are for Red, the middle 2 digits for Green, and the last 2 digits for Blue. The only difference is that they use radix 13 (0-9 and A-C) instead of 16. Now given a color in three decimal numbers (each between 0 and 168), you are supposed to output their Mars RGB values.
**Input**
Each input file contains one test case which occupies a line containing the three decimal color values.
**Output**
For each test case you should output the Mars RGB value in the following format: first output "#", then followed by a 6-digit number where all the English characters must be upper-cased. If a single color is only 1-digit long, you must print a "0" to the left.
**Sample Input**
15 43 71
**Sample Output**
\#123456

# 分析
题意：
其实就是一道10进制转13进制的题目包装了一下，另外输出如果不足两位需要前面补0。

模拟笔算的短除法即可，这里只可能出现两位的13进制数，所以可以单独处理两次循环，会更简单。

注意输入0 0 0，输出是#000000，其他没什么特殊的。

# 源代码

    #include <iostream>

    using namespace std;

    string radix(int tmp){
        string s = "";
        int count = 0; //记录循环次数，与输出的位数相同 
        while(tmp){
            int rest = tmp % 13;
            ++count;
            if(rest >= 0 && rest <= 9){
                s = (char)(rest + '0') + s;
            }
            else if(rest == 10){
                s = 'A' + s;
            }
            else if(rest == 11){
                s = 'B' + s;
            }
            else if(rest == 12){
                s = 'C' + s;
            }
            tmp /= 13;
        }
        if(count == 0){ //若没循环，则用00补位 
            s = "00" + s;
        }
        else if(count == 1){ //若只循环一次，则用0补位 
            s = '0' + s;
        }
        return s;
    }

    int main(){
        int a, b, c;
        scanf("%d %d %d", &a, &b, &c);
        cout << "#" << radix(a) << radix(b) << radix(c);
        return 0;
    }