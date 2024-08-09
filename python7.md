# Numpy
用于快速处理任意维度的数组  
支持常见的数组和矩阵操作
## 创建数组对象
使用ndarray可以处理一维、二维和多维数组。优于list
方法一：使用`array`函数，通过`list`创建数组对象

代码：

```Python
array1 = np.array([1, 2, 3, 4, 5])
array1
```

输出：

```
array([1, 2, 3, 4, 5])
```

方法二：使用`arange`函数，指定取值范围和跨度创建数组对象

代码：

```Python
array3 = np.arange(0, 20, 2)
array3
```

输出：

```
array([ 0,  2,  4,  6,  8, 10, 12, 14, 16, 18])
```

方法三：使用`linspace`函数，用指定范围和元素个数创建数组对象，生成等差数列

代码：

```Python
array4 = np.linspace(-1, 1, 11)
array4
```

输出：

```
array([-1. , -0.8, -0.6, -0.4, -0.2,  0. ,  0.2,  0.4,  0.6,  0.8,  1. ])
```

方法四：使用`logspace`函数，生成等比数列

代码：

```python
array5 = np.logspace(1, 10, num=10, base=2)
array5
```

> **注意**：等比数列的起始值是$2^1$，等比数列的终止值是$2^{10}$，`num`是元素的个数，`base`就是底数。

方法五：通过`fromstring`函数从字符串提取数据创建数组对象

```Python
np.fromstring(s, dtype=float, count=-1, sep='')
```
>s：输入的字符串，其中包含要转换为数组的元素。  'q,w,e'
dtype：输出数组的数据类型。  
count：需要读取的元素数量，默认为-1，表示读取字符串中的所有元素。  
sep：字符串中元素之间的分隔符，默认为空字符串，表示元素之间没有分隔符。  

方法六：通过`fromiter`函数从生成器（迭代器）中获取数据创建数组对象

代码：

```Python
def fib(how_many):
    a, b = 0, 1
    for _ in range(how_many):
        a, b = b, a + b
        yield a


gen = fib(20)
array7 = np.fromiter(gen, dtype='i8')
array7
```

输出：

```
array([   1,    1,    2,    3,    5,    8,   13,   21,   34,   55,   89,
        144,  233,  377,  610,  987, 1597, 2584, 4181, 6765])
```

方法七：使用`numpy.random`模块的函数生成随机数创建数组对象

产生10个[0, 1)范围的随机小数，代码：

```Python
array8 = np.random.rand(10)
```

产生10个[1, 100)范围的随机整数，代码：

```Python
array9 = np.random.randint(1, 100, 10)
```

产生20个的正态分布随机数，代码：

```Python
array10 = np.random.normal(50, 10, 20)
array10
```

产生[0, 1)范围的随机小数构成的3行4列的二维数组，代码：

```Python
array11 = np.random.rand(3, 4)
array11
```

输出：

```
array([[0.54017809, 0.46797771, 0.78291445, 0.79501326],
       [0.93973783, 0.21434806, 0.03592874, 0.88838892],
       [0.84130479, 0.3566601 , 0.99935473, 0.26353598]])
```

产生[1, 100)范围的随机整数构成的三维数组，代码：

```Python
array12 = np.random.randint(1, 100, (3, 4, 5))
array12
```

输出：

```
array([[[94, 26, 49, 24, 43],
        [27, 27, 33, 98, 33],
        [13, 73,  6,  1, 77],
        [54, 32, 51, 86, 59]],

       [[62, 75, 62, 29, 87],
        [90, 26,  6, 79, 41],
        [31, 15, 32, 56, 64],
        [37, 84, 61, 71, 71]],

       [[45, 24, 78, 77, 41],
        [75, 37,  4, 74, 93],
        [ 1, 36, 36, 60, 43],
        [23, 84, 44, 89, 79]]])
```

方法八：创建全0、全1或指定元素的数组

使用`zeros`函数，代码：

```Python
array13 = np.zeros((3, 4))
array13
```

使用`ones`函数，代码：

```Python
array14 = np.ones((3, 4))
array14
```

使用`full`函数，代码：

```Python
array15 = np.full((3, 4), 10)
array15
```

输出：

```
array([[10, 10, 10, 10],
       [10, 10, 10, 10],
       [10, 10, 10, 10]])
```

方法九：使用`eye`函数创建单位矩阵

代码：

```Python
np.eye(4)
```

输出：

```
array([[1., 0., 0., 0.],
       [0., 1., 0., 0.],
       [0., 0., 1., 0.],
       [0., 0., 0., 1.]])
```

方法十：读取图片获得对应的三维数组

代码：

```Python
array16 = plt.imread('res/guido.jpg')
array16
```

## 数组对象的属性

`size`属性：获取数组元素个数。

`shape`属性：获取数组的形状。

`dtype`属性：获取数组元素的数据类型。`

`ndim`属性：获取数组的维度。

`itemsize`属性：获取数组单个元素占用内存空间的字节数。

`nbytes`属性：获取数组所有元素占用内存空间的字节数。

## 数组的索引运算
>使用普通索引和切片索引进行常规操作，如访问单个元素或子数组。<br>
使用花式索引非连续元素的访问,进行复杂的元素选择，如随机采样或选择特定模式的元素。<br>
使用布尔索引基于条件筛选元素,进行数据过滤和条件选择<br>
### 普通索引
```python
#array是三维数组
array17[0] #输出二维数组，eg.  array([[1,2,3],[4,5,6]])
array17[0][1] #或 array17[0, 1]
```
### 切片索引
形如[开始索引:结束索引:跨度]的语法
<img src="png/ndarray-slice.png" style="zoom:60%;">
### 花式索引
```python
#一维
arr = np.array([10, 20, 30, 40, 50])
arr2 = arr[[2, 0]] #[30, 10]

#多维
arr_2d = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
row_indices = [0, 1, 2]
col_indices = [2, 1, 0]
selected_elements = arr_2d[row_indices, col_indices] #[3 5 7]
```

### 布尔索引
```python
arr_2d = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
bool_indices = arr_2d > 4
selected_elements = arr_2d[bool_indices]
print(selected_elements)  # 输出: [5 6 7 8 9]
```
## 数组对象的方法
计算总和、均值、中位数
```python
array1.sum()
np.sum(array1)

array1.mean()
np.mean(array1)

array1.median()
np.median(array1)

np.quantile(array1, 0.5) #计算50%分位数
q1, q3 = np.quantile(array1, [0.25, 0.75])
```
同理，极值、方差、标准差
```python
array1.var()
array1.std()
```
## 数组的运算
### 数组跟标量的运算
NumPy 的数组可以跟一个数值进行加、减、乘、除、求模、求幂等运算，对应的运算会作用到数组的每一个元素上
```python
array1 + 10
array1 * 10
array1 > 5
array1 % 2 == 0
```
### 数组跟数组的运算
两个数组的形状（shape属性）要相同
```
array1 + array2
array1 * array2
```
### 通用函数

| 函数                               | 说明                                                         |
| ---------------------------------- | ------------------------------------------------------------ |
| `add(x, y)` / `substract(x, y)`    | 加法函数 / 减法函数                                          |
| `multiply(x, y)` / `divide(x, y)`  | 乘法函数 / 除法函数                                          |
| `floor_divide(x, y)` / `mod(x, y)` | 整除函数 / 求模函数                                          |
| `allclose(x, y)`                   | 检查数组`x`和`y`元素是否几乎相等                             |
| `power(x, y)`                      | 数组$x$的元素$x_i$和数组$y$的元素$y_i$，计算$x_i^{y_i}$      |
| `maximum(x, y)` / `fmax(x, y)`     | 两两比较元素获取最大值 / 获取最大值（忽略NaN）               |
| `minimum(x, y)` / `fmin(x, y)`     | 两两比较元素获取最小值 / 获取最小值（忽略NaN）               |
| `dot(x, y)`                        | 点积运算（数量积，通常记为$\cdot$，用于欧几里得空间（Euclidean space）） |
| `inner(x, y)`                      | 内积运算（内积的含义要高于点积，点积相当于是内积在欧几里得空间$\mathbb{R}^n$的特例，而内积可以推广到赋范向量空间，只要它满足平行四边形法则即可） |
| `cross(x, y) `                     | 叉积运算（向量积，通常记为$\times$，运算结果是一个向量）     |
| `outer(x, y)`                      | 外积运算（张量积，通常记为$\bigotimes$，运算结果通常是一个矩阵） |
| `intersect1d(x, y)`                | 计算`x`和`y`的交集，返回这些元素构成的有序数组               |
| `union1d(x, y)`                    | 计算`x`和`y`的并集，返回这些元素构成的有序数组               |
| `in1d(x, y)`                       | 返回由判断`x` 的元素是否在`y`中得到的布尔值构成的数组        |
| `setdiff1d(x, y)`                  | 计算`x`和`y`的差集，返回这些元素构成的数组                   |
| `setxor1d(x, y)`                   | 计算`x`和`y`的对称差，返回这些元素构成的数组                 |

