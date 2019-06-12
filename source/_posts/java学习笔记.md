---
title: java学习笔记
date: 2019-06-12 20:56:31
tags:
categories: java
---

### Java 跳出单个循环、多重嵌套循环

##### 退出单个循环：

使用return、break：return、break会结束整个循环(不是结束当前这一次循环，而是整个，结束后不会再执行下一次的循环）

```java
public class test {
	public static void main(String[] args) {
		
		for(int i = 0; i < 10; i++){
			System.out.println(i);
			if(i == 5)
				return;//这里等价于使用break 都是跳出整个循环
		}
	}
}

```

##### 退出多嵌套循环：

###### 方法一：

通过设置标记　跳出循环：

```
public static void main(String[] args) {
		
		OK:
		for(int i = 0; i < 10; i++){
			for(int j = 0; j < 10; j++){
				System.out.println(j);
				if(j == 5)
					break OK;//退出到ok处
			}
		}		
	}

```

输出结果：012345

###### 方法二：

通过变量判断跳过循环：

```
public static void main(String[] args) {
		
        boolean flag = false;  //设置变量
        for (int i = 0; i < 10 && !flag; i++) {  //当flag为true时跳出循环  
            for (int j = 0; j < 10; j++) {  
            	System.out.println(j);
                if (j == 5) {  
                    flag = true;  
                    break;  
                }  
            }  
        }  		
	}

```

输出结果：012345

