# 一、变量和函数

## 1.变量

1. ### val 和var

2. ### var 修饰的非基础类型在定义时必须被初始化，否则要加上关键字lateinit，除非所有构造器都对其赋值

## 2.单行和近似单行函数体的 函数，可以省略函数体(见二.1/2)

# 二、逻辑控制

## 1.if可以有返回值，即最后一行的值。可以配合 2语法糖使用

```kotlin
fun largerNum(num1: Int, num2: Int) = if (num1 > num2) num1 else num2

```

## 2.when语句-升级版switch

```kotlin
when(para){
	case->{return}
    ...
    else->{return}
}
```

- 可以传父类进行类型匹配

```kotlin
fun checkNumber(num: Number) {
    when (num) {
		is Int -> println("number is Int") 	
        is Double -> println("number is Double") 
        else -> println("number not support")
	} 
}
```

- 也可以不传，引用外部值，用于合并处理多个case

```kotlin
fun getScore(name: String) = when { 
    name.startsWith("Tom") -> 86 
    name == "Jim" -> 77 name == "Jack" -> 95 
    name == "Lily" -> 100 else -> 0
}
```

## 3.区间 和 for-in

### 区间

0~10闭区间

```kotlin
val range = 0..10
```

0~10左闭右开

```kotlin
val range = 0 until 10
```

02468步长

```kotlin
val range = 0 until 10 step 2
```

降序 闭区间

```kotlin
val range = 10 downTo 0
```

### for-in



```kotlin
for (i in 0..10 step 2) { 
    println(i)
}
```

# 三、面向对象

## 1. 构造器

1. ###  主次构造器

   1. ####  分为主构造器和次构造器，主构造器写在类名括号里。不能在主构造器写逻辑代码

   2. #### 如果不写构造器，则默认有空参主构造器。反之不会默认添加空参构造器

   3. #### 子类构造器必须调用父类构造器，且默认调用空参构造（如果有）

   4. #### 次构造器必须调用主构造器,若没有可以调父类主构造器

2. ### init代码块

   1. #### 相当于非静态代码块，每次创建对象都执行一次

3. ### 子类有参主构造器调用父类有参构造器

   1. #### 不用再写val或者var，否则会被当做子类成员

## 2.继承

1. ### 被继承的类，和方法需要在前面加上open关键字

2. ### ==子类对象怎么调用父类方法?==

## 3.静态方法和静态代码块？

## 4.接口

1. ### 可以设置接口默认方法

2. 实现类需要override即实现

## 5.权限修饰符

| 修饰符    | java                                         | kotlin         |
| --------- | -------------------------------------------- | -------------- |
| public    | 所有类                                       | 所有类（默认） |
| private   | 当前类                                       | 当前类         |
| protected | 当前类，子类                                 | 当前类，子类   |
| default   | 同包（当前类，同包子类，同包其他类）（默认） | 无             |
| internal  | 无                                           | 同一模块       |

## 6.数据类

1. ### data修饰工具类，自动重写hashcode，equals，toString方法

```kotlin
data class Cellphone(val brand: String, val price: Double)
```

## 7.单例方法

1. ### 原理：构造方法私有化，实例对象作为本身私有成员，静态方法保证只有一个实例对象并传出

2. ### kotlin写法：只需类前加object修饰，正常写成员，方法就可以
