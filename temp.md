# 和JS的异同

## 布尔值
py中真假的字面量首字母是大写的。
true => True
false => False

## 逻辑运算符
py中符号变成了英文单词，可读性更高了。
&& => and
|| => or
!  => not

## 空值
py中没有undefined
null => None

## 变量
不能出现$

## 字符串
类似c中的printf的占位符形式的字符串模板，更简洁了
'你好%s' % '杨先生'
'你好%s和%s' % ('杨先生', '杨妈妈')


## 数组
Array => list
字面量还是和js数组一样，不过下标访问可以使用负数，倒序访问元素。
尾部插入push => append
插入splice => insert
删除末尾splice => pop
删除指定位置splice => pop(i)
.length => len()

### 元数组(tuple)
不可变的数组，对象类型的元素内容貌似可以改变
字面量为 (1,3,4) or (1,)
tuple赋值给多个变量，会按位置赋值


## 条件判断
没有了括号，更简洁了
if (a == true) 
	alert (a)

=>

if a == True:
	alert (a)

如果是条件判断可以简写

if a:
	alert (a)

注意：js中只要是对象转换成bool类型都是true，但是py中非空list才是


## 隐式类型转换
py中数字和字符串运算的时候会报错，请用int()或者str() ??转换成同类型

## 循环
不得不说py语法的简洁啊
需求：循环一个数组计算总数
js：
var arr = [1,2,3,4,5]
for (var key in arr) {
	total += arr[key];
}
py:
arr = [1,2,3,4,5]
for val in arr:
	total += val
循环的另一种形式
js:
var arr = [1,2,3,4,5]


ps:
py中提供了很多类型强制类型转换的函数，或者说是类型构造函数？
以及很多工具函数
for val in list(range(5)):
	total += val


## 字典（dict)
js中的对象
好像dict不支持点表达式
支持的有下标和get方法
get()方法的第二个参数可以指定如果访问的key不存在的话返回的是什么值


## 函数
py中函数也是对象
函数默认返回None
空语句变成pass而不是;
返回多个值可以考虑返回tuple
函数返回tuple是可以省略（）的

### 默认参数
很好理解，需要注意的是
py中函数的默认参数如果是可变类型对象，每次函数调用的结束的时候，这个默认参数似乎并不被释放，因此尽量使用不可变类型对象

### 可变参数
可变参数允许你传入0个或任意个参数，这些可变参数在函数调用时自动组装为一个tuple。
def func (*names):
	pass
调用时需要注
a = [1, 2, 3]
func(*a)

### 关键字参数
怎么理解呢，就把他理解成js中的对象解构赋值

def func (**person):
	pass

func (name='yb', age=18)

或者

a = {name:'yb', age:18}
func (**a)

注意：函数内部的person是一份拷贝

#### 限制关键字参数的名字
需要用到特殊的*分隔符
也可以有默认值


### 参数组合
参数定义的顺序必须是：必选参数、默认参数、可变参数、命名关键字参数和关键字参数


## 异常
raise TypeError('bad operand type')

## set
无序不重复列表，由list构造？
元素不能是可变对象
因为内部无法判断是否相等（所以==是判断内容？）

string是不可变对象

## 数组切片（slice）
arr = range(10)
arr[0:10]
arr[:10]
arr[:]
arr[:5:2] =》前5个，每2个取一个


## 迭代
因为dict的存储不是按照list的方式顺序排列，所以，迭代出的结果顺序很可能不一样。
任何可迭代对象都可以作用于for循环
测试是否是可迭代对象
isinstance('abc', Iterable) 

for k, v in d.items()

enumerate函数可以把一个list变成索引-元素对
for i, value in enumerate(['A', 'B', 'C']):
   print(i, value)

for x, y in [(1, 1), (2, 4), (3, 9)]:
   print(x, y)


## 列表生产式
list()
[x * x for x in range(1, 11)]
[x * x for x in range(1, 11) if x % 2 == 0]
[m + n for m in 'ABC' for n in 'XYZ']

## 生成器
和js中的生成器是一样一样的

生成器？
g = (x * x for x in range(10))

生成器函数？
def fib(max):
    n, a, b = 0, 0, 1
    while n < max:
        yield b
        a, b = b, a + b
        n = n + 1
    return 'done'

## 迭代器
isinstance([], Iterable)


# 待解决的疑问
python中可以不声明就使用变量吗

def person(name, age, *args, city, job):