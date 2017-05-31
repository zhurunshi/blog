---
title: PAT-A 1031. Hello World for U (20)
categories: PAT-A
date: 2017-02-13 23:58:40
tags:
---
# 传送门
[https://www.patest.cn/contests/pat-a-practise/1031](https://www.patest.cn/contests/pat-a-practise/1031)
<!--more-->
# 题目
> Given any string of N (>=5) characters, you are asked to form the characters into the shape of U. For example, "helloworld" can be printed as:
h&nbsp;&nbsp;&nbsp;&nbsp;d
e&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;l
l&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;r
lowo
That is, the characters must be printed in the original order, starting top-down from the left vertical line with n1 characters, then left to right along the bottom line with n2 characters, and finally bottom-up along the vertical line with n3 characters. And more, we would like U to be as squared as possible -- that is, it must be satisfied that n1 = n3 = max { k| k <= n2 for all 3 <= n2 <= N } with n1 + n2 + n3 - 2 = N.
**Input Specification:**
Each input file contains one test case. Each case contains one string with no less than 5 and no more than 80 characters in a line. The string contains no white space.
**Output Specification:**
For each test case, print the input string in the shape of U as specified in the description.
**Sample Input:**
helloworld!
**Sample Output:**
h&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;!
e&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;d
l&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;l
lowor

# 分析
首先这道题的题意不用读，光看图就看懂了，重要的就是计算行数和列数。

只要按照题目给定的条件算出来行数和列数即可，题目保证n1是最大值，所以从n2为最小值3开始计算，直到满足条件：

1.n1 + n2为偶数
2.n1 <= n2

时停止，然后根据n1和n2输出图形，方法见代码。

# 源代码

    #include <iostream>
    #include <string>

    using namespace std;

    int main(){
        int n1, n2;
        string s;
        cin >> s;
        int n = s.size();
        // 先求出行数n1和列数n2
        for (n2 = 3; n2 <= n; ++n2){
            int tmp = n + 2 - n2; // tmp = n1 + n3 = 2 * n1;
            if (tmp % 2 != 0){
                continue;
            }
            n1 = tmp / 2;
            if (n1 <= n2){
                break;
            }
        }
        int blank = n2 - 2;
        int row = n1 - 1;
        for (int i = 0; i < n1; ++i){ // 行数
            if (i < row){ // 前三行
                printf("%c", s[i]);
                cout << string(blank, ' ');
                printf("%c\n", s[n - 1 - i]);
            }
            else{
                for (int j = 0; j < n2; ++j){ // 最后一行
                    printf("%c", s[i + j]);
                }
            }
        }
        return 0;
    }