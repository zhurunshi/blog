---
title: PAT 乙级真题 题解目录
categories: PAT-B
date: 2016-11-05 22:37:00
tags:
---
前60题写于：2016.09.09 - 2016.11.05
全部是C/C++混输代码，少量简单题也有Java代码
后面如有新题会继续补充……
<!--more-->

[写在最前](http://zhurunshi.com/PAT-B-%E5%86%99%E5%9C%A8%E6%9C%80%E5%89%8D/)
[1001. 害死人不偿命的(3n+1)猜想 (15)](http://zhurunshi.com/PAT-B-1001-%E5%AE%B3%E6%AD%BB%E4%BA%BA%E4%B8%8D%E5%81%BF%E5%91%BD%E7%9A%84-3n-1-%E7%8C%9C%E6%83%B3-15/)
[1002. 写出这个数 (20)](http://zhurunshi.com/PAT-B-1002-%E5%86%99%E5%87%BA%E8%BF%99%E4%B8%AA%E6%95%B0-20/)
[1003. 我要通过！(20)](http://zhurunshi.com/PAT-B-1003-%E6%88%91%E8%A6%81%E9%80%9A%E8%BF%87%EF%BC%81-20/)
[1004. 成绩排名 (20)](http://zhurunshi.com/PAT-B-1004-%E6%88%90%E7%BB%A9%E6%8E%92%E5%90%8D-20/)
[1005. 继续(3n+1)猜想 (25)](http://zhurunshi.com/PAT-B-1005-%E7%BB%A7%E7%BB%AD-3n-1-%E7%8C%9C%E6%83%B3-25/)
[1006. 换个格式输出整数 (15)](http://zhurunshi.com/PAT-B-1006-%E6%8D%A2%E4%B8%AA%E6%A0%BC%E5%BC%8F%E8%BE%93%E5%87%BA%E6%95%B4%E6%95%B0-15/)
[1007. 素数对猜想 (20)](http://zhurunshi.com/PAT-B-1007-%E7%B4%A0%E6%95%B0%E5%AF%B9%E7%8C%9C%E6%83%B3-20/)
[1008. 数组元素循环右移问题 (20)](http://zhurunshi.com/PAT-B-1008-%E6%95%B0%E7%BB%84%E5%85%83%E7%B4%A0%E5%BE%AA%E7%8E%AF%E5%8F%B3%E7%A7%BB%E9%97%AE%E9%A2%98-20/)
[1009. 说反话 (20)](http://zhurunshi.com/PAT-B-1009-%E8%AF%B4%E5%8F%8D%E8%AF%9D-20/)
[1010. 一元多项式求导 (25)](http://zhurunshi.com/PAT-B-1010-%E4%B8%80%E5%85%83%E5%A4%9A%E9%A1%B9%E5%BC%8F%E6%B1%82%E5%AF%BC-25/)
[1011. A+B和C (15)](http://zhurunshi.com/PAT-B-1011-A-B%E5%92%8CC-15/)
[1012. 数字分类 (20)](http://zhurunshi.com/PAT-B-1012-%E6%95%B0%E5%AD%97%E5%88%86%E7%B1%BB-20/)
[1013. 数素数 (20)](http://zhurunshi.com/PAT-B-1013-%E6%95%B0%E7%B4%A0%E6%95%B0-20/)
[1014. 福尔摩斯的约会 (20)](http://zhurunshi.com/PAT-B-1014-%E7%A6%8F%E5%B0%94%E6%91%A9%E6%96%AF%E7%9A%84%E7%BA%A6%E4%BC%9A-20/)
[1015. 德才论 (25)](http://zhurunshi.com/PAT-B-1015-%E5%BE%B7%E6%89%8D%E8%AE%BA-25/)
[1016. 部分A+B (15)](http://zhurunshi.com/PAT-B-1016-%E9%83%A8%E5%88%86A-B-15/)
[1017. A除以B (20)](http://zhurunshi.com/PAT-B-1017-A%E9%99%A4%E4%BB%A5B-20/)
[1018. 锤子剪刀布 (20)](http://zhurunshi.com/PAT-B-1018-%E9%94%A4%E5%AD%90%E5%89%AA%E5%88%80%E5%B8%83-20/)
[1019. 数字黑洞 (20)](http://zhurunshi.com/PAT-B-1019-%E6%95%B0%E5%AD%97%E9%BB%91%E6%B4%9E-20/)
[1020. 月饼 (25)](http://zhurunshi.com/PAT-B-1020-%E6%9C%88%E9%A5%BC-25/)
[1021. 个位数统计 (15)](http://zhurunshi.com/PAT-B-1021-%E4%B8%AA%E4%BD%8D%E6%95%B0%E7%BB%9F%E8%AE%A1-15/)
[1022. D进制的A+B (20)](http://zhurunshi.com/PAT-B-1022-D%E8%BF%9B%E5%88%B6%E7%9A%84A-B-20/)
[1023. 组个最小数 (20)](http://zhurunshi.com/PAT-B-1023-%E7%BB%84%E4%B8%AA%E6%9C%80%E5%B0%8F%E6%95%B0-20/)
[1024. 科学计数法 (20)](http://zhurunshi.com/PAT-B-1024-%E7%A7%91%E5%AD%A6%E8%AE%A1%E6%95%B0%E6%B3%95-20/)
[1025. 反转链表 (25)](http://zhurunshi.com/PAT-B-1025-%E5%8F%8D%E8%BD%AC%E9%93%BE%E8%A1%A8-25/)
[1026. 程序运行时间(15)](http://zhurunshi.com/PAT-B-1026-%E7%A8%8B%E5%BA%8F%E8%BF%90%E8%A1%8C%E6%97%B6%E9%97%B4-15/)
[1027. 打印沙漏(20)](http://zhurunshi.com/PAT-B-1027-%E6%89%93%E5%8D%B0%E6%B2%99%E6%BC%8F-20/)
[1028. 人口普查(20)](http://zhurunshi.com/PAT-B-1028-%E4%BA%BA%E5%8F%A3%E6%99%AE%E6%9F%A5-20/)
[1029. 旧键盘(20)](http://zhurunshi.com/PAT-B-1029-%E6%97%A7%E9%94%AE%E7%9B%98-20/)
[1030. 完美数列(25)](http://zhurunshi.com/PAT-B-1030-%E5%AE%8C%E7%BE%8E%E6%95%B0%E5%88%97-25/)
[1031. 查验身份证(15)](http://zhurunshi.com/PAT-B-1031-%E6%9F%A5%E9%AA%8C%E8%BA%AB%E4%BB%BD%E8%AF%81-15/)
[1032. 挖掘机技术哪家强(20)](http://zhurunshi.com/PAT-B-1032-%E6%8C%96%E6%8E%98%E6%9C%BA%E6%8A%80%E6%9C%AF%E5%93%AA%E5%AE%B6%E5%BC%BA-20/)
[1033. 旧键盘打字(20)](http://zhurunshi.com/PAT-B-1033-%E6%97%A7%E9%94%AE%E7%9B%98%E6%89%93%E5%AD%97-20/)
[1034. 有理数四则运算(20)](http://zhurunshi.com/PAT-B-1034-%E6%9C%89%E7%90%86%E6%95%B0%E5%9B%9B%E5%88%99%E8%BF%90%E7%AE%97-20/)
[1035. 插入与归并(25)](http://zhurunshi.com/PAT-B-1035-%E6%8F%92%E5%85%A5%E4%B8%8E%E5%BD%92%E5%B9%B6-25/)
[1036. 跟奥巴马一起编程(15)](http://zhurunshi.com/PAT-B-1036-%E8%B7%9F%E5%A5%A5%E5%B7%B4%E9%A9%AC%E4%B8%80%E8%B5%B7%E7%BC%96%E7%A8%8B-15/)
[1037. 在霍格沃茨找零钱（20）](http://zhurunshi.com/PAT-B-1037-%E5%9C%A8%E9%9C%8D%E6%A0%BC%E6%B2%83%E8%8C%A8%E6%89%BE%E9%9B%B6%E9%92%B1%EF%BC%8820%EF%BC%89/)
[1038. 统计同成绩学生(20)](http://zhurunshi.com/PAT-B-1038-%E7%BB%9F%E8%AE%A1%E5%90%8C%E6%88%90%E7%BB%A9%E5%AD%A6%E7%94%9F-20/)
[1039. 到底买不买（20）](http://zhurunshi.com/PAT-B-1039-%E5%88%B0%E5%BA%95%E4%B9%B0%E4%B8%8D%E4%B9%B0%EF%BC%8820%EF%BC%89/)
[1040. 有几个PAT（25）](http://zhurunshi.com/PAT-B-1040-%E6%9C%89%E5%87%A0%E4%B8%AAPAT%EF%BC%8825%EF%BC%89/)
[1041. 考试座位号(15)](http://zhurunshi.com/PAT-B-1041-%E8%80%83%E8%AF%95%E5%BA%A7%E4%BD%8D%E5%8F%B7-15/)
[1042. 字符统计(20)](http://zhurunshi.com/PAT-B-1042-%E5%AD%97%E7%AC%A6%E7%BB%9F%E8%AE%A1-20/)
[1043. 输出PATest(20)](http://zhurunshi.com/PAT-B-1043-%E8%BE%93%E5%87%BAPATest-20/)
[1044. 火星数字(20)](http://zhurunshi.com/PAT-B-1044-%E7%81%AB%E6%98%9F%E6%95%B0%E5%AD%97-20/)
[1045. 快速排序(25)](http://zhurunshi.com/PAT-B-1045-%E5%BF%AB%E9%80%9F%E6%8E%92%E5%BA%8F-25/)
[1046. 划拳(15)](http://zhurunshi.com/PAT-B-1046-%E5%88%92%E6%8B%B3-15/)
[1047. 编程团体赛(20)](http://zhurunshi.com/PAT-B-1047-%E7%BC%96%E7%A8%8B%E5%9B%A2%E4%BD%93%E8%B5%9B-20/)
[1048. 数字加密(20)](http://zhurunshi.com/PAT-B-1048-%E6%95%B0%E5%AD%97%E5%8A%A0%E5%AF%86-20/)
[1049. 数列的片段和(20)](http://zhurunshi.com/PAT-B-1049-%E6%95%B0%E5%88%97%E7%9A%84%E7%89%87%E6%AE%B5%E5%92%8C-20/)
[1050. 螺旋矩阵(25)](http://zhurunshi.com/PAT-B-1050-%E8%9E%BA%E6%97%8B%E7%9F%A9%E9%98%B5-25/)
[1051. 复数乘法 (15)](http://zhurunshi.com/PAT-B-1051-%E5%A4%8D%E6%95%B0%E4%B9%98%E6%B3%95-15/)
[1052. 卖个萌 (20)](http://zhurunshi.com/PAT-B-1052-%E5%8D%96%E4%B8%AA%E8%90%8C-20/)
[1053. 住房空置率 (20)](http://zhurunshi.com/PAT-B-1053-%E4%BD%8F%E6%88%BF%E7%A9%BA%E7%BD%AE%E7%8E%87-20/)
[1054. 求平均值 (20)](http://zhurunshi.com/PAT-B-1054-%E6%B1%82%E5%B9%B3%E5%9D%87%E5%80%BC-20/)
[1055. 集体照 (25)](http://zhurunshi.com/PAT-B-1055-%E9%9B%86%E4%BD%93%E7%85%A7-25/)
[1056. 组合数的和(15)](http://zhurunshi.com/PAT-B-1056-%E7%BB%84%E5%90%88%E6%95%B0%E7%9A%84%E5%92%8C-15/)
[1057. 数零壹(20)](http://zhurunshi.com/PAT-B-1057-%E6%95%B0%E9%9B%B6%E5%A3%B9-20/)
[1058. 选择题(20)](http://zhurunshi.com/PAT-B-1058-%E9%80%89%E6%8B%A9%E9%A2%98-20/)
[1059. C语言竞赛(20)](http://zhurunshi.com/PAT-B-1059-C%E8%AF%AD%E8%A8%80%E7%AB%9E%E8%B5%9B-20/)
[1060. 爱丁顿数(25)](http://zhurunshi.com/PAT-B-1060-%E7%88%B1%E4%B8%81%E9%A1%BF%E6%95%B0-25/)
[1061. 判断题(15)](http://zhurunshi.com/PAT-B-1061-%E5%88%A4%E6%96%AD%E9%A2%98-15/)
[1062. 最简分数(20)](http://zhurunshi.com/PAT-B-1062-%E6%9C%80%E7%AE%80%E5%88%86%E6%95%B0-20/)
[1063. 计算谱半径(20)](http://zhurunshi.com/PAT-B-1063-%E8%AE%A1%E7%AE%97%E8%B0%B1%E5%8D%8A%E5%BE%84-20/)
[1064. 朋友数(20)](http://zhurunshi.com/PAT-B-1064-%E6%9C%8B%E5%8F%8B%E6%95%B0-20/)
[1065. 单身狗(25)](http://zhurunshi.com/PAT-B-1065-%E5%8D%95%E8%BA%AB%E7%8B%97-25/)
[1066. 图像过滤(15)](http://zhurunshi.com/PAT-B-1066-%E5%9B%BE%E5%83%8F%E8%BF%87%E6%BB%A4-15/)
[1067. 试密码(20)](http://zhurunshi.com/PAT-B-1067-%E8%AF%95%E5%AF%86%E7%A0%81-20/)
[1068. 万绿丛中一点红(20)](http://zhurunshi.com/PAT-B-1068-%E4%B8%87%E7%BB%BF%E4%B8%9B%E4%B8%AD%E4%B8%80%E7%82%B9%E7%BA%A2-20/)
[1069. 微博转发抽奖(20)](http://zhurunshi.com/PAT-B-1069-%E5%BE%AE%E5%8D%9A%E8%BD%AC%E5%8F%91%E6%8A%BD%E5%A5%96-20/)
[1070. 结绳(25)](http://zhurunshi.com/PAT-B-1070-%E7%BB%93%E7%BB%B3-25/)