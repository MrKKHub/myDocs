---
title: TypeScrpt基础
date: 2021-6-3
tags:
 - TypeScrpt
categories: 
 - TypeScrpt
---

::: tip TypeScrpt基础
1. 这是关于TS基础的一些总结；<br>
:::

## 原始数据类型&any数据类型


```bash
let u: undefined = undefined
let n: null = null
let num: number = undefined

let notSure: any = 12
notSure = '12'
notSure = true

any表示可以为任意类型, 但是应尽量避免使用,否则就失去了ts严重的意义
```


## 数组&元祖

```bash
let arrNumber: number[] = [1,2,5] // 限定数组里的值为数字类型

let tuple: [string, number] = ['1', 1]

元组一定程度上表示限定数据类型和长度的数组, 元组本身还是数组,
所以可以通过使用数组的方法来突破长度限制, 但是只能push限定的类型(联合类型)
```


## interface接口

```bash
interface IPerson {
    readonly id: number,
    name: string,
    age: number,
    weight?: number
}
一般可以在命名单词前加上字母I 告诉别人这是一个接口

let user: IPerson = {
    id: 22,
    name: 'codekk',
    age: 23

限定user形状与接口形状一样, 不能多也不能少. 当接口中属性后有? 则表示可添加可不添加
// user.id = 1   
readonly表示只读属性, 与const类型  区别就是const做用于变量, readonly做用于属性.
```


## 函数

```bash
function add (x: number, y:number, z?:number): number {
    if (typeof z === 'number') {
        return x + y + z
    } {
        return x + y
    }
}
add为函数类型, 该函数无论是传参还是返回值都限定为number类型  注: 可选参数后不可再加确定参数

如果想给一个变量限定为函数类型 需要如何定义?
let add2: (x:number, y:number, z?:number) => number = add
注: 这里的箭头不是es6的箭头函数, 而是ts中声明函数类型返回值的方法 
ts中凡是在冒号后面都是在声明类型, 和实际代码逻辑没关系

interface ISum {
    (x:number, y:number, z?:number): number   // 在interface中使用: 在外面定义则用箭头
}
let add3: ISum = add
```