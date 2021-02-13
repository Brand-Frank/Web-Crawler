# 《python网络爬虫从入门到精通》——唐松

@[TOC]

## ch1  网络爬虫入门

### 1.1 为什么要学习爬虫
**网站与用户的沟通本质上是数据的交换**
#### 1.1.1  学习网络爬虫带来的好处
传统数据处理的缺点：（1）无法自动化（2）无法实时获取
#### 1.1.2  能爬什么数据
基本都能
#### 1.1.3  应不应该学习爬虫
（1） 简单易学

（2）生产力
### 1.2 网络爬虫是否犯法
看网站的要求和个人用途
#### 1.2.1 Robots协议
**Robots协议（爬虫协议）——“网络爬虫排除标准”（`Robots Exclusion Protocol`）**

网站通过Robots协议告诉搜索引擎哪些网页可以爬取。

eg:
[淘宝Robots协议](https://www.taobao.com/robots.txt) 

![img.png](img/img.png)
````
User-agent: Baiduspider
Allow:      /oshtml
Allow:      /article
Disallow:   /      # 禁止访问除Allow规定页面外的其它所有页面
````
#### 1.2.2 网络爬虫的约束
**限制爬取速度和频次**

（1）在爬取网站的时候需要限制自己的爬虫，遵守Robots协议和约束网络爬虫程序的速度。

（2）在使用数据的时候必须遵守网站的知识产权。

### 1.3 网络爬虫的基本议题
#### 1.3.1 python爬虫的流程
1. 获取网页
2. 解析网页（提取数据）
3. 存储数据
-----------------------------
（1）获取网页就是给一个网址发送请求，该网址会返回整个网页的数据。类似于在浏览器中键入网址并按回车键，然后可以看到网站的整个页面。

（2）解析网页就是从整个网页的数据中提取想要的数据。类似于在浏览器中看到网站的整个页面，但是你想找的是产品的价格，价格就是你想要的数据。

（3）存储数据也很容易理解，就是把数据存储下来。我们可以存储在csv中，也可以存储在数据库中。

-------------------------------------------
#### 1.3.2 三个流程的技术实现

-------------------------------------

1．获取网页

获取网页的基础技术：`request`、`urllib`和`selenium`（模拟浏览器）。

获取网页的进阶技术：多进程多线程抓取、登录抓取、突破IP封禁和服务器抓取。

2．解析网页

解析网页的基础技术：`re`正则表达式、`BeautifulSoup`和`lxml`。

解析网页的进阶技术：解决中文乱码。

3．存储数据

存储数据的基础技术：存入`txt`文件和存入`csv`文件。

存储数据的进阶技术：存入`MySQL`数据库和存入`MongoDB`数据库。

---------------------------------

## ch2  编写第一个网络爬虫

### 2.1 搭建Python平台
#### 2.1.1 Python的安装
安装`Anaconda`
#### 2.1.2 使用pip安装第三方库(package)
第三方库：供用户调用的代码组合，我们可以不用自己写代码而调用库来实现复杂的功能

#### 2.1.3 使用Jupyter Notebook编程

### 2.2 Python使用入门

#### 2.2.1 基本命令
- `print`
````python
print('hello world')
````
- 严格的代码缩进，以Tab键或4个空格键进行缩进
````python
x = 1
if x==1:
    print('Hello world!')
````
- 注释符号`#`

#### 2.2.2 数据类型
python是OOP，不需要再使用之前声明要使用的变量和类别

1. 字符串(`string`)

最常见的**数据类型**

双引号("")或单引号('')之间
````python
string1 = 'Python Web Scrappy'
string2 = 'by Codebuger'
string3 = string1 + " " + string2

print(string3)
````
输出
````shell
Python Web Scrappy
````

2. 数字(`Number`)

整数和浮点数

其它两种复杂的数据类型——长整数和复数

3. 列表(`list`)

如果要把上面的字符串和数字囊括起来，就可以使用列表。

列表的特点是`[]`符号

````python
list1 = ['Python', 'Web', 'Scrappy']
list2 = [1, 2, 3, 4, 5]
list3 = ["a", 2, "c", 4]
````

- 访问列表中的值：`list[i]` (i = 0 ~ n)

- 修改列表中的值：`list[i] = "new value"`

4. 字典(`dictionary`)

- 字典是一种可变容器模型，字典含有字(`key`)和值(`value`)

- 使用字典的过程就像是自己创建一个字典和查字典的过程。

- 每个存储的值都对应着一个键值(`key`)，`key`必须位移，但是值不用。

- 值可以是任何数据类型

- 关键字：`{key1:value1, key2:value2, key3:value3}`


````python
namebook = {"Name":"Alex", "Age":17, "Class":"first"}
print(namebook['Name'])     # 可以把相应的键值放入方括号中，提取(访问)值
print(namebook)     # 也可以直接输出整个字典
````

- 遍历访问字典中的每个值（字典和循环结构）
```python
# 循环提取（访问）整个dictionary里的key和value
# for key, vlaue in namebook.items():
#     print(key, value)
```

#### 2.2.3 条件语句和循环语句

伪代码：

```python
if True:
    print(1)
else:   # False
    print("false")
```
- `if`-`else`

例子：
```python
book = 'python'
if book == 'python':
    print('You are studying python.')
else:
    print('Wrong.')
```

- `if`-`elif`-`else`
例子：
```python
book = 'java'
if book == 'python':
    print('You are learning python.')
elif book == 'java':
    print("You are studying java.")
else:
    print("Wrong.")
```

- `for`循环
```python
cityList = ['Beijing', 'Shanghai', 'Guangzhou']
for eachCity in cityList:
    print(eachCity)
```

#### 2.2.4 函数

- 函数可以重复使用，容易调整顺序。
- 输入输出

```python
def calulus(x):
    y = x + 1
    return y

def fruit_function(fruit1, fruit2):     # 多输入参数
    fruits = fruit1 + ' ' + fruit2
    return fruits

result_calulus = calulus(2)
print(result_calulus)

result_fruit = fruit_function('apple','banana')
print(result_fruit)
```

#### 2.2.5 面向对象编程(`OOP`)

- 面向过程编程 -> 函数式编程 -> 面向对象编程
  - 面向过程编程：按照逻辑，一步一步地写代码。
  - 函数式编程：把某些功能封装到函数中，直接调用。
  - 面向对象编程：把函数进行分类和封装后放入对象。

```python
class Person:   # 创建类
    def _init_(self, name, age):    # _init_方法称为构造类的方法
        self.name = name
        self.age = age
    
    def detail(self):   # 通过self调用被封装的内容
        print(self.name, self.age)

obj1 = Person('codebuger', 18)
obj1.detail()   # Python将obj1传给self参数，相当于 obj1.detail(obj1),此时内部self=obj1
```
##### 使用函数式编程还是面向对象编程？
>如果各个函数间没有共用的数据，选用**函数式编程**
>如果各个函数间有一定的关联性，选用**面向对象编程**

##### 面向对象编程的两大特性

- **封装**
>把内容封装好，再调用封装好的内容
>
>包括（1）封装内容；（2）调用被封装的内容

- - 封装内容
```python
class Person:
  def _init_(self, name, age):
    self.name = name
    self.age = age

obj1 = Person('codebuger', 18)  # 将'codebuger'和18分别封装到obj1及self的name和age属性
```

- - 调用被封装的内容
  
> (1) 通过对象调用
>
> (2) 通过self间接调用

**通过对象直接调用`obj1`对象的`name`和`age`属性**
```python
class Person:
  def _init_(self, name, age):
    self.name = name
    self.age = age

obj1 = Person('codebuger', 18)  # 将'codebuger'和18分别封装到obj1及self的name和age属性

# 调用
print(obj1.name)
print(obj1.age)
```

**通过`self`间接调用**
>python默认将`obj1`传给`self`参数，即`obj1.detail(obj1)`，此时方法内部的`self=obj1`
>即`self.name = 'santos', slef.age = 18`
```python
class Person:
  def _init_(self, name, age):
    self.name = name
    self.age = age

  def detail(self):
    print(self.name)
    print(self.age)

obj1 = Person('codebuger', 18)  # 将'codebuger'和18分别封装到obj1及self的name和age属性
obj1.detail()
```
- - 总结
>面向对象的封装实质是**使用构造方法将内容封装到对象中**，然后通过对象直接或`self`间接获取被封装的内容。

- **继承**
> 以普通的类为基础建立专门的类对象

例如：

猫：喵喵叫、吃、喝、拉、撒

狗：汪汪叫、吃、喝、拉、撒

共同特性是：吃、喝、拉、撒

可以写成继承

>动物：吃、喝、拉、撒
> 猫：喵喵叫（猫继承动物的功能）
> 猫：汪汪叫（狗继承动物的功能）

```python
class Animal:
    def eat(self):
        print('%s在吃东西' %self.name)
    
    def drink(self):
        print('%s在喝水' %self.name)

    def shit(self):
        print('%s在拉东西' %self.name)

    def pee(self):
        print('%s在撒东西' %self.name)

# 猫        
class Cat(Animal):    # 继承Animal的吃喝拉撒属性
  def __init__(self, name):
    self.name = name
  def cry(self):
    print('喵喵叫')

# 狗
class Dog(Animal):
  def __init__(self, name):
    self.name = name
  def cry(self):
    print('汪汪叫')

c1 = Cat('小白家的小黑猫')
c1.eat()
c1.cry()

d1 = Dog('小胖子家的小瘦狗')
d1.eat()
```
对于继承来说，其实就是将多个类共有的方法提取到父类中，子类继承父类中的方法即可，不必一一实现每个方法。

### 2.3 编写第一个简单的爬虫
```shell
http://www.santostang.com/
```
#### 2.3.1 第一步：获取页面
```python
#！ /usr/bin/python
# coding: UTF-8

import requests

link = 'http://www.santostang.com/'
headers = {'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/88.0.4324.150 Safari/537.36 Edg/88.0.705.63'}

# 获取网页，用requests的headers伪装成浏览器访问
r = requests.get(link, headers = headers)
# r是requests的Response回复对象，可以从中获得想要的信息
print(r.text)   # r.text是获取网页内容的代码
```
#### 2.3.2 提取需要的数据

```python
#！ /usr/bin/python
# coding: UTF-8

import requests
from bs4 import BeautifulSoup

link = 'http://www.santostang.com/'

headers = {'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/88.0.4324.150 Safari/537.36 Edg/88.0.705.63'}

r = requests.get(link, headers = headers)

# 使用BeautifulSoup解析这段代码,把html代码转化为soup对象,需要提前安装lxml解析器，pip install lxml
soup = BeautifulSoup(r.text,'lxml')

# 得到第一篇文章的标题，并且打印出来
title = soup.find('h1',class_ = 'post-title').a.text.strip()
print(title)
```
这里需要注意：`soup = BeautifulSoup(r.text,'lxml')`这句需要提前安装`lxml`解析器。

#### 2.3.3 第三步：存储数据
```python
#！ /usr/bin/python
# coding: UTF-8

import requests
from bs4 import BeautifulSoup

link = 'http://www.santostang.com/'
# link = 'http://www.santostang.com/2018/07/15/4-3-%e9%80%9a%e8%bf%87selenium-%e6%a8%a1%e6%8b%9f%e6%b5%8f%e8%a7%88%e5%99%a8%e6%8a%93%e5%8f%96/'

headers = {'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/88.0.4324.150 Safari/537.36 Edg/88.0.705.63'}

# 获取网页，用requests的headers伪装成浏览器访问
r = requests.get(link, headers = headers)
# r是requests的Response回复对象，可以从中获得想要的信息

# 使用BeautifulSoup解析这段代码,需要提前安装lxml解析器，pip install lxml
soup = BeautifulSoup(r.text, 'lxml')

# 得到第一篇文章的标题，并且打印出来
title = soup.find('h1', class_='post-title').a.text.strip()
# title = soup.find('h1', class_='view-title').a.text.strip()

print(r.text)   # r.text是获取网页内容的代码

# 保存到上一目录的子目录img里边
with open('../txt/title.txt', 'a+') as f:
    f.write(title)
    f.close()
```
### 2.4 Python实践：基础巩固
#### 2.4.1 Python基础试题
##### 试题1：
> 请使用Python中的循环打印输出从1到100的所有奇数。

##### 试题2：
> 请将字符串“你好$$$我正在学Python@#@#现在需要&*&*&修改字符串”中的符号变成一个空格，需要输出的格式为：“你好 我正在学Python现在需要 修改字符串”。

##### 试题3：
> 输出9×9乘法口诀表。

##### 试题4：
> 请写出一个函数，当输入函数变量月利润为I时，能返回应发放奖金的总数。例如，输出“利润为100000元时，应发放奖金总数为10000元”。
> 其中，企业发放的奖金根据利润提成。
> 利润（I）低于或等于10万元时，奖金可提10%；
> 利润高于10万元，低于20万元时，低于10万元的部分按10%提成，高于10万元的部分，可提成7.5%；
> 利润在20万元到40万元之间时，高于20万元的部分可提成5%；
> 利润在40万元到60万元之间时，高于40万元的部分可提成3%；
> 利润在60万元到100万元之间时，高于60万元的部分可提成1.5%；
> 利润高于100万元时，超过100万元的部分按1%提成。

#####试题5：
> 用字典的值对字典进行排序，将{1: 2, 3: 4, 4:3, 2:1, 0:0}按照字典的值从大到小进行排序。试题6：请问以下两段代码的输出分别是什么？

##### 试题6：
> 请问以下两段代码的输出分别是什么？
```python
a=1
def fun(a):
    a=2
fun(a)
print(a)
a= []
def fun(a):
    a.append(1)
fun(a)
print(a)
```
输出分别为：1   [1]
从结果发现，在第一段代码中，a为数字`int`，函数改变不了函数以外a的值，输出结果仍然为1（作用域问题）；
而在第二段代码中，a为列表，函数将函数以外的a值改变了。这是因为对象有两种，即可更改（`mutable`）与不可更改（`immutable`）对象。
在Python中，`strings`、`tuples`和`numbers`是不可更改对象，而`list`、`dict`等是可更改对象。
> 在第一段代码中，当一个引用传递给函数时，函数自动复制一份引用。函数里和函数外的引用是不一样的。
> 在第二段代码中，函数内的引用指向的是可变对象列表a，函数内的列表a和函数外的列表a是同一个。
##### 试题7：
> 请问以下两段代码的输出分别是什么？
```python
class Person:
  name="aaa"
p1=Person()
p2=Person()
p1.name="bbb"
print (p1.name)
print (p2.name)
print (Person.name)

class Person:
  name=[]
pl=Person()
p2=Person()
p1.name.append(1)
print (p1.name)
print (p2.name)
print (Person.name)
```
> 第一段代码输出的结果是：bbb aaa aaa
> 第二段代码输出的结果是：[1] [1] [1]
> 这里p1.name="bbb"表示实例调用了类变量，其实就是函数传参的问题。
> p1.name一开始指向类变量name="aaa"，但是在实例的作用域里把类变量的引用改变了，就变成了一个实例变量bbb，self.name不再引用Person的类变量name了，即换成了bbb
> 第二段是因为list、dict等是可更改对象，因此修改一个指向的对象时会把类变量也改变了。


## ch3  静态网页抓取
> 在网站设计中，纯粹`HTML`格式的网页通常被称为**静态网页**，早期的网站一般都是由静态网页制作的。
> 在网络爬虫中，静态网页的数据比较容易获取，因为所有数据都呈现在网页的HTML代码中。
> 相对而言，<u>使用`AJAX`动态加载网页的数据不一定会出现在`HTML`代码中</u>，这就给爬虫增加了困难。
> 本章先从简单的静态网页抓取开始介绍，第4章再介绍动态网页抓取。
> 在静态网页抓取中，有一个强大的`Requests`库能够让你轻易地发送`HTTP`请求。本章介绍如何使用Requests库获取响应内容，最后可以通过定制Requests的一些参数来满足我们的需求。

### 3.1 安装Requests

### 3.2 获取响应内容
```python
import requests
r=requests.get('http://www.santostang.com/')
print("文本编码：", r.encoding)
print("响应状态码：", r.status_code)
print("字符串方式的响应体：", r.text)
print('字节方式的响应体:', r.content)
print('Request中内置的JSON解码器', r.json())
```
输出：
```shell
本编码: UTF-8
响应状态码: 200
字符串方式的响应体: <!DOCTYPE html>...
```
- 说明
（1）`r.encoding`是服务器内容使用的文本编码。 
（2）`r.status_code`用于检测响应的状态码，如果返回200，就表示请求成功了；如果返回的是4xx，就表示客户端错误；返回5xx则表示服务器错误响应。我们可以用r.status_code来检测请求是否正确响应。 
（3）`r.text`是服务器响应的内容，会自动根据响应头部的字符编码进行解码。
（4）`r.content`是字节方式的响应体，会自动解码`gzip`和`deflate`编码的响应数据。
（5）`r.json()`是`Requests`中内置的`JSON解码器`。

### 3.3 定制Requests
有些网页需要对Requests的参数进行设置才能获取需要的数据，这包括**传递URL参数`params`**、**定制请求头`headers`**、**发送POST请求`data`**、**设置超时`timeout`**等。
#### 3.3.1 传递URL参数`params`
- 请求**特定的数据**，我们需要**在URL的查询字符串中加入某些数据**。

如：http://httpbin.org/get?key1=value1

- 在Requests中，你可以直接把这些参数保存在字典中，用params构建至URL中。

例如，传递`key1=value1`和`key2=value2`到http://httpbin.org/get，可以这样编写：
```python
import requests

key_dict = {'key1': 'value1', 'key2': 'value2'}
r = requests.get('http://httpbin.org/get', params=key_dict)
print('URL已经正确编码：', r.url)
print("文本编码：", r.encoding)
print("响应状态码：", r.status_code)
print('字符串方式的响应体：\n', r.text)
```
输出：
```shell
URL已经正确编码: http://httpbin.org/get?key1=value1&key2=value2
文本编码: utf-8
响应状态码: 200
字符串方式的响应体:
 {
  "args": {                 # 使用get请求，此处的args的key1,key2值会被显示出来
    "key1": "value1",
    "key2": "value2"
  }, 
  "headers": {
    "Accept": "*/*", 
    "Accept-Encoding": "gzip, deflate", 
    "Host": "httpbin.org", 
    "User-Agent": "python-requests/2.25.1", 
    "X-Amzn-Trace-Id": "Root=1-6026482c-41a9bd646c22ba00497a8a63"
  }, 
  "origin": "118.212.203.240", 
  "url": "http://httpbin.org/get?key1=value1&key2=value2"
}
```

#### 3.3.2 定制请求头`requests`
> 请求头`Headers`提供了关于请求、响应或其他发送实体的信息。
> 对于爬虫而言，请求头十分重要，如果没有指定请求头或请求的请求头和实际网页不一致，就可能无法返回正确的结果。
> `Requests`并不会基于定制的请求头`Headers`的具体情况改变自己的行为，只是在最后的请求中，所有的请求头信息都会被传递进去
```python
import requests

# key_dict = {'key1': 'value1', 'key2': 'value2'}
# 指定请求头
headers = {'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/88.0.4324.150 Safari/537.36 Edg/88.0.705.63',
           'Host': 'www.santostang.com'}

# r = requests.get('http://httpbin.org/get', params=key_dict)
r = requests.get('http://www.santostang.com/', headers=headers)

print('URL已经正确编码：', r.url)
print("文本编码：", r.encoding)
print("响应状态码：", r.status_code)
print('字符串方式的响应体：\n', r.text)
```
输出：
```shell
URL已经正确编码: http://www.santostang.com/
文本编码: UTF-8
响应状态码: 200
```

#### 3.3.3 发送POST请求`data`
> 除了`GET`请求外，有时还需要**发送一些编码为表单形式的数据**，如在登录的时候请求就为`POST`，因为如果用`GET`请求，**密码就会显示在`URL`中**，这是非常不安全的。
> 如果要实现`POST`请求，只需要简单地传递一个字典给`Requests`中的`data`参数，这个**数据字典就会在发出请求的时候自动编码为表单形式**。
```python
import requests

key_dict = {'key': 'value1', 'key2': 'value2'}

r = requests.post('http://httpbin.org/post', data=key_dict)

print('URL已经正确编码：', r.url)
print("文本编码：", r.encoding)
print("响应状态码：", r.status_code)
print('字符串方式的响应体：\n', r.text)
```
输出：
```shell
URL已经正确编码: http://httpbin.org/post
文本编码: utf-8
响应状态码: 200
字符串方式的响应体:
 {
  "args": {}, # 使用post请求，此处的args的key1,key2值会被隐藏
  "data": "", 
  "files": {}, 
  "form": {   # form变量的值为key_dict输入的值
    "key": "value1", 
    "key2": "value2"
  }, 
  "headers": {
    "Accept": "*/*", 
    "Accept-Encoding": "gzip, deflate", 
    "Content-Length": "22", 
    "Content-Type": "application/x-www-form-urlencoded", 
    "Host": "httpbin.org", 
    "User-Agent": "python-requests/2.25.1", 
    "X-Amzn-Trace-Id": "Root=1-60264cca-63d77c2c1c8bcf8c1042057b"
  }, 
  "json": null, 
  "origin": "118.212.203.240", 
  "url": "http://httpbin.org/post"
}
```

#### 3.3.4 超时`timeout`
> 有时爬虫会遇到服务器长时间不返回，这时爬虫程序就会一直等待，造成爬虫程序没有顺利地执行。
> 因此，可以用`Requests`在`timeout`参数设定的秒数结束之后停止等待响应。
> 意思就是，**如果服务器在`timeout`秒内没有应答，就返回异常**。一般会把这个值设置为20秒。

### 3.4 Requests爬虫实践：TOP250电影数据
> 本章实践项目的目的是获取豆瓣电影TOP250的所有电影的名称，网页地址为：https://movie.douban.com/top250。在此爬虫中，将请求头定制为实际浏览器的请求头。
```python
#！ /usr/bin/python
# coding: UTF-8

import requests
from bs4 import BeautifulSoup

def get_movies():
    # 定制请求头 requests
    headers = {
        'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/88.0.4324.150 Safari/537.36 Edg/88.0.705.63',
        'Host': 'movie.douban.com'}

    movie_list = []
    # info_list = []

    # 1页25部电影，for循环获取250部
    for i in range(0, 10):
        link = 'https://movie.douban.com/top250?start=' + str(i*25)

        # 发送get请求，设置超时 timeout
        r = requests.get(link, headers=headers, timeout=10)

        print('=====================================================================================================================================')
        # 检验状态
        print(str(i+1), ' 页响应状态码:', r.status_code)
        print('URL已经正确编码：', r.url)
        print("文本编码：", r.encoding)
        # print(r.text)   # r.text里的内容为html文本形式

        # 解析网页
        soup = BeautifulSoup(r.text, 'lxml')
        div_list = soup.find_all('div', class_='hd')
        # div_info_list = soup.find_all('div', class_='item')

        # 把电影名保存到movie_list列表中
        for each in div_list:
            movieName = each.a.span.text.strip()
            movie_list.append(movieName)    # 把电影都保存到字典后，由下边的打印语句打印出总的list
            # movie_info = each.a.span.text.strip()
            # info_list.append(movie_info)

    print(movie_list)
    # print(info_list)
    return movie_list

# 调用函数
movies = get_movies()
```

## ch4  动态网页抓取
> 前面爬取的网页均为**静态网页**，这样的网页在浏览器中展示的内容都在`HTML`源代码中。
> 
> 但是，由于主流网站都使用`JavaScript`展现网页内容，和静态网页不同的是，**在使用`JavaScript`时，很多内容并不会出现在`HTML`源代码中**，所以爬取静态网页的技术可能无法正常使用。
> 
> 因此，我们需要用到**动态网页抓取**的两种技术：**<u>通过浏览器审查元素解析真实网页地址</u>**和**<u>使用selenium模拟浏览器的方法</u>**。

### 4.1 动态抓取的实例
- **异步更新技术**——`AJAX`（`Asynchronous Javascript And XML`，**异步JavaScript和XML**）。 

通过在后台与服务器进行少量数据交换就可以使网页实现异步更新。

这意味着**可以在不重新加载整个网页的情况下对网页的某部分进行更新**。

一方面**减少了网页重复内容的下载**，另一方面**节省了流量**，

相对于使用`AJAX`网页而言，传统的网页如果需要更新内容，就必须重载整个网页页面。因此，AJAX使得互联网应用程序更小、更快、更友好。但是，AJAX网页的爬虫过程比较麻烦。

动态网页的例子: http://www.santostang.com/2018/07/04/hello-world/#comments。

网页面下面的**评论**就是用JavaScript加载的，这些评论数据不会出现在网页源代码中。

### 4.2 解析真实地址抓取

[来源](https://blog.csdn.net/weixin_43616817/article/details/109022479)

虽然数据并没有出现在网页源代码中，但是我们还是可以找到数据的真实地址，请求这个真实地址也可以获得想要的数据。这里用到浏览器的“检查”功能。

点击“网络”，刷新，点击左边list?callback开头的链接，真实链接如下：

https://api-zero.livere.com/v1/comments/list?callback=jQuery112409913001985965064_1613139610757&limit=10&repSeq=4272904&requestPath=%2Fv1%2Fcomments%2Flist&consumerSeq=1020&livereSeq=28583&smartloginSeq=5154&code=&_=1613139610759

点击`JS` - `preview`会发现里边由这些评论的内容。
```python
import requests

link = '''https://api-zero.livere.com/v1/comments/list?callback=jQuery112409913001985965064_1613139610757&limit=10
          &repSeq=4272904&requestPath=%2Fv1%2Fcomments%2Flist&consumerSeq=1020&livereSeq=28583&smartloginSeq=5154&code=&_=1613139610759'''

headers = {'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/88.0.4324.150 Safari/537.36 Edg/88.0.705.63'}

r = requests.get(link, headers=headers)

print('页响应状态码:', r.status_code)
print(r.text)
```
### 4.3 通过Selenium模拟浏览器抓取

使用浏览器渲染引擎：直接用浏览器在显示网页时接卸`HTML`、应用`CSS`样式并执行`Javascript`的语句

自动打开浏览器加载网页，并自主浏览各个网页，顺便抓取数据。

Selenium测试直接运行在浏览器中，浏览器自动按照脚本代码做出单击、输入、打开、验证等操作，就像真正的用户在操作一样。


## ch5  解析网页

## ch6  数据存储

## ch7  提升爬虫的速度

## ch8  反爬虫问题

## ch9  解决中文乱码

## ch10 登陆与验证码处理

## ch11 服务器采集

## ch12 分布式爬虫

## ch13 爬虫实践1：维基百科

## ch14 爬虫实践2：知乎Live

## ch15 爬虫实践3：百度地盘api

## ch16 爬虫实践4：餐厅点评