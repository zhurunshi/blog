---
title: (String)、toString()和String.valueOf()的区别
categories: Java
date: 2017-03-31 22:46:44
tags:
---
本文将以从int类型转为String类型的方法为例，讲解从其他类型转换到String类型的各种方法，以及其中的区别。
<!--more-->
# 1.(String)强制转换一式

	Object obj = new Integer(100);
	String str = (String)obj;
	System.out.println(str);

**【失败】**
此种情况可以在语法检测上通过，但是运行后会报错：
java.lang.ClassCastException: java.lang.Integer cannot be cast to java.lang.String

# 2.(String)强制转换二式

	String str = (String)100;

![](http://upload-images.jianshu.io/upload_images/2319568-3896ace6b7ccb2ed.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
**【失败】**
从图中提示可以发现，IDE直接报错，提示不能从int类型转换为java.lang.String类型。

# 3.String特殊转换

	String str = "" + 100;
	System.out.println(str);

**【成功】**
参考的是Java规范。这里引用的是一个匿名的知乎用户的回答。原文链接：https://www.zhihu.com/question/57105649/answer/151613096
> If only one operand expression is of type String, then string conversion (§5.1.11) is performed on the other operand to produce a string at run time.The result of string concatenation is a reference to a String object that is the concatenation of the two operand strings. The characters of the left-hand operand precede the characters of the right-hand operand in the newly created string.
渣翻如下
如果其中一个操作数表达式是String，那么对另一个操作数执行字符串转换，以在运行时产生一个字符串。
字符串连接的结果是对一个String对象的引用，该对象是两个操作数字符串的连接。左侧操作数的字符位于新创建的字符串中右侧操作数的字符之前。

# 4.Integer.toString(int i)方法

	String str = Integer.toString(100);
	System.out.println(str);

**【成功】**
使用的是int的包装类中实现的toString方法。
# 5.String.valueOf(int i)方法

	String str = String.valueOf(100);
	System.out.println(str);

**【成功】**
我在查看源代码时发现调用的是Integer中的toString方法，也就是4的方法。

	public static String valueOf(int i) {
	    return Integer.toString(i);
	}

但是查看网上的资料中写的都是调用这个方法

	public static String valueOf(Object obj) {
	    return (obj == null) ? "null" : obj.toString();
	}

想了一下，发现自己有点傻，原来String.valueOf()方法经过很多重载，可以通过传入的参数类型加以区分，从而调用相应的toString()方法进行类型转换。
使用的全部是基本类型对应的包装类，类似的方法还有很多，例如：

	public static String valueOf(long l) {
	    return Long.toString(l);
	}
	public static String valueOf(float f) {
	    return Float.toString(f);
	}

# 6.总结
上述几种成功的方法中，只有String.valueOf()方法会首先对转换的对象进行判空检测，如果为空，则返回“null”字符串，以至于不会报出空指针异常。
**所以，在遇到字符串转换的时候，首选String.valueOf()方法。**

**另外，由于String.valueOf方法的内部实现是toString方法，所以在新建一个类后，如果想使用String.valueOf方法，千万不要忘记在类中重写toString方法哦。**