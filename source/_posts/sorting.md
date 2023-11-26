---
title: sorting
date: 2023-10-25 10:49:15
tags: Python
---

### sort函数

``` py3
#实例
list.sort(key=lambda x:len(x),reverse=1)
```

sort函数默认为升序排列.key为排序的依据,reverse确认是否反转.这两个参数都可以省略.

这里使用了lambda函数来按照进行list内部元素的长度为依据来排序.sort函数和map函数可以类比,key中的参数x实际上是list中的每一个元素.
