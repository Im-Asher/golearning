# 数组
数组是具有相同唯一类型的一组已编号且长度固定的数据项序列，这种类型可以是任意的原始类型例如整型、字符串或者自定义类型。数组元素可以通过索引（位置）来读取（或者修改），索引从 0 开始，第一个元素索引为 0，第二个索引为 1，以此类推。

- 语法形式

``` go
// Go 语言数组声明需要指定元素类型及元素个数
var variable_name [SIZE] variable_type


// 定义了数组 balance 长度为 10 类型为 float32
var balance [10] float32
```

## 初始化数组
数组初始化

``` go
var balance = [5]float32{1000.0, 2.0, 3.4, 7.0, 50.0}

// 通过字面量在声明数组的同时快速初始化数组
balance := [5]float32{1000.0, 2.0, 3.4, 7.0, 50.0}

// 数组长度不确定，可以使用 ... 代替数组的长度，编译器会根据元素个数自行推断数组的长度
var balance = [...]float32{1000.0, 2.0, 3.4, 7.0, 50.0}

balance := [...]float32{1000.0, 2.0, 3.4, 7.0, 50.0}

// 设置了数组的长度，我们还可以通过指定下标来初始化元素
// 将索引为 1 和 3 的元素初始化
balance := [5]float32{1:2.0,3:7.0}

// 初始化数组中 {} 中的元素个数不能大于 [] 中的数字。

// 如果忽略 [] 中的数字不设置数组大小，Go 语言会根据元素的个数来设置数组的大小

// 读取了第五个元素。
balance[4] = 50.0

// 数组元素可以通过索引（位置）来读取（或者修改），索引从 0 开始，第一个元素索引为 0，第二个索引为 1，以此类推。
```

## 访问数组元素
数组元素可以通过索引（位置）来读取。格式为数组名后加中括号，中括号中为索引的值。
```go
// 读取数组 balance 第 10 个元素的值
var salary float32 = balance[9]
```

- 实例

```go
package main

import "fmt"

func main() {
   var n [10]int /* n 是一个长度为 10 的数组 */
   var i,j int

   /* 为数组 n 初始化元素 */        
   for i = 0; i < 10; i++ {
      n[i] = i + 100 /* 设置元素为 i + 100 */
   }

   /* 输出每个数组元素的值 */
   for j = 0; j < 10; j++ {
      fmt.Printf("Element[%d] = %d\n", j, n[j] )
   }
}
```

- 执行结果

``` go
Element[0] = 100
Element[1] = 101
Element[2] = 102
Element[3] = 103
Element[4] = 104
Element[5] = 105
Element[6] = 106
Element[7] = 107
Element[8] = 108
Element[9] = 109
```

- 实例

```go
package main

import "fmt"

func main() {
   var i,j,k int
   // 声明数组的同时快速初始化数组
   balance := [5]float32{1000.0, 2.0, 3.4, 7.0, 50.0}

   /* 输出数组元素 */         ...
   for i = 0; i < 5; i++ {
      fmt.Printf("balance[%d] = %f\n", i, balance[i] )
   }
   
   balance2 := [...]float32{1000.0, 2.0, 3.4, 7.0, 50.0}
   /* 输出每个数组元素的值 */
   for j = 0; j < 5; j++ {
      fmt.Printf("balance2[%d] = %f\n", j, balance2[j] )
   }

   //  将索引为 1 和 3 的元素初始化
   balance3 := [5]float32{1:2.0,3:7.0}  
   for k = 0; k < 5; k++ {
      fmt.Printf("balance3[%d] = %f\n", k, balance3[k] )
   }
}
```

- 执行结果

```go
balance[0] = 1000.000000
balance[1] = 2.000000
balance[2] = 3.400000
balance[3] = 7.000000
balance[4] = 50.000000
balance2[0] = 1000.000000
balance2[1] = 2.000000
balance2[2] = 3.400000
balance2[3] = 7.000000
balance2[4] = 50.000000
balance3[0] = 0.000000
balance3[1] = 2.000000
balance3[2] = 0.000000
balance3[3] = 7.000000
balance3[4] = 0.000000
```

## 多维数组

- 语法形式
```go
var variable_name [SIZE1][SIZE2]...[SIZEN] variable_type
```
- 实例

```go
// 声明了三维数组
var threedim [5][10][4]int
```

### 二维数组

二维数组是最简单的多维数组，二维数组本质上是由一维数组组成的。二维数组定义方式如下：

```go
// variable_type 为 Go 语言的数据类型，arrayName 为数组名，二维数组可认为是一个表格，x 为行，y 为列
var arrayName [ x ][ y ] variable_type
```
二维数组中的元素可通过 a[ i ][ j ] 来访问。
- 实例

```go
package main

import "fmt"

func main() {
    // Step 1: 创建数组
    values := [][]int{}

    // Step 2: 使用 append() 函数向空的二维数组添加两行一维数组
    row1 := []int{1, 2, 3}
    row2 := []int{4, 5, 6}
    values = append(values, row1)
    values = append(values, row2)

    // Step 3: 显示两行数据
    fmt.Println("Row 1")
    fmt.Println(values[0])
    fmt.Println("Row 2")
    fmt.Println(values[1])

    // Step 4: 访问第一个元素
    fmt.Println("第一个元素为：")
    fmt.Println(values[0][0])
}
```

- 执行结果
```go 
Row 1
[1 2 3]
Row 2
[4 5 6]
第一个元素为：
1
```

### 初始化二维数组
多维数组可通过大括号来初始值。以下实例为一个 3 行 4 列的二维数组：

```go 
a := [3][4]int{  
 {0, 1, 2, 3} ,   /*  第一行索引为 0 */
 {4, 5, 6, 7} ,   /*  第二行索引为 1 */
 {8, 9, 10, 11},   /* 第三行索引为 2 */
}
```
**注意：以上代码中倒数第二行的 } 必须要有逗号，因为最后一行的 } 不能单独一行，也可以写成这样：**
```go
a := [3][4]int{  
 {0, 1, 2, 3} ,   /*  第一行索引为 0 */
 {4, 5, 6, 7} ,   /*  第二行索引为 1 */
 {8, 9, 10, 11}}   /* 第三行索引为 2 */
 ```
以下实例初始化一个 2 行 2 列 的二维数组：

- 实例
```go
package main

import "fmt"

func main() {
    // 创建二维数组
    sites := [2][2]string{}

    // 向二维数组添加元素
    sites[0][0] = "Google"
    sites[0][1] = "Runoob"
    sites[1][0] = "Taobao"
    sites[1][1] = "Weibo"

    // 显示结果
    fmt.Println(sites)
}
```
- 执行结果

```go
[[Google Runoob] [Taobao Weibo]]
```

### 访问二维数组
二维数组通过指定坐标来访问。如数组中的行索引与列索引，例如：
```go
val := a[2][3]
// 或
var value int = a[2][3]
```
二维数组可以使用循环嵌套来输出元素：

```go
package main

import "fmt"

func main() {
   /* 数组 - 5 行 2 列*/
   var a = [5][2]int{ {0,0}, {1,2}, {2,4}, {3,6},{4,8}}
   var i, j int

   /* 输出数组元素 */
   for  i = 0; i < 5; i++ {
      for j = 0; j < 2; j++ {
         fmt.Printf("a[%d][%d] = %d\n", i,j, a[i][j] )
      }
   }
}
```
- 执行结果

```go
a[0][0] = 0
a[0][1] = 0
a[1][0] = 1
a[1][1] = 2
a[2][0] = 2
a[2][1] = 4
a[3][0] = 3
a[3][1] = 6
a[4][0] = 4
a[4][1] = 8
```
以下实例创建各个维度元素数量不一致的多维数组：

```go
package main

import "fmt"

func main() {
    // 创建空的二维数组
    animals := [][]string{}

    // 创建三一维数组，各数组长度不同
    row1 := []string{"fish", "shark", "eel"}
    row2 := []string{"bird"}
    row3 := []string{"lizard", "salamander"}

    // 使用 append() 函数将一维数组添加到二维数组中
    animals = append(animals, row1)
    animals = append(animals, row2)
    animals = append(animals, row3)

    // 循环输出
    for i := range animals {
        fmt.Printf("Row: %v\n", i)
        fmt.Println(animals[i])
    }
}
```
- 执行结果
```go
Row: 0
[fish shark eel]
Row: 1
[bird]
Row: 2
[lizard salamander]
```
## 向函数传递数组
在函数定义时，声明形参为数组
- 语法形式

```go
// 形参设定数组大小
void myFunction(param [10]int)
{
.
.
.
}
```

```go
// 形参未设定数组大小
void myFunction(param []int)
{
.
.
.
}
```
- 实例

实例中函数接收整型数组参数，另一个参数指定了数组元素的个数，并返回平均值
```go
func getAverage(arr []int, size int) float32
{
   var i int
   var avg, sum float32  

   for i = 0; i < size; ++i {
      sum += arr[i]
   }

   avg = sum / size

   return avg;
}
```
函数调用
```go
package main

import "fmt"

func main() {
   /* 数组长度为 5 */
   var  balance = [5]int {1000, 2, 3, 17, 50}
   var avg float32

   /* 数组作为参数传递给函数 */
   avg = getAverage( balance, 5 ) ;

   /* 输出返回的平均值 */
   fmt.Printf( "平均值为: %f ", avg );
}
func getAverage(arr [5]int, size int) float32 {
   var i,sum int
   var avg float32  

   for i = 0; i < size;i++ {
      sum += arr[i]
   }

   avg = float32(sum) / float32(size)

   return avg;
}
```

- 执行结果

```
平均值为: 214.399994
```

浮点数计算输出有一定的偏差，你也可以转整型来设置精度。

```go 
package main
import (
    "fmt"
)
func main() {
    a := 1.69
    b := 1.7
    c := a * b      // 结果应该是2.873
    fmt.Println(c)  // 输出的是2.8729999999999998
}
```

固定精度

```go
package main
import (
    "fmt"
)
func main() {
    a := 1690           // 表示1.69
    b := 1700           // 表示1.70
    c := a * b          // 结果应该是2873000表示 2.873
    fmt.Println(c)      // 内部编码
    fmt.Println(float64(c) / 1000000) // 显示
}
```