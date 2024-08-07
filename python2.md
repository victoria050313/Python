#
## sys
sys模块是与python解释器交互的一个接口<br>
### 处理命令行参数
argv 列表包含了传递给脚本的所有参数<br>
列表的第一个元素为脚本自身的名称<br>
```python
sys.argv[0] #表示程序自身
sys.argv[1] #表示程序的第一个参数
sys.argv[2] #表示程序的第二个参数
```
### 输入
```python
# sys.stdin.readline() 相当于input，区别在于input不会读入'\n'
aa = sys.stdin.readline()		# 输入数据多一个'\n'
bb = input('请输入：')
 
print(len(aa))		
print(len(bb))
 
#结果
i love DL
请输入：i love DL
10
9
```
### 输出
```python
sys.stdout.write('hello' + '\n')
print('hello')  #等价
```

## 变量类型
```python 
int() 
float()
str() #字符串型
chr() #将整数转换成该编码对应的字符串
ord() #将字符串（一个字符）转换成对应的编码（整数）

type() #检查类型
```
## 分支结构
### if
```python
if x > 1:
    y = 3 * x - 5
elif x >= -1:
    y = x + 2
else:
    y = 5 * x + 3
```
### for-in
```python
for x in range(101):
    sum += x

break #终止本次循环
continue #终止循环
range(101) #0~100
range(1,101) #1~100
range(1,101,2) #步长
range(100,0,-2) 
```
### while
```python
while True:
while i<=2:
```
## 函数与模块
函数的参数都设定了默认值
```python
def fac(num):
    """求阶乘"""
    result = 1
    for n in range(1, num + 1):
        result *= n
    return result
```
函数有可变参数，即不确定参数个数
```python
def add(*args):
    total = 0
    for val in args:
        total += val
    return total
```
用模块管理函数
```python
import module1 as m1
import module2 as m2

m1.foo()
m2.foo()
```
```python
from module1 import foo
from module2 import foo

foo()
```
这样的话除非直接运行该模块，if条件下的这些代码是不会执行的<br>
import module1 导入module1时模块不会执行
```python
def foo():

if __name__ == '__main__':
    print('call foo()')
    foo()
```
变量的作用域：按照“局部作用域”、“嵌套作用域”、“全局作用域”和“内置作用域”的顺序进行搜索<br>
global a 标识全局变量
## 字符串
```python
s1 = 'abc456'
s2 = "789"

s3 = s1 * 3 #字符串的重复
s4 = s1 + s2 #字符串的拼接
# 使用in和not in来判断一个字符串是否包含另外一个字符串

s5 = s1[2:4] #切片 c45
s6 = s1[2:]  #c456
s7 = s1[::] #ac5
s8 = s1[::-1] #654cba

len(s1) #长度
s1.capitalize() #首字母大写
s1.title() #每个单词首字母大写
s1.upper() #大写
```
格式化输出
```python
print('%d * %d = %d' % (a, b, a * b))

print('{0} * {1} = {2}'.format(a, b, a * b))
