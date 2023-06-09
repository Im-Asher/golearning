# 条件语句

## 1.if条件语句

- 语法形式
    ```
    if 布尔表达式 {
        /* 在布尔表达式为 true 时执行 */
    }
    ```
- 实例

    ```
    package main

    import "fmt"

    func main() {
    /* 定义局部变量 */
    var a int = 10
    
    /* 使用 if 语句判断布尔表达式 */
    if a < 20 {
        /* 如果条件为 true 则执行以下语句 */
        fmt.Printf("a 小于 20\n" )
    }
    fmt.Printf("a 的值为 : %d\n", a)
    }
    ```

- 代码执行结果
    ```
    a 小于 20
    a 的值为 : 10
    ```
## 2.if...else语句

- 语法形式
    ```
    if 布尔表达式 {
        /* 在布尔表达式为 true 时执行 */
    } else {
        /* 在布尔表达式为 false 时执行 */
    }
    ```
- 实例

    ```
    package main

    import "fmt"

    func main() {
        /* 局部变量定义 */
        var a int = 100;
        
        /* 判断布尔表达式 */
        if a < 20 {
            /* 如果条件为 true 则执行以下语句 */
            fmt.Printf("a 小于 20\n" );
        } else {
            /* 如果条件为 false 则执行以下语句 */
            fmt.Printf("a 不小于 20\n" );
        }
        fmt.Printf("a 的值为 : %d\n", a);
    }
    ```
- 代码执行结果
    ```
    a 不小于 20
    a 的值为 : 100
    ```

## 3.if 语句嵌套

- 语法形式
    ```
    if 布尔表达式 1 {
        /* 在布尔表达式 1 为 true 时执行 */
        if 布尔表达式 2 {
            /* 在布尔表达式 2 为 true 时执行 */
        }
    }
    ```
- 实例

    ```
    package main

    import "fmt"

    func main() {
        /* 定义局部变量 */
        var a int = 100
        var b int = 200
        
        /* 判断条件 */
        if a == 100 {
            /* if 条件语句为 true 执行 */
            if b == 200 {
                /* if 条件语句为 true 执行 */
                fmt.Printf("a 的值为 100 ， b 的值为 200\n" );
            }
        }
        fmt.Printf("a 值为 : %d\n", a );
        fmt.Printf("b 值为 : %d\n", b );
    }
    ```
- 代码执行结果
    ```
    a 的值为 100 ， b 的值为 200
    a 值为 : 100
    b 值为 : 200
    ```
## 4.switch 语句

- 语法形式
    ```
    switch var1 {
        case val1:
            ...
        case val2:
            ...
        default:
            ...
    }
    ```
- 实例

    ```
    package main

    import "fmt"

    func main() {
        /* 定义局部变量 */
        var grade string = "B"
        var marks int = 90

        switch marks {
            case 90: grade = "A"
            case 80: grade = "B"
            case 50,60,70 : grade = "C"
            default: grade = "D"  
        }

        switch {
            case grade == "A" :
                fmt.Printf("优秀!\n" )    
            case grade == "B", grade == "C" :
                fmt.Printf("良好\n" )      
            case grade == "D" :
                fmt.Printf("及格\n" )      
            case grade == "F":
                fmt.Printf("不及格\n" )
            default:
                fmt.Printf("差\n" );
        }
        fmt.Printf("你的等级是 %s\n", grade );      
    }
    ```
- 代码执行结果
    ```
    优秀!
    你的等级是 A
    ```
## 5.Type Switch
    
switch 语句还可以被用于 type-switch 来判断某个 interface 变量中实际存储的变量类型。

- 语法形式
    ```
    switch x.(type){
        case type:
            statement(s);      
        case type:
            statement(s); 
        /* 你可以定义任意个数的case */
        default: /* 可选 */
            statement(s);
    }
    ```
- 实例

    ```
    package main

    import "fmt"

    func main() {
        var x interface{}
        
        switch i := x.(type) {
            case nil:  
                fmt.Printf(" x 的类型 :%T",i)                
            case int:  
                fmt.Printf("x 是 int 型")                      
            case float64:
                fmt.Printf("x 是 float64 型")          
            case func(int) float64:
                fmt.Printf("x 是 func(int) 型")                      
            case bool, string:
                fmt.Printf("x 是 bool 或 string 型" )      
            default:
                fmt.Printf("未知型")    
        }  
    }
    ```
- 代码执行结果
    ```
    x 的类型 :<nil>
    ```

## 6.fallthrough
使用 fallthrough 会强制执行后面的 case 语句，fallthrough 不会判断下一条 case 的表达式结果是否为 true。

- 实例
```
package main

import "fmt"

func main() {

    switch {
    case false:
            fmt.Println("1、case 条件语句为 false")
            fallthrough
    case true:
            fmt.Println("2、case 条件语句为 true")
            fallthrough
    case false:
            fmt.Println("3、case 条件语句为 false")
            fallthrough
    case true:
            fmt.Println("4、case 条件语句为 true")
    case false:
            fmt.Println("5、case 条件语句为 false")
            fallthrough
    default:
            fmt.Println("6、默认 case")
    }
}

```

- 代码执行结果
```
2、case 条件语句为 true
3、case 条件语句为 false
4、case 条件语句为 true
```

## 7.select 语句
等待补充