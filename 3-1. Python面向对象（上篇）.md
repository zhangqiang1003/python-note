> **概述：**
- **面向过程**：根据业务逻辑依次编写代码
- **函数式**：将具备某功能的代码进行函数封装，后面通过方法名调用即可，避免写重复的逻辑代码
- **面向对象**：定义一个类，通过**类的属性和方法**描述这类事物具有的特性和行为，更加有利于开发


### 1. 面向对象的概念
- 类：生活中一类事物的总称
- 对象：对某类事物的举例化
```python
'''
举例：Human 类 ---->  p1 = Human('张三', 18)
有一个Human类，p1是Human类实例化的一个对象（一个具体人，叫 张三，18岁）

概念理解：私有属性，它也是属于公有属性，只不过不能在类的外面被实例化对象p1访问到

注意：这里的公有属性和独有属性是相对的，他不是和私有属性是相对的，因为私有属性也是公有属性
'''

# 定义一个Human类
class Human(object):
    def __init__(self, name, age, id):
        # 创建成员变量
        self.name = name # 公有属性
        self.age = age # 公有属性
        self.__id = id # 公有属性，私有属性

        
# 创建一个对象
p1 = Human('张三', 18, 20190309)
p1.like = '打篮球' # 独有属性
print(p1.name) # 张三
print(p1.age) # 18
```
**公有属性（变量）**：在类中声明定义好的属性（变量），每个对象都具有的属性

**独有属性（变量）**：在对象创建后，定义的属性（变量），只有这个对象才具有的属性

#### 1. **`__init__()方法`**
>在创建对象后悔自动执行的方法，为魔法方法
- 用途：用来创建类的成员变量
 
#### 2. **`__str__()方法`**
当调用print方法直接打印对象的时候，会自动调用对象的__str__()方法，打印该方法的返回值
```python
'''
该方法是一个魔法方法
当实例化一个对象p1后，print(p1)时，会自动调用该方法，并返回结果
返回的结果有两种可能：
如果在类Human中，没有定义__str__方法，则会返回p1对象的内存地址：<__main__.Human object at 0x000001DE9614B240>
如果在类Human中，定义了__str__方法，则会返回该方法返回的值，举例如下：
'''
# 没有定义__str__()方法
class Human(object):
    pass

p1 = Human()
print(p1) # <__main__.Human object at 0x000001DE9614B240>

# 定义了__str__()方法
class Human(object):
    def __str__(self):
        return '这儿可以返回任意指定的值'

p1 = Human()
print(p1) # 这儿可以返回任意指定的值
```
#### 3. 成员方法和成员变量的使用
- 通过`self`直接调用，哪个对象调用成员方法，`self`就表示该对象
```python
'''
验证self 就是 那个实例化的对象
'''
class Human(object):
    def check_obj_self(self, obj):
        if self is obj:
            return 'self 就是 这个实例化的对象p1'
        else:
            return 'self 不是 这个实例化的对象p1'

p1 = Human()
rr = p1.check_obj_self(p1)
print(rr) # self 就是 这个实例化的对象p1
```
- 成员方法和成员变量的使用
```python
# 定义类
class Student:
    def __init__(self):
        # 定义成员变量
        self.name = ""
        self.age = 18
	# 定义成员方法
    def study(self):
        print("%s 在学习" % self.name)

    def sleep(self):
        print("%s 正学习呢，睡着了" % self.name)

    def say(self):
        print("%s 说 ，老子今年%d岁了" % (self.name, self.age))

    def __str__(self):
        return "这是一个学生对象，姓名%s 年龄%d" % (self.name, self.age)

# 创建对象1
stu1 = Student()
# 对象1修改成员变量name
stu1.name = "张三"
stu1.age = 28
# 创建对象2
stu2 = Student()
stu2.name = "李斯"
# 对象2修改成员变量age
stu2.age = 19

# 对象1调用成员方法
stu1.study() # 张三 在学习
stu2.study() # 李斯 在学习

stu1.sleep() # 张三 正学习呢，睡着了
stu2.say() # 李斯 说 ，老子今年19岁了

# 直接打印对象，会自动调用对象的__str__方法，打印该方法的返回值
print(stu1) # 这是一个学生对象，姓名张三 年龄28
print(stu2) # 这是一个学生对象，姓名李斯 年龄19
```
