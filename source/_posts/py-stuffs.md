---
title: py_stuffs
date: 2023-10-25 11:21:29
tags: Python
---

* 可迭代:变量是可以迭代的,而整形数字等常量是不可迭代的.许多函数都需要接受可迭代的变量作为参数

字典性质

``` py3
d=dict(k1='v1', k2='v2', k3='v3') #这种格式相当于用花括号创建字典，但键不需要引号，比如 d={‘k1’: ‘v1’, ‘k2’: ‘v2’, ‘k3’: ‘v3’}，
d=dict([()])

'k1' in d # True
'v1' in d # False。表明in方法检查的是键而不是值

'v1' in d.values() #True。注意，d.values()返回的是dict_values对象，可以用list()转换成列表
('k1', 'v1') in d.items() #True。注意，d.values()返回的是dict_items对象，可以用list()转换成列表

d.get('key') #None
#d['key'] 报错
d.get('key','value') #若d['key']存在，则返回d['key']的值，否则返回默认值'value'

d.setdefault('k4','v4') #'v4'。若键不存在，则添加对应的键和值，并返回新值。第二个值默认为None，可以省略
d.setdefault('k1','v4') #'v1'。若键存在，则返回对应的值，且不执行别的操作

d.pop('k4','value') #'v4'。若键存在，则删除该键，并返回先前对应的键值。此时第二个数值可以省略
d.pop('k4','value') #'value'。若键不存在，则返回规定的默认的键值。姿势第二个数值不可忽略，否则报错

d.clear()
d #{}

```

集合

``` py3
s={1,2,3} #s={}创建的是字典而不是集合。
s=set('123') #只能接受可迭代变量。可以为空，创建空字典
```

zip(list1,list2)

``` bash
a=[1,2,3],b=[4,5,6]
c=list(zip(a,b))
#c=[(1,4),(2,5),(3,6)]
```

isinstance(value,type)

``` bash
>>>isinstance(1.1+0j,float) 
False
```

eval(str)

``` bash
>>>eval("1+2*3/4")
2.5
```

exec(str)

``` bash
>>>exec("print("hello,world")")
hello,world
```

all() 与逻辑的函数版本

any() 或逻辑的函数版本

id(var)

``` bash
>>>pi=3.14
>>>id(pi)
1458273010640
>>>k=3.14
>>>id(k)
1458273025264
```

模块:

* 模块中定义的常量可以被修改
