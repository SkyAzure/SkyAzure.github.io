---
title: python str和list排序并删除重复数据
date: 2019-06-30 14:31:26
categories:
- python
tags:
- python
---

# 一、排序函数sort()和sort()

sort() 是Python列表的一个内置的排序方法，`list.sort()` 方法排序时直接修改原列表，返回None；

sort() 是Python内置的一个排序函数，它会从一个**迭代器**返回一个排好序的新列表。

相比于 sort()，sorted() 使用的范围更为广泛，但是如果不需要保留原列表，sort更有效一点。另外，sort() 只是列表的一个方法，只适用于列表，而`sorted()` 函数接受一切迭代器，返回新列表。

这两个方法有以下 2 个共同的参数：

- key 是带一个参数的**函数**，返回一个值用来排序，默认为 None。这个函数只调用一次，所以fast。
- reverse 表示排序结果是否反转
<!-- more -->
  看例子

```python
>>> a = (1,2,4,2,3)        # a 是元组，故不能用sort() 排序
>>> a.sort()
Traceback (most recent call last):
 File "<stdin>", line 1, in <module>
AttributeError: 'tuple' object has no attribute 'sort'
>>> sorted(a)              # sorted() 可以为元组排序，返回一个新有序列表
[1, 2, 2, 3, 4]

>>> a=['1',1,'a',3,7,'n']
>>> sorted(a)
[1, 3, 7, '1', 'a', 'n']
>>> a                      # sorted() 不改变原列表
['1', 1, 'a', 3, 7, 'n']     
>>> print a.sort()
None
>>> a                      # a.sort()直接修改原列表
[1, 3, 7, '1', 'a', 'n']
```

因此如果实际应用过程中需要保留原有列表，使用 sorted() 函数较为适合，否则可以选 择 sort() 函数，因为 sort() 函数不需要复制原有列表，消耗的内存较少，效率也较高。

sorted() 函数功能非常强大，它可以方便地针对不同的数据结构进行排序，从而满足不同需求。例子如下：

- 对字典进行排序

```python
>>> sorted({1: 'D', 2: 'B', 3: 'B', 4: 'E', 5: 'A'})    
# 根据字典键排序[1, 2, 3, 4, 5]
>>> sorted({1: 'D', 2: 'B', 3: 'B', 4: 'E', 5: 'A'}.values())   
# 根据字典值排序['A', 'B', 'B', 'D', 'E']
```

- 对多维列表排序

```python
>>> student_tuples = [('john', 'A', 15),('jane', 'B', 12),('dave', 'B', 10)]
>>> sorted(student_tuples, key = lambda student: student[0]) # 对姓名排序
[('dave', 'B', 10), ('jane', 'B', 12), ('john', 'A', 15)]
>>> sorted(student_tuples, key = lambda student: student[2])  # 年龄排序
[('dave', 'B', 10), ('jane', 'B', 12), ('john', 'A', 15)]
```

- 调用operator模块中的 itemgetter() 可以实现根据多个参数排序

```python
>>> sorted(student_tuples, key = itemgetter(2))  # 根据年龄排序
[('dave', 'B', 10), ('jane', 'B', 12), ('john', 'A', 15)]
>>> sorted(student_tuples, key = itemgetter(1, 2))  # 根据成绩和年龄排序
[('john', 'A', 15), ('dave', 'B', 10), ('jane', 'B', 12)]
>>> sorted(student_tuples, key = itemgetter(1, 2), reverse=True) # 反转排序结果
[('jane', 'B', 12), ('dave', 'B', 10), ('john', 'A', 15)]
```

ps: itemgetter 返回一个函数，实现取元素的功能。比如
	  f = itemgetter(2)，调用 f(r) 返回 r[2];
	  f = itemgetter(2, 5, 3)，调用 f(r) 返回元组 (r[2], r[5], r[3]).

# 二、python集合(set)操作

python的set和其他语言类似, 是一个无序不重复元素集, 基本功能包括关系测试和消除重复元素. 集合对象还支持union(联合), intersection(交), difference(差)和sysmmetric difference(对称差集)等数学运算.

- 下面来点简单的小例子说明

```python
>>> x = set('spam')
>>> y = set(['h','a','m'])
>>> x, y
(set(['a', 'p', 's', 'm']), set(['a', 'h', 'm']))
```

- 再来些小应用。

```python
>>> x & y # 交集
set(['a', 'm'])

>>> x | y # 并集
set(['a', 'p', 's', 'h', 'm'])

>>> x - y # 差集
set(['p', 's'])
```

记得以前个网友提问怎么去除海量列表里重复元素，用hash来解决也行，只不过感觉在性能上不是很高，用set解决还是很不错的，示例如下：

```python
>>> a = [11,22,33,44,11,22]
>>> b = set(a)
>>> b
set([33, 11, 44, 22])
>>> c = [i for i in b]
>>> c
[33, 11, 44, 22]
```

**集合**用于包含一组无序的对象。要创建集合，可使用set()函数并像下面这样提供一系列的项：

```python
s = set([3,5,9,10])      #创建一个数值集合

t = set("Hello")         #创建一个唯一字符的集合
```

与列表和元组不同，集合是无序的，也无法通过数字进行索引。此外，集合中的元素不能重复。例如，如果检查前面代码中t集合的值，结果会是：

 ```python
>>> t
set(['H', 'e', 'l', 'o'])
 ```

注意只出现了一个'l'。

集合支持一系列标准操作，包括并集、交集、差集和对称差集，例如：

 ```python
a = t | s          # t 和 s的并集
b = t & s          # t 和 s的交集
c = t – s          # 求差集（项在t中，但不在s中）
d = t ^ s          # 对称差集（项在t或s中，但不会同时出现在二者中）
 ```

### 基本操作：

```python
t.add('x')            # 添加一项
s.update([10,37,42])  # 在s中添加多项

t.remove('H')
#使用remove()可以删除一项

len(s)
#set 的长度

x in s
#测试 x 是否是 s 的成员

x not in s
#测试 x 是否不是 s 的成员

s.issubset(t)
s <= t
#测试是否 s 中的每一个元素都在 t 中

s.issuperset(t)
s >= t
#测试是否 t 中的每一个元素都在 s 中

s.union(t)
s | t
#返回一个新的 set 包含 s 和 t 中的每一个元素

s.intersection(t)
s & t
#返回一个新的 set 包含 s 和 t 中的公共元素

s.difference(t)
s - t
#返回一个新的 set 包含 s 中有但是 t 中没有的元素

s.symmetric_difference(t)
s ^ t
#返回一个新的 set 包含 s 和 t 中不重复的元素

s.copy()
#返回 set “s”的一个浅复制

hash(s)
#返回 s 的 hash 值

s.update(t)
s |= t
#返回增加了 set “t”中元素后的 set “s”

s.intersection_update(t)
s &= t
#返回只保留含有 set “t”中元素的 set “s”

s.difference_update(t)
s -= t
#返回删除了 set “t”中含有的元素后的 set “s”

s.symmetric_difference_update(t)
s ^= t
#返回含有 set “t”或者 set “s”中有而不是两者都有的元素的 set “s”

s.remove(x)
#从 set “s”中删除元素 x, 如果不存在则引发 KeyError

s.discard(x)
#如果在 set “s”中存在元素 x, 则删除

s.pop()
#删除并且返回 set “s”中的一个不确定的元素, 如果为空则引发 KeyError

s.clear()
#删除 set “s”中的所有元素
```

# 三、str和list排序 删除重复数据

- List排序并删除重复值

```python
>>> a =[1,1,2,3,4,5,4,2,3,1]
>>> b =sorted(set(a)) 
>>> print(b)
[1,2,3,4,5]
```

- List排序不删除重复值

```python
>>> a=[1,1,2,3,4,5,4,2,3,1]
>>> a.sort()
>>> print (a)
[1, 1, 1, 2, 2, 3, 3, 4, 4, 5]
```

- String排序不删除重复值

```python
>>> a="abchabcgesdfaad"
>>> b=list(a)
>>> b.sort()
>>> s="".join(b)
>>>print (s)
aaaabbccddefghs
```

- String排序删除重复值

```python
>>> a="abchabcgesdfaad"
>>> b=list(a)
>>> c=sorted(set(b))
>>> c
['a','b','c','d','e','f','g','h','s']
```

