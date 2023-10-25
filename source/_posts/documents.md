---
title: documents
date: 2023-10-25 08:06:22
tags: Python
---

文件路径:
相对路径 绝对路径

``` bash
//设当前文件的路径为D:\test1\test2\code.py,即当前工作的文件夹为test2

D   ///盘符作为根目录
|   test1
|   |   document1.txt
|   |   document2.txt
|   test2
|   |   code.py
|   |   document3.txt
|   |   test3
|   |   |   document4.txt


D:/test2/document3.txt     ///标准绝对路径
./test3/document4.txt    ///标准相对路径,需要使用\\来转义\.默认读取代码同一层的文件
../test1/document1.txt    ///"../"可以叠加使用来达到更外层的文件夹,但是不能超过根目录




```

windows系统的分隔符默认为\,但是替换成/python也能正常识别.也就是说,在不考虑转义的情况下,正反斜杠的作用是一样的

``` py3
'''文件读写'''
f=open("file_route","open_type")
li=list(f)   ///以行为间隔,将内容存在列表里.注意每个元素最后包含一个换行符
f.readline()
f.seek(offset[,whence])  #0为头，1为本地，2为尾部
f.write("content")
f.writelines(list)
f.close()
```
