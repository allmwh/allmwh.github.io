---
layout: post
title: python學習筆記-簡化的def:lambda function
description: python學習筆記-簡化的def:lambda function
categories: [Python]
---

看[精通python](https://www.tenlong.com.tw/products/9789863477310)的時候其實沒有很懂lambda，[看了udemy的某課程影片](https://www.udemy.com/course/python-for-data-science-and-machine-learning-bootcamp/)才比較了解一些

<!--more-->

## def函式
要懂lambda一定要先知道一下def，def就是可以自己些功能的東西
```python
def square(num):
    return num**2
```
上面的def是可以把輸入的數變成平方輸出，`square(2)`，輸出結果即為`4`

## lambda:簡化的def function
上面的def可以寫成一行，
```python
def square(num):return num**2
```
把`def`和`return`去掉
```python
square(num):num**2
```
再把`function`名稱和`參數括號`去掉，最前面加上`lambda`，lambda函式
```python
lambda num:num**2
```

## lambda使用情境
你可以幫lambda指定變數，呼叫的方式就和使用`def`的時候一樣
```python
square=lambda num:num**2

square(2)
4
```
但lambda比較常見的狀況是，你只需要這function一次，就不必要寫個`def`出來，若搭配`map()`

`map()`:可以對list的所有值做某個你要的function，並返回一個新的list，`map(function,引入list)`
```python
list_a=[1,2,3,4]
list_b=list(map(lambda num:num**2,list_a))

list_b
[1, 4, 9, 16]
```


## 不推 精通python
後來發現，精通python範例都寫得好複雜，可能我太駑鈍，雖然他榜上有名。蠻推另一本的:[Python 自動化的樂趣](https://www.tenlong.com.tw/products/9789864762729)

## 參考資料
* 精通python p105
* Udemy:[Python for Data Science and Machine Learning Bootcamp](https://www.udemy.com/course/python-for-data-science-and-machine-learning-bootcamp/)