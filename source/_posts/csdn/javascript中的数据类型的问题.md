---
title: javascript中的数据类型的问题
date: 2015-08-04 10:51:11
tags: javascript
---
# undefined 与null 
如果用alert(undefined==null)，这个一定是打印的是true ，因为他两个都是空的,当用alert(undefined===null);的时候，就不false了，为什么呢？因为这两个值的类型是不同的，alert(undefined);=undefined，而alert(null);=object 这时候，就能看出这两个东西有什么不同了。
可以参看 http://www.ruanyifeng.com/blog/2014/03/undefined-vs-null.html
# NaN 
NaN 属性是代表非数字值的特殊值。该属性用于指示某个值不是数字。可以把 Number 对象设置为该值，来指示其不是数字值。
提示：使用 isNaN() 全局函数来判断一个值是否是 NaN 值。
例如 ：alert(Number.NaN); //NaN
alert(NaN+1);	//NaN
alert(NaN==NaN);//false
这里可以看出来，它自己是不与自己相等的，更不要说别的东西了，也就是说，他谁都不等
alert(isNaN(25)) //false
alert(isNaN("25"))//false 这个是自己会转成数字
alert(isNaN("lee"))//true
alert(isNaN(true))//false 转成了1
alert(isNaN(false )) //false 转成0
alert(isNaN(NaN)) //true

isNaN()函数也适用于对象，在调用isNaN()函数过程中，首先会调用valueOf()方法，然后确定返回值是否转换成数值，如果不能，则基于这个返回值再调用toString()方法，再测试返回值

# parseInt() 
parseInt(); 只会从第一位起，到不为数值的字符串为止，也支持16进制与8进制,2进制的字符串，当然这里我们是要传入参数的，
parseInt("0xae",16);
parseFloat() 是不认识16进制的