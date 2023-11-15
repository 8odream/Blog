---
title: py-GUI
date: 2023-11-15 08:12:35
tags: Python
---
GUI是用户图形界面(Graphic User Interface)的简称.在Python中,最为简单且适合初学者的模块就是tkinter.
以下给出一个基本的模板:

``` py3
import tkinter from tkinter

windows=Tk()
```

以下以"win"作为实例名,介绍一下各个参数的作用.

控件的类型:
Lable Message Entry Text
Button Radiobutton Checkbutton
Listbox Combobox
Scale Scrollbar
Menu
Frame
Toplevel

下面的代码示例中,每一段不和下一段有关联,减少变量的混淆,提高易读性

``` py3
from tkinter import *
win.winfo_screenwidth() #获取整个屏幕的宽度。高度同理。返回值为px的数量
win.geometry("%dx%d+%d+%d"%(width,height,to_screen_left,to_screen_right))  #调整窗口的大小（单位为px）

lable1=tk.Lable(win,text="content",bg="white",fg="blue")

button1=tk.Button(win,text="content",command=func) #绑定点击后触发的函数。不允许带括号传递参数

var1=StringVar() #可变变量
entry1=Entry(win,textvariable=var1,show="*") #输入的字符可以转化为*，从而保护隐私.可以用var1这个可变变量来获取、更改输入框的内容
user_input=entrt1.get()  #获取用户输入方法1。注意使用这种方法读取输入数据时不能直接在语句末尾添加布局，需要另起一行设置布局，否则读取不成功
entry1.delect(start,end) #删除指定范围的文本
user_input=var1.get()  #获取用户输入方法2
var1.set("再次输入")  #更改输入框的内容

#单选控件需要绑定同一个var变量，否则每个Radiobutton自成一组
var2=IntVar()
var2.set(1)  #预选中第一个对象
Radiobutton(win,text="text1",variable=var2,value=0).pack()  #选中后，var2的值变为对应的value值。该实例允许增加command对象
Radiobutton(win,text="text2",variable=var2,value=1).pack()
Radiobutton(win,text="text2",variable=var2,value=2).pack()

#多选控件需分别绑定多个var变量
ch1=Checkbutton(win,text="text1",variable=var1,onvalue=onvalue1,offvalue=offvalue1).pack()
ch2=Checkbutton(win,text="text1",variable=var2,onvalue=onvalue2,offvalue=offvalue2).pack()
pass

#列表框，可供用户选择。能后期插入选项。
lb1=Listbox(win,selectmode=MULTIPLE) #selectmode默认单选，可以这样设置为多选
for i in List1:
    lb1.insert(insert_position,stuff)
lb1.pack()
lb1.curselection() #返回选中的项目编号，类型为元组

#框架。注意自行设定width和height等参数
frame1=Frame(win).pack()#relief为边框样式，可选的有：FLAT、SUNKEN、RAISED、GROOVE、RIDGE。默认为 FLAT

#组合框
from tkinter import ttk
var1=IntVar()
combobox1=ttk.Combobox(win,textvariable=var1,values=List1)
user=combobox1.get() #获取内容
id=combobox1.current() #获取内容的编号


```

修改控件的内容:
注意修改text内容只能使用textvariable来实现.详见上面的entry实例代码.text内容不可更改

``` py3
lable1.config(Control=Stuff)
button1[Control]=Stuff
```

可变变量:IntVar()  StringVar()  DoubleVar
需要用对应的模块导入.例如from tkinter import IntVar
var.get()用以获取变量的值

### 布局

grid 会自动根据所有组件的大小来计算其网格的大小。

``` py3
lable1.grid(colomn=2,row=1,colomnspan=2)
```

pack是自上到下的简单布局

### 方法

tkinter after方法:相当于不会阻塞进程的sleep.

``` py3
win.after(num,func()) #在num毫秒后执行func函数
```

注意,在实际使用时,往往在一个类中定义一个tk实例.

下面是我自己写的一个小计算器😊

``` py3
from tkinter import *
from tkinter import StringVar,DoubleVar, ttk


def calculate():
    way=selectbox.current()
    num1=en1.get()
    num2=en2.get()
    var2.set(eval(num1+method[way][1]+num2))

win=Tk()
var1=StringVar()
var2=DoubleVar()
var2.set(0)
method=["加+","减-","乘*","除/"]
selectbox=ttk.Combobox(win,textvariable=var1,values=method)
selectbox.grid(column=2,row=1,columnspan=2)

en1=Entry(win)
en1.grid(column=2,row=2)
en2=Entry(win)
en2.grid(column=3,row=2)

button=Button(win,text="计算",command=calculate).grid(column=2,row=3)

lable1=Label(win,textvariable=var2).grid(column=2,row=4,columnspan=2)


win.title("Calculaetr!")
sw=win.winfo_screenwidth()
sh=win.winfo_screenheight()
win.geometry("%dx%d+%d+%d"%(300,200,sw/2-150,sh/2-100))

win.mainloop()
```
