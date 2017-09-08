##python基础知识

### 知识点
因为感觉学的编程语言一多,很多的规则都会搞混,所以就整理一下一些使用方法(看廖雪峰官网的总结版本3)
注释: #
大小写敏感
r''表示''里的字符不转义
以:结束时,锁紧的语句视为代码块
空值:None
除法:/ 得到浮点数
地板除:// 得到整数
取余:%
输入:name = input('name:');
输出:print();
转换成整数:int();input()输入的是str,与数据进行比较时要转换类型

### 字符串
字符转ASCII:ord('A');
ASCII转字符:chr(65);
b'ABC':bytes类型,每个字符只占一个字节;
'ABC'.encode('ascii'):b'ABC' 编码为指定bytes;

### 数组
#### list
内置一种数据类型:列表 list
classmates = ['0','1','2'];
长度:len();
转换成list:list(range(5));#[0,1,2,3,4]
索引访问:classmates[0];
直接获取最后一个元素:classmates[-1];
倒数第二个:classmates[-2];
追加元素到末尾:classmates.append('3');
插入到指定位置:classmates.insert(1,'1');
删除末尾元素:classmates.pop();
删除指定位置元素:classmates.pop(i);
排序:sort()
#### tuple
另一种有序列表叫元祖:tuple,一旦初始化就不能修改,没有append(),insert(),pop()方法,也不能赋值.
定义:t = (1,2);
**注意:**t = (1),表示1这个数!只有一个元素时定义:t = (1,);

### "对象"
#### dict
Python内置了字典：dict的支持，dict全称dictionary，在其他语言中也称为map，使用键-值（key-value）存储，具有极快的查找速度。
有点类似js中的对象
d = {'a':65,'b':66}
判断key是否存在:'a' in d => True ; d.get('a')
删除: d.pop(key)
**请务必注意**，dict内部存放的顺序和key放入的顺序是没有关系的。
和list比较，dict有以下几个特点：
1.查找和插入的速度极快，不会随着key的增加而变慢；
2.需要占用大量的内存，内存浪费多。
而list相反：
1.查找和插入的时间随着元素的增加而增加；
2.占用空间小，浪费内存很少。
所以，dict是用空间来换取时间的一种方法。
dict可以用在需要高速查找的很多地方。
这个通过key计算位置的算法称为哈希算法（Hash）。
#### set
一组key的集合,但不存储value,set中没有重复的key
要创建一个set，需要提供一个list作为输入集合：
s = set([1,2,2,3,3]) => {1,2,3}
添加元素:s.add(key)
删除元素:s.remove(key)
交集: s1 & s2
并集: s1 | s2

### 函数
[官方文档](!http://docs.python.org/3/library/functions.html)
#### 定义函数
```python
def my_abs(x):
  if not isinstance(x, (int, float)):#对参数类型做检查，只允许整数和浮点数类型的参数。
    raise TypeError('bad operand type')
  if x < 0:
    return -x
  else:
    return x
```
如果将函数my_abs()保存在absfun.py文件中,用from absfun import my_abs来导入my_abs()函数
#### 返回多个值
```python
import math #import math语句表示导入math包，并允许后续代码引用math包里的sin、cos等函数。
def move(x, y, step, angle=0):
    nx = x + step * math.cos(angle)
    ny = y - step * math.sin(angle)
    return nx, ny
```
其实返回的是一个tuple,仍然是单一值
```python
>>> r = move(100, 100, 60, math.pi / 6)
>>> print(r)
(151.96152422706632, 70.0)
```
#### 参数组合
必选参数 默认参数 可变参数 关键字参数 命名关键字参数
[函数的参数](!https://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000/001431752945034eb82ac80a3e64b9bb4929b16eeed1eb9000)

#### 尾递归
递归调用过深会导致栈溢出,可以通过尾递归来避免
```python
#函数返回时调用自身本身,且return语句不能包含表达式
def fact_iter(num, product):
    if num == 1:
        return product
    return fact_iter(num - 1, num * product) #仅返回递归函数本身，num - 1和num * product在函数调用前就会被计算，不影响函数调用。
```

### 语句
#### 条件判断
可以用elif做到更细致的判断
```python
age = 20
if age >= 18:
  print('age is',age)
elif age >= 6:
  print('teenager')
else:
  print('kid')
```
#### 循环
##### for循环
```python
names = ['a','b','c']
for name in names:
  print(name)
```
range():生成一个整数序列
```python
sum = 0
for x in range(101): #生成0-100的整数序列
  sum = sum + x
print(sum)
```
##### while循环
```python
sum = 0
n = 99
while n > 0:
  sum = sum + n 
  n = n - 2
print(sum)
```