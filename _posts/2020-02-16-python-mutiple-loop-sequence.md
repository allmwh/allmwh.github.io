---
layout: post
title: python學習筆記-在for迴圈中迭代多個序列
description: python學習筆記-在for迴圈中迭代多個序列
categories: [python]
---
以前沒有認真看過一遍[精通pytohn](https://www.tenlong.com.tw/products/9789863477310?list_name=srh)時，就遇到這個問題，稍微做個紀錄

<!--more-->
## 問題
> 有兩個串列想同時在迴圈中迭代

果然要讀一下書，不然會一直要google...，方法還蠻簡單的，只要使用`zip()`函式就可以了

## zip()函式介紹

假如我有這兩個list
```python
animal=['cat','lion','elephant','dog','zebra']
color=['black','yellow','orange','pink','purple','red']
```
就可以使用`zip()`同時迭代這兩個list

```python
for x,y in zip(animal,color):
    print(x+':'+y)
```
輸出為
```python
cat:black
lion:yellow
elephant:orange
dog:pink
zebra:purple
```
## 每個序列長度不相同時

可以發現我`color`序列中的`red`值，沒有被迭代出來，因為`color`比`animal`多一個值，`zip()`函式只會取到所有序列最短的


這樣就完成多個序列的迭代，當然不只`list[]`，`tuple()`，`dict{}`，`set{}`都可以這樣做

## 參考資料
* 精通python p86