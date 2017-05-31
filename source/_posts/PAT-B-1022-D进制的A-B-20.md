---
title: PAT-B 1022. D进制的A+B (20)
categories: PAT-B
date: 2016-09-26 09:17:17
tags:
---
# 传送门
[https://www.patest.cn/contests/pat-b-practise/1022](https://www.patest.cn/contests/pat-b-practise/1022)
<!--more-->
# 题目
> 输入两个非负10进制整数A和B(<=2^30-1)，输出A+B的D (1 < D <= 10)进制数。
**输入格式：**
输入在一行中依次给出3个整数A、B和D。
**输出格式：**
输出A+B的D进制数。
**输入样例：**
123 456 8
**输出样例：**
1103

# 分析
就是根据短除法的代码实现，平时都是拿数组做的，这次我用栈来练习一下。

遇到的坑：
如果栈顶是0，即开头数字是0，则不输出，数组实现也同理。

# 源代码

    //C/C++实现
    #include <iostream>
    #include <stack>

    using namespace std;

    int main(){
    	int a, b, d;
    	scanf("%d %d %d", &a, &b, &d);
    	stack<int> s;
    	int tmp = a + b;
    	int rest;
    	do{
    		s.push(tmp %d);
    		tmp /= d;
    	}while(tmp != 0);
    	while(!s.empty()){
    		printf("%d", s.top());
    		s.pop();
    	}
    	printf("%c", '\n');
    	return 0;
    }

***

    //Java实现
    import java.io.BufferedReader;
    import java.io.InputStreamReader;

    public class Main {
        public static void main(String[] args) throws Exception {
            BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(System.in));
            String s = bufferedReader.readLine();
            String[] arrayS = s.split(" ");
            if(arrayS.length != 3){
                System.exit(0);
            }
            int a = 0,b = 0,d = 0;
            try{
                a = Integer.valueOf(arrayS[0]);
                b = Integer.valueOf(arrayS[1]);
                d = Integer.valueOf(arrayS[2]);
            }catch(Exception e) {
                System.exit(0);
            }
            if(a < 0 || a > 1073741823 || b < 0 || b > 1073741823 || d <= 1 || d > 10){
                System.exit(0);
            }
            f(a+b,d);
        }
        public static void f(int num,int target){
            int tmp = 0;
            if(num / target != 0){
                tmp = num / target;
                f(tmp,target);
                System.out.print(num % target);
            }
            else{
                System.out.print(num % target);
                return;
            }
        }
    }