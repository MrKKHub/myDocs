---
title: JavaScript常见问题(一)
date: 2020-06-12
tags:
 - JavaScript
categories: 
 - JavaScript
---

::: tip JavaScript常见问题(一)
:::

## 数据类型检测

```bash
基本数据类型: number string boolean undefined null
typeof 检测基本数据类型时都都会正常返回对应类型
null 除外.  null会返回object.  原因是null存储的机器码尾数000的形式 而这种形式typeof检测时都会返回object类型

注: typeof 检测引用数据类型时  会有两种返回结果: object function
    数据为引用类型-->以函数形式时会内置一个[[call]]方法
    判断时会根据是否有[[call]]方法来判断, 有则function 无则object
-------------------------------------------------------------------------->

instanceof 返回结果是Boolean值   true or false
检测方式为  A instanceof B   意思是A对象是否是由B对象实例化而来(会顺着原型链一直往上进行判断)
因此:  [] instanceof Object -->  true    
    function Person () {}    new Person() instance Person --> true;  new Person instanceof Object --> true;

也可以用以下方式进行判断:
Object.prototype.toString.call(['hsk']) ----> [object Array]
Object.prototype.toString.call('hsk')  ---> [object String]
Object.prototype.toString.call({name: 'hsk'}) --->  [object Object]
```

## 深浅拷贝的几种方式
```bash
1. Object.create()  ---> 浅拷贝
let obj = { name: 'hsk' }
let newObj = Object.create(obj)   --> 会将obj中的属性复制到newObj对象的_proty_属性上去

2. 循环遍历  ---> 深拷贝
function deepClone (original, target) {
    let newObj = target || {}
    for (let key in original) {
        if (typeof original[key] === 'object') {
            newObj[key] = Array.isArray(original[key]) ? [] : {}
            deepClone(original[key], newObj[key])
        } else {
            newObj[key] = original[key]
        }
    }
    return newObj
}
3. JSON.stringify() JSON.parse()  ---> 深拷贝
let newObj = JSON.parse(JSON.stringify(obj))

```

## 隐式类型转换

```bash
NAN 0 undefined null  ""   Boolean都是转为false 其他都是true

== 比较时会做隐式类型转换   === 则不会  需要值和类型都要相等
```

## javascript内置对象

```bash
三种包装对象:  String Number Boolean
常用内置对象:  Array Date Function Object
```
