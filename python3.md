# 常用数据结构
## 列表
定义列表可以将列表的元素放在[]中，多个元素用,进行分隔<br>
是值的有序序列，每个值都可以通过索引进行标识<br>
可以使用for循环对列表元素进行遍历<br>
可以使用[]或[:]运算符取出列表中的元素<br>
定义列表、遍历列表、列表的下标运算
```python
s1 = [1,2,3,4,5]
s2 = ['hello'] * 3

#生成式创建列表
# 用这种语法创建列表之后元素已经准备就绪所以需要耗费较多的内存空间
f = [x for x in range(1, 10)]
# 通过生成器可以获取到数据但它不占用额外的空间存储数据
# 每次需要数据的时候就通过内部的运算得到数据(需要花费额外的时间)
f = (x for x in range(1, 1000))


# 计算列表长度(元素个数)
len(s2) #3

#下标运算
s1[0] #1

# 遍历元素
print(s1)
# 通过循环用下标遍历列表元素
for index in range(len(s1)):
    print(s1[index])
for element in s1:
    print(s1)

#添加元素
s1.append(6)
s1.insert(6,7)

# 合并两个列表
s1.extend([1000, 2000])
s1 += [1000, 2000]

# 先通过成员运算判断元素是否在列表中，如果存在就删除该元素
if 3 in list1:
	s1.remove(3)
# 从指定的位置删除元素
s1.pop(0)
# 清空列表元素
s1.clear()

#列表切片
s1[1:4] #2,3,4

#列表排序
sorted(s1)
```
## 元组
元组的元素不能修改<br>
元组在创建时间和占用的空间上面都优于列表<br>
```python
# 定义元组
t = ('骆昊', 38, True, '四川成都')

#下标运算
t[0]

#遍历元组
for member in t:
    print(member)

#不能修改元素
# t[0] = '王大锤'  # TypeError

# 将元组转换成列表
person = list(t)

#将列表转换成元组
t = tuple(person)
```
## 集合（set）
不允许有重复元素，而且可以进行交集、并集、差集等运算<br>
创建集合
```python
set1 = {1,2,3}
set2 = set(range(1,4))
set3 = set((1,2,3))
set4 = {num for num in range(1,10) if num % 2 == 0 }
```
添加元素和删除元素
```python
#添加
set1.add(4) 
set1.update([11,12]) #添加多个元素，参数是一个可迭代对象，比如列表、集合、元组等
#删除
set1.remove(4) #如果元素不存在，则会发生错误
set.discard(3) #如果元素不存在，不会发生错误
set1.pop() #随机删除一个,返回删除的元素
#清空
set1.clear
```
集合的交集、并集、差集、对称差运算
```python
set1 & set2
set1 | set2
set1 - set2
set1 ^ set2
```
## 字典
每个元素都是由一个键和一个值组成的“键值对”.键：值
```python
# 创建字典的字面量语法
scores = {'骆昊': 95, '白元芳': 78, '狄仁杰': 82}
# 创建字典的构造器语法
items1 = dict(one=1, two=2, three=3, four=4)
# 通过zip函数将两个序列压成字典
items2 = dict(zip(['a', 'b', 'c'], '123'))
# 创建字典的推导式语法
items3 = {num: num ** 2 for num in range(1, 10)}

# 通过键可以获取字典中对应的值
print(scores['骆昊'])
# 对字典中所有键值对进行遍历
for key in scores:
    print(f'{key}: {scores[key]}')

# 更新字典中的元素
scores['白元芳'] = 65
scores.update(冷面=67, 方启鹤=85)
if '武则天' in scores:
    print(scores['武则天'])

# get方法也是通过键获取对应的值但是可以设置默认值
print(scores.get('武则天', 60))

# 删除字典中的元素
scores.pop('骆昊', 100)
# 清空字典
scores.clear()
```
