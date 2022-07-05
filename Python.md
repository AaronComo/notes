# **python**

1、变量构建无需声明，直接赋值

```python
first_name = "Cris"
last_name = "Hue"
num = 12
```



2、+可以连接两个字符串

```python
print("Your name is " first_name + last_name)
```



3、用户输入

```python
name = input("提示语")  # input函数始终将读取内容转换为字符串储存
```



4、字符串函数

```python
first_name.upper()  # 全体大写
first_name.capitalize()  # 首字母大写
first_name.lower()  # 全体小写
```



5、格式化字符串

```python
num = 23

output1 = "Hello, " + first_name + " " + last_name
output2 = "Hello, {} {}".format(first_name, last_name)
output3 = "Hello, {0} {1}".format(num, last_name)
output4 = "Hello, {1}, {0}".format(first_name, last_name)
output5 = f"Hello, {first_name} {last_name}"  # Py3 only

print(output1)
print(output2)
print(output3)
print(output4)
print(output5)
```



6、运算符

```python
+
-
*  # 对字符串使用可以将n个字符串拼接在一起
/  # 可以带小数
%  # 取余
//  # 整除
**  # 指数
```



7、类型转换

```python
str(variable)
int(variable)
float(variable)
```



8、日期

```python
# 引用函数库
from datetime import datetime, timedelta
```

- 日期的类型类似于c语言结构体，可以用 . 向下访问second/minute/hour/day/month/year等，详见说明

- 一些日期函数

  ```python
  from datetime import datetime
  datetime.now()  # 获取当前时间
  datetime.strptime()  # 格式化读取，参数%d/%m/%Y(注意大写表示4位年份)
  
  from datetime import datetime, timedelta
  timedelta()  # 日期偏移量，参数days=x,weeks=x,years=x等，详见说明
  ```



9、错误

```python
try:
    <code 1>
except ErrorType1:  # 若发生ErrorType1类型的错误，则执行code2
    <code 2>
except ErrorType2 as e:  # 若发生ErrorType类型的错误，则执行code3，并将ErrorType类型中的错误信息赋给变量e
    <code 3>
except:  # 若发生错误，则执行code4（后面应该跟上条件）
    <code 4>
else:  # 若未发生上述错误，执行code5
    <code 5>
finally:  # code6一定被执行，此条可省略
    <code 6>
```



10、条件

```python
if condition:
    <code>
elif condition:
    <code>
else:
    <code>
```

- tips:处理字符串时，可以先将输入转为统一的大小写再比较

  ```python
  a = input('Hello! \
  	Where are you from?')  # '\'连接两行
  a = a.lower()
  ...
  ```

- in 的使用

  ```python
  if variable in (condition1, condition2, ...):  # variable符合任意括号中的条件，则执行
  ```

  



11、布尔值（注意首字母大写）

- True
- False



12、列表

```python
list1 = ['hhhh', 12, 34.3]
list2 = []  # 空列表
```

- 表中内容可为任意类型混用

- 可用 [ ] 访问列表中元素

- 插入元素

  ```python
  list.append(value)  # 向列表尾插入value
  list.insert(position, value)  # 向positon位置插入value
  ```



13、数组

```python
from array import array  # 引用array库
arr = array(Type)
```

| Type |       C Type       |    Python Type    | Minimum size in bytes |
| :--: | :----------------: | :---------------: | :-------------------: |
| 'b'  |        char        |        int        |           1           |
| 'B'  |   unsigned char    |        int        |           1           |
| 'u'  |     Py_UNICODE     | Unicode character |           2           |
| 'h'  |       short        |        int        |           2           |
| 'H'  |   unsigned short   |        int        |           2           |
| 'i'  |        int         |        int        |           2           |
| 'I'  |    unsigned int    |        int        |           2           |
| 'l'  |        long        |        int        |           4           |
| 'L'  |   unsigned long    |        int        |           4           |
| 'q'  |     long long      |        int        |           8           |
| 'Q'  | unsigned long long |        int        |           8           |
| 'f'  |       float        |       float       |           4           |
| 'd'  |       double       |       float       |           8           |

