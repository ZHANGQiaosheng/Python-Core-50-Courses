# f-string 在 print() 函数中的妙用

## 什么是 f-string？

小朋友们，你们有没有想过让电脑说话的时候更聪明一些呢？比如说，我们想让电脑告诉我们"小明今年8岁"，但是如果我们换了一个人，比如"小红今年9岁"，我们不想每次都重新写一遍代码。这时候，f-string 就像是一个神奇的魔法，可以帮助我们！

f-string 是 Python 中一种特殊的字符串，它的前面有一个字母 `f`，就像给字符串戴上了一顶魔法帽。在这个字符串里面，我们可以用 `{}` 大括号来放入变量，Python 会自动把变量的值填进去。

## 基本语法

f-string 的基本写法是这样的：
```python
f"这里是文字 {变量名} 这里又是文字"
```

让我们看一个简单的例子：

```python
name = "小明"
age = 8
print(f"你好，我是{name}，今年{age}岁了！")
```

运行结果：
```
你好，我是小明，今年8岁了！
```

是不是很神奇？Python 自动把 `{name}` 替换成了"小明"，把 `{age}` 替换成了8！

## 在变量中使用 f-string

### 1. 不同类型的变量

f-string 可以处理各种不同类型的数据，就像一个万能的翻译器：

```python
# 字符串变量
student_name = "小红"
print(f"学生姓名：{student_name}")

# 数字变量
score = 95
print(f"考试成绩：{score}分")

# 小数变量
height = 1.35
print(f"身高：{height}米")

# 布尔变量（真假值）
is_good_student = True
print(f"是好学生吗？{is_good_student}")
```

运行结果：
```
学生姓名：小红
考试成绩：95分
身高：1.35米
是好学生吗？True
```

### 2. 在大括号里进行计算

更神奇的是，我们还可以在大括号里直接进行计算！

```python
length = 5
width = 3
print(f"长方形的面积是：{length * width}平方米")

apple_count = 10
people_count = 3
print(f"平均每人可以分到{apple_count / people_count:.1f}个苹果")
```

运行结果：
```
长方形的面积是：15平方米
平均每人可以分到3.3个苹果
```

## 数字格式化 - 让数字更好看

有时候，我们希望数字显示得更整齐一些。f-string 提供了很多格式化的方法：

### 1. 控制小数位数

```python
pi = 3.1415926
print(f"π约等于：{pi:.2f}")  # 保留2位小数
print(f"π约等于：{pi:.1f}")  # 保留1位小数
print(f"π约等于：{pi:.0f}")  # 不保留小数
```

运行结果：
```
π约等于：3.14
π约等于：3.1
π约等于：3
```

### 2. 数字对齐和补零

```python
number = 7
print(f"编号：{number:03d}")  # 用0补足3位数
print(f"编号：{number:>5d}")  # 右对齐，总共5位
print(f"编号：{number:<5d}")  # 左对齐，总共5位
```

运行结果：
```
编号：007
编号：    7
编号：7    
```

### 3. 添加符号

```python
temperature = 25
cold_temp = -5
print(f"今天温度：{temperature:+d}°C")  # 显示正号
print(f"昨天温度：{cold_temp:+d}°C")   # 显示负号
```

运行结果：
```
今天温度：+25°C
昨天温度：-5°C
```

## 调用函数

f-string 中还可以调用函数，让我们的代码更强大：

```python
def get_grade(score):
    if score >= 90:
        return "优秀"
    elif score >= 80:
        return "良好"
    elif score >= 60:
        return "及格"
    else:
        return "不及格"

math_score = 95
chinese_score = 85

print(f"数学成绩：{math_score}分，等级：{get_grade(math_score)}")
print(f"语文成绩：{chinese_score}分，等级：{get_grade(chinese_score)}")
```

运行结果：
```
数学成绩：95分，等级：优秀
语文成绩：85分，等级：良好
```

## f-string 与普通字符串的区别

让我们来比较一下使用 f-string 和不使用 f-string 的区别：

### 方法一：使用加号拼接（比较麻烦）
```python
name = "小明"
age = 8
# 使用 + 号拼接，很麻烦
print("你好，我是" + name + "，今年" + str(age) + "岁了！")
```

### 方法二：使用 % 格式化（比较复杂）
```python
name = "小明"
age = 8
# 使用 % 格式化，需要记住很多符号
print("你好，我是%s，今年%d岁了！" % (name, age))
```

### 方法三：使用 f-string（最简单！）
```python
name = "小明"
age = 8
# 使用 f-string，简单清楚
print(f"你好，我是{name}，今年{age}岁了！")
```

可以看出，f-string 是最简单、最好理解的方法！

## 多种数据类型的综合例子

让我们来看一个包含多种数据类型的完整例子：

```python
# 学生信息
student_name = "李小华"
student_age = 10
student_height = 1.42
student_weight = 35.5
favorite_subjects = ["数学", "科学", "美术"]
is_monitor = True

# 使用 f-string 输出完整信息
print(f"=== 学生档案 ===")
print(f"姓名：{student_name}")
print(f"年龄：{student_age}岁")
print(f"身高：{student_height}米")
print(f"体重：{student_weight:.1f}公斤")
print(f"BMI指数：{student_weight / (student_height * student_height):.1f}")
print(f"喜欢的科目：{', '.join(favorite_subjects)}")
print(f"是否是班长：{'是' if is_monitor else '不是'}")
print(f"总共有{len(favorite_subjects)}个喜欢的科目")
```

运行结果：
```
=== 学生档案 ===
姓名：李小华
年龄：10岁
身高：1.42米
体重：35.5公斤
BMI指数：17.6
喜欢的科目：数学, 科学, 美术
是否是班长：是
总共有3个喜欢的科目
```

## 练习题

现在轮到你来试试了！完成下面的练习题：

### 练习1：个人介绍
创建变量存储你的姓名、年龄、最喜欢的颜色，然后用 f-string 输出一句完整的自我介绍。

```python
# 在这里写你的代码
my_name = "你的姓名"
my_age = 你的年龄
favorite_color = "你最喜欢的颜色"

# 使用 f-string 输出
print(f"大家好，我是{my_name}，今年{my_age}岁，我最喜欢{favorite_color}色！")
```

### 练习2：数学计算器
用 f-string 制作一个简单的数学计算器：

```python
# 在这里写你的代码
num1 = 15
num2 = 7

print(f"{num1} + {num2} = {num1 + num2}")
print(f"{num1} - {num2} = {num1 - num2}")
print(f"{num1} × {num2} = {num1 * num2}")
print(f"{num1} ÷ {num2} = {num1 / num2:.2f}")
```

### 练习3：购物清单
帮妈妈制作一个购物清单：

```python
# 在这里写你的代码
apple_price = 6.5
apple_count = 3
banana_price = 4.2
banana_count = 2

apple_total = apple_price * apple_count
banana_total = banana_price * banana_count
total_cost = apple_total + banana_total

print(f"苹果：{apple_price}元/斤 × {apple_count}斤 = {apple_total}元")
print(f"香蕉：{banana_price}元/斤 × {banana_count}斤 = {banana_total}元")
print(f"总计：{total_cost}元")
```

### 练习4：成绩报告单
制作一个成绩报告单：

```python
# 在这里写你的代码
subject1 = "语文"
score1 = 92
subject2 = "数学"
score2 = 88
subject3 = "英语"
score3 = 95

average_score = (score1 + score2 + score3) / 3

print(f"=== 成绩报告单 ===")
print(f"{subject1}：{score1}分")
print(f"{subject2}：{score2}分")
print(f"{subject3}：{score3}分")
print(f"平均分：{average_score:.1f}分")
```

## 章节总结

通过这一章的学习，我们掌握了：

1. **f-string 的基本概念**：在字符串前加 `f`，用 `{}` 包围变量名
2. **变量嵌入**：可以在 f-string 中嵌入各种类型的变量
3. **表达式计算**：可以在 `{}` 中直接进行数学运算
4. **函数调用**：可以在 f-string 中调用函数
5. **数字格式化**：
   - `:.2f` 保留2位小数
   - `:03d` 用0补足3位数
   - `:+d` 显示正负号
6. **与其他方法的比较**：f-string 是最简单易懂的字符串格式化方法

f-string 就像是给字符串施了魔法，让我们可以轻松地把变量的值嵌入到文字中。它不仅写起来简单，读起来也很清楚，是 Python 程序员最喜欢使用的字符串格式化方法。

记住：**简单的事情简单做，复杂的事情简单做，这就是编程的魅力！**

下次当你需要在 print() 函数中显示变量的值时，不要忘记使用 f-string 这个强大的工具哦！