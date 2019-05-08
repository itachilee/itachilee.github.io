---
title: reserve integer
date: 2019-05-08 23:19:28
tags: leetcode
catepories: leetcode
---

Reverse Integer

Given a 32-bit signed integer, reverse digits of an integer.

```java
class Solution {
    public int reverse(int x) {
        int rev=0;
        while(x!=0){
            int pop=x%10;
            x/=10;
            if(rev>Integer.MAX_VALUE/10 ||(rev ==Integer.MAX_VALUE/10 &&pop>7)) return 0;
            if (rev < Integer.MIN_VALUE/10 || (rev == Integer.MIN_VALUE / 10 && pop < -8)) return 0;
            rev =rev *10 +pop;
        }
        return rev;
    }
}
```

```python
class Solution:
    def reverse(self, x) :
        re_string=str(x)[::-1]
        if re_string[-1]=='-':
            re_string=re_string[-1]+re_string[0:-1]
        output=int(re_string)
        if output > 2**31 or output <-2**31:
            output=0
        return(output)
```

<!--more-->

note:整形类型是有范围的，最大值为Integer.MAX_VALUE，即2的31次方2147483647，最小值为Integer.MIN_VALUE -2147483648。
对整形最大值加1，2147483648（越界了），那么此时值为多少呢？结果是-2147483648，即是Integer.MIN_VALUE。
类似的，对Integer.MIN_VALUE取反或者取绝对值呢？仍为Integer.MIN_VALUE，因为值为-2147483648，绝对值2147483648超过Integer.MAX_VALUE 2147483647。
故：
Integer.MAX_VALUE + 1 = Integer.MIN_VALUE

Math.abs(Integer.MIN_VALUE) =  Integer.MIN_VALUE