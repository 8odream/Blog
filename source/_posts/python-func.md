---
title: python_func
date: 2023-10-25 09:12:34
tags:Python
---
### 自定义函数

``` py3
def function_name(arguments):  #传入的参数可以默认赋值，且可以在传入时不传入已经赋值的内容，或者可以用对应的语句重新赋值对应参数
    */ Code /*  #pass 占位语句，用于打框架时占位提示代码未完成
    return return_value
```

注意,自定义函数内定义的变量为局部变量(变量名可以和主函数的变量重复且不干扰.但是不推荐这样做.可以加globle显式声明使用全局变量),不可被主函数或其他外部函数使用.用完即销.函数内定义的函数同样遵循这一规则.

1.函数可以没有return值.
2.函数可以自我调用递归.
3.函数内可以使用其他自定义函数.

可变长参数:

``` py3
def func1(a,*b):   #b为元组。传入元组时可以不带括号
    pass

def func2(c,**d):   #d为字典
    pass
```

函数参数:

``` py3
    def f(function,a,b):
        '''return function(a)+function(b)'''
        pass
```

### 类名

``` py3
class class_name(value1,value2...):
    fixed_value3_name=fixed_value3  #可以在主程序中被修改。可以直接修改整个类的属性，也可以只修改单个实例（实质是创建了新的同名属性，且之前的属性被屏蔽。可以使用del删除这个属性来恢复对原值的访问）
    fixed_value4_name=fixed_value4
    def __init__(self,value1_name,value2_name...):
        self.value1_name=value1
        self.value2_name=value2

    def function_name1:
        pass
    def function_name2:
        pass
    pass

a=class_name(v1,v2)
print(a.function1())

```
