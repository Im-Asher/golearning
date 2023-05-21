# 函数声明和调用

## 函数声明

- 语法形式
	```
	func function_name( [parameter list] ) [return_types] {
	函数体
	}
	```
- func：函数由 func 开始声明
- function_name：函数名称，参数列表和返回值类型构成了函数签名。
- parameter list：参数列表，参数就像一个占位符，当函数被调用时，你可以将值传递给参数，这个值被称为实际参数。参数列表指定的是参数类型、顺序、及参数个数。参数是可选的，也就是说函数也可以不包含参数。
- return_types：返回类型，函数返回一列值。return_types 是该列值的数据类型。有些功能不需要返回值，这种情况下 return_types 不是必须的。
函数体：函数定义的代码集合

	```
	func SquaresOfSumAndDiff(a int64, b int64) (s int64, d int64) {
		x, y := a + b, a - b
		s = x * x
		d = y * y
		return // <=> return s, d
	}
	```
- 第一部分是func关键字。
- 第二部分是函数名称。函数名称必须是一个标识符。 这里的函数名称是SquareOfSumAndDiff。
- 第三部分是输入参数列表。输入参数声明列表必须用一对小括号括起来。 输入参数声明有时也称为形参声明（对应后面将介绍的函数调用中的实参）。
- 第四部分是输出结果声明列表。在Go中，一个函数可以有多个返回值。 比如上面这个例子就有两个返回值。 当一个函数的输出结果声明列表为空或者只包含一个匿名结果声明时，此列表可以不用一对小括号括起来（见下面的示例）；否则，小括号是必需的。
- 最后一部分是函数体。函数体必须用一对大括号括起来。 一对大括号和它其间的代码形成了一个显式代码块。 在一个函数体内，return关键字可以用来结束此函数的正常向前执行流程并进入此函数的退出阶段（详见下下节中的解释）。


- 实例

	```
	/* 函数返回两个数的最大值 */
	func max(num1, num2 int) int {
	/* 声明局部变量 */
	var result int

	if (num1 > num2) {
		result = num1
	} else {
		result = num2
	}
	return result
	}
	```

## 函数调用

- 实例
	```
	package main

	import "fmt"

	func main() {
	/* 定义局部变量 */
	var a int = 100
	var b int = 200
	var ret int

	/* 调用函数并返回最大值 */
	ret = max(a, b)

	fmt.Printf( "最大值是 : %d\n", ret )
	}

	/* 函数返回两个数的最大值 */
	func max(num1, num2 int) int {
	/* 定义局部变量 */
	var result int

	if (num1 > num2) {
		result = num1
	} else {
		result = num2
	}
	return result
	}

	```

- 代码执行结果
  
  ```
  最大值是 : 200
  ```


## 函数返回多个值

- 实例

	```
	package main

	import "fmt"

	func swap(x, y string) (string, string) {
		return y, x
	}

	func main() {
		a, b := swap("Google", "Runoob")
		fmt.Println(a, b)
	}
	```

- 代码执行结果
  
	```
	Runoob Google
	```


## 函数参数
函数如果使用参数，该变量可称为函数的形参。

形参就像定义在函数体内的局部变量。

调用函数，可以通过两种方式来传递参数：

| **传递类型** | **描述**                                                                                                     |
| ------------ | ------------------------------------------------------------------------------------------------------------ |
| 值传递       | 值传递是指在调用函数时将实际参数复制一份传递到函数中，这样在函数中如果对参数进行修改，将不会影响到实际参数。 |
| 引用传递     | 引用传递是指在调用函数时将实际参数的地址传递到函数中，那么在函数中对参数所进行的修改，将影响到实际参数。     |
