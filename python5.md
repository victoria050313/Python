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
    def __init__(self, name, age):
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
