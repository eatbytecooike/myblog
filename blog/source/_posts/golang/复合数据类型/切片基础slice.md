---
title: 切片基础slice
p: /golang/复合数据类型/切片基础slice
date: 2018-06-16 17:06:20
tags:
categories:
- golang
- 复合数据类型
---
如下
{% include_code /source/code/go/复合数据类型/切片基础slice %}
```
package main

import (
	"fmt"
	"reflect"
)

/*
定义：slice表示一个拥有相同类型元素的可变长度的序列
slice有三个属性：指针，长度，容量
指针指向第一个可以从slice中访问的元素，这个元素并不一定是数组的第一个元素

注意：
1.一个底层数组可以对应多个slice
2.slice超过被引用对象的容量，将会宕机
 */
func main()  {
	//定义slice
	myslice := []int{1, 2, 3, 4}
	fmt.Println(reflect.TypeOf(myslice))

	//slice底层是数组,slice可以引用数组的任何位置
	var myarr [9]int = [9]int{1, 2, 3, 4, 5, 6, 7, 8, 9}
	slicearr1 := myarr[1:4]

	//slice是引用了数组，数组的值发生了改变
	slicearr1[0] = 99
	fmt.Println(slicearr1)
	fmt.Println(myarr)

	//slice用法
	slicearr2 := myarr[:5]
	slicearr3 := myarr[5:]
	slicearr4 := myarr[:]
	fmt.Println(slicearr2, slicearr3, slicearr4)

	//求长度 结果： 5 4
	fmt.Println(len(slicearr2), len(slicearr3))
	//求容量 结果： 9 4 容量实质和底层数组相关
	fmt.Println(cap(slicearr2), cap(slicearr3))

	//对string类型求子串，返回值是string
	str := "hello"
	slicestr := str[:3]
	fmt.Println(slicestr)

	//对[]byte类型做slice操作，返回值是[]byte类型
	myBytes := []byte("hello world!")
	slicemyBytes := myBytes[:5]
	fmt.Println(string(slicemyBytes))

	//slice比较，可使用bytes.Equal来比较两个字节slice,其他类型
	//则需要自己实现。不可以直接用==比较，唯一用==比较是和nil
	fmt.Println(slicemyBytes == nil)

	//内置函数make，创建一个指定元素类型，长度和容量的slice，参数容量可省略
	//make实质创建了一个无名数组并返回了它的一个slice
	myslice2 := make([]int, 5, 10)
	fmt.Println(myslice2)
}
```
