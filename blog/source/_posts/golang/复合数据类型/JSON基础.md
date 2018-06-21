---
title: post
p: /golang/复合数据类型/JSON基础
date: 2018-06-20 13:55:57
tags:
categories:
- golang
- 复合数据类型
---
```
package main

import (
	"encoding/json"
	"log"
	"fmt"
)

/*
JavaScript对象表示法(JSON)是一种发送和接收格式化信息的标准。
JSON是JavaScript值的Unicode编码，包括 字符串 数字 布尔值 数组 对象
数字：十进制或科学计数法表示。go语言数字类型会变成json浮点型 例如： -231.12
布尔值：true或false。 例如：true
字符串：双引号括起来的Unicode代码点的序列，使用反斜杠作为转义字符。 例如： "hello \" "
数组:方括号括起来，使用逗号分隔元素。用来编码GO语言中的数组和slice。 例如：["gold", "silver", "bronze"]

 */

 //结构体成员名首字母大写才可以转换JSON
 type Movie struct {
 	Title string  //字符串
 	Year int `json:"date"` //整型 对应到date的成员标签
 	Important bool  //布尔类型
 	Lists []string  //slice
 	Point *int  //指针 取得指针指向的值，空指针则对应null
 	Object Ob  //对象
 }

 type Ob struct {
 	myname string
 }



func main()  {
	po1 := new(int)
	*po1 = 10
	ob1 := Ob{"biliy"}
	m1 := []Movie{
		{"GL1", 1997, true, []string{"str1", "str2"}, po1, ob1},
		{"GL2", 1998, true, []string{"str11", "str22"}, po1, ob1},
		{"GL3", 1999, true, []string{"str111", "str222"}, po1, ob1},
	}

	//将go数据结构转换成json。实现了一个接口的所有方法意味着实现了这个接口，所以任何类都实现了空接口
	data1, err := json.Marshal(m1)
	if err != nil {
		log.Fatal("JSON marshaling failed : %s", err)
	}
	fmt.Printf("%s\n", data1)

	//格式化输出结果,v2定义前缀字符串，v3定义锁紧的字符串
	data2, err := json.MarshalIndent(m1, "", "    ")
	if err != nil {
		log.Fatal("JSON marshaling failed : %s", err)
	}
	fmt.Printf("%s\n", data2)

	//将JSON解码为GO数据结构,只取得title字段
	var titles []struct{ Title string }
	if err := json.Unmarshal(data1, &titles); err != nil {
		log.Fatal("unmarshling failed: %s", err)
	}
	fmt.Println(titles)
}
```


