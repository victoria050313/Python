## 封装、继承、多态
把一组数据结构和处理它们的方法组成对象（object），把相同行为的对象归纳为类（class），
通过类的封装（encapsulation）隐藏内部细节，通过继承（inheritance）实现类的特化（specialization）
和泛化（generalization），通过多态（polymorphism）实现基于对象类型的动态分派。<br>
## 类和对象
一切皆为对象，对象都有属性和行为<br>
每个对象都是独一无二的，而且对象一定属于某个类（型）<br>
### 定义类（class）
```python
class Student(object):
    # __init__是一个特殊方法用于在创建对象时进行初始化操作
    # 通过这个方法我们可以为学生对象绑定name和age两个属性
    def __init__(self, name, age = 19):
        self.name = name
        self.age = age

    def study(self, course_name):
        print('%s正在学习%s.' % (self.name, course_name))

    def watch_movie(self):
         print('%s只能观看《熊出没》.' % self.name)
```
### 创建和使用对象
```python
def main():
    # 创建学生对象并指定姓名和年龄
    stu1 = Student('骆昊', 38)
    # 给对象发study消息
    stu1.study('Python程序设计')
    # 给对象发watch_av消息
    stu1.watch_movie()
```
## @property
使用@property包装器来包装getter和setter<br>
@property装饰器将类的方法转换为类的属性<br>
通常，类的方法需要通过调用来执行，例如 person.name()<br>
用类的属性的方式来访问，例如 person.name<br>
定义 getter 方法:只读属性<br>
```python
class Person(object):

    def __init__(self, name, age):
        self._name = name
        self._age = age

    # 访问器 - getter方法
    @property
    def name(self):
        return self._name
```
定义setter方法来使属性可写，并且在写入时可以添加逻辑控制，例如有效性检查。<br>
代码会抛出一个 ValueError 异常，从而防止不合法的值被赋给 age 属性<br>
```python
class Person(object):
    
    def __init__(self, name, age):
        self._name = name
        self._age = age

@property
    def name(self):
        return self._name

@property
    def age(self):
        return self._age

    @age.setter
    def age(self, age):
        if age < 0 or age > 120:
            raise ValueError("年龄必须在0到120之间")
        self._age = age
```
@property 可读属性<br>
@age.setter age可写属性<br>
```python
def main():
    person = Person('王大锤', 12)
    person.age = 13 #
    # person.name = '白元芳'  # AttributeError: can't set attribute
```
## _slots_属性
限定自定义类型的对象只能绑定某些属性，限制动态创建新的属性<br>
可以通过在类中定义__slots__变量来进行限定<br>
需要注意的是__slots__的限定只对当前类的对象生效，对子类并不起任何作用。<br>
使用 __slots__ 可以带来内存和性能上的优化<br>
```python
class Child(Parent):
    __slots__ = ('age',)

    def __init__(self, name, age):
        super().__init__(name)
        self.age = age

# child.address = '北京'  # AttributeError: 'Child' object has no attribute 'address'无法在person示例中添加未声明的属性
```
