---
title: PAT-B 1011. A+B和C (15)
categories: PAT-B
date: 2016-09-18 23:46:57
tags:
---
# 传送门
[https://www.patest.cn/contests/pat-b-practise/1011](https://www.patest.cn/contests/pat-b-practise/1011)
<!--more-->
# 题目
> 给定区间[-2^31, 2^31]内的3个整数A、B和C，请判断A+B是否大于C。
**输入格式：**
输入第1行给出正整数T(<=10)，是测试用例的个数。随后给出T组测试用例，每组占一行，顺序给出A、B和C。整数间以空格分隔。
**输出格式：**
对每组测试用例，在一行中输出“Case #X: true”如果A+B>C，否则输出“Case #X: false”，其中X是测试用例的编号（从1开始）。
**输入样例：**4
1 2 3
2 3 4
2147483647 0 2147483646
0 -2147483648 -2147483647
**输出样例：**
Case #1: false
Case #2: true
Case #3: true
Case #4: false

# 分析
因为int类型的最大值为-2^31 ~ 2^31-1，所以不能用int类型进行运算，要选用long long类型，即可运算。

需要注意的是：
1.**C++中标准规定long的大小不小于int也就是说sizeof(long)>=sizeof(int)。**所以保险来讲要选用long long类型，可以具体求一下long的字节数和int的字节数，如果相同就选用long long即可；
2.**Java中long是64位整数**，可以用于计算。

# 源代码

    //C/C++实现
    #include <stdio.h>
    #include <iostream>

    using namespace std;

    int main(){
    	int t;
    	long long a, b, c;
    	scanf("%d", &t);
    	for(int i = 0; i < t; i++){
    		scanf("%lld %lld %lld", &a, &b, &c);
    		printf("Case #%d: %s\n", i + 1, (a + b > c ? "true" : "false"));
    	}
    	return 0;
    }

***

    //Java实现
    import java.io.BufferedReader;
    import java.io.InputStreamReader;

    /**
     * Created by Rush on 16/8/30.
     */
    public class Main {
        public static void main(String[] args) throws Exception{
            BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(System.in));
            String s = bufferedReader.readLine();
            int n = 0;
            try{
                n = Integer.valueOf(s);
            }catch (Exception e){
                System.exit(0);
            }
            long a = 0, b = 0, c = 0;
            for(int i=0;i<n;i++){
                String ss = bufferedReader.readLine();
                String[] arraySs = ss.split(" ");
                try{
                    a = Long.valueOf(arraySs[0]);
                    b = Long.valueOf(arraySs[1]);
                    c = Long.valueOf(arraySs[2]);
                }catch (Exception e){
                    System.exit(0);
                }
                System.out.println("Case #" + (i + 1) + ": " + (a + b > c ? "true" : "false"));
            }
        }
    }