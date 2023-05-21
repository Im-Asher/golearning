# 循环语句

## 1.for 循环

- 语法形式
    ```
    # 形式1
    # init： 一般为赋值表达式，给控制变量赋初值；
    # condition： 关系表达式或逻辑表达式，循环控制条件；
    # post： 一般为赋值表达式，给控制变量增量或减量。
    for init; condition; post { }

    # 形式2
    for condition { }

    # 形式3
    for { }
    ```
- 解释
  
  for语句执行过程如下：

    1、先对表达式 1 赋初值；    

    2、判别赋值表达式 init 是否满足给定条件，若其值为真，满足循环条件，则执行循环体内语句，然后执行 post，进入第二次循环，再判别 condition；否则判断 condition 的值为假，不满足条件，就终止for循环，执行循环体外语句。

## 2.循环控制语句

| **控制语句**  | **语句描述**                                     |
| ------------- | ------------------------------------------------ |
| break 语句    | 经常用于中断当前 for 循环或跳出 switch 语句      |
| continue 语句 | 跳过当前循环的剩余语句，然后继续进行下一轮循环。 |
| goto 语句     | 将控制转移到被标记的语句。                       |


## 3.for 循环的 range 格式

for 循环的 range 格式可以对 slice、map、数组、字符串等进行迭代循环。

- 语法形式
    ```
    # 形式1
    for key, value := range oldMap {
        newMap[key] = value
    }

    # 形式2
    for key := range oldMap

    # 形式3
    sfor key, _ := range oldMap

    # 形式4
    for _, value := range oldMap
    ```


- 实例

    ```
    package main

    import "fmt"

    func main() {
    sum := 0
        for i := 0; i <= 10; i++ {
            sum += i
        }
    fmt.Println(sum)
    }
    ```

- 执行结果

    ```
    55
    ```

- 实例2

    ```
    package main

    import "fmt"

    func main() {
        sum := 1
        for ; sum <= 10; {
            sum += sum
        }
        fmt.Println(sum)

        // 这样写也可以，更像 While 语句形式
        for sum <= 10{
            sum += sum
        }
        fmt.Println(sum)
    }
    ```
- 执行结果

    ```
    16
    16
    ```

- 实例3

    ```
    package main

    import "fmt"

    func main() {
        sum := 0
        for {
            sum++ // 无限循环下去
        }
        fmt.Println(sum) // 无法输出
    }
    ```
- 执行结果

    ```
    无输出结果
    # 无限循环
    ```

- 实例4

    ```
    package main
    import "fmt"

    func main() {
        strings := []string{"google", "runoob"}
        for i, s := range strings {
            fmt.Println(i, s)
        }


        numbers := [6]int{1, 2, 3, 5}
        for i,x:= range numbers {
            fmt.Printf("第 %d 位 x 的值 = %d\n", i,x)
        }  
    }
    ```
- 执行结果

    ```
    0 google
    1 runoob
    第 0 位 x 的值 = 1
    第 1 位 x 的值 = 2
    第 2 位 x 的值 = 3
    第 3 位 x 的值 = 5
    第 4 位 x 的值 = 0
    第 5 位 x 的值 = 0
    ```

- 实例5

    ```
    package main
    import "fmt"

    func main() {
        map1 := make(map[int]float32)
        map1[1] = 1.0
        map1[2] = 2.0
        map1[3] = 3.0
        map1[4] = 4.0
    
        // 读取 key 和 value
        for key, value := range map1 {
            fmt.Printf("key is: %d - value is: %f\n", key, value)
        }

        // 读取 key
        for key := range map1 {
            fmt.Printf("key is: %d\n", key)
        }

        // 读取 value
        for _, value := range map1 {
            fmt.Printf("value is: %f\n", value)
        }
    }
    ```
- 执行结果

    ```
    key is: 4 - value is: 4.000000
    key is: 1 - value is: 1.000000
    key is: 2 - value is: 2.000000
    key is: 3 - value is: 3.000000
    key is: 1
    key is: 2
    key is: 3
    key is: 4
    value is: 1.000000
    value is: 2.000000
    value is: 3.000000
    value is: 4.000000
    ```

## 4.嵌套循环

- 语法形式
  ```
    for [condition |  ( init; condition; increment ) | Range]
    {
        for [condition |  ( init; condition; increment ) | Range]
        {
            statement(s);
        }
    statement(s);
    }
  ```

- 实例
  ```
    package main

    import "fmt"

    func main() {
        /* 定义局部变量 */
        var i, j int

        for i=2; i < 100; i++ {
            for j=2; j <= (i/j); j++ {
                if(i%j==0) {
                    break; // 如果发现因子，则不是素数
                }
            }
            if(j > (i/j)) {
                fmt.Printf("%d  是素数\n", i);
            }
        }  
    }

  ```

- 运行结果

    ```
    2  是素数
    3  是素数
    5  是素数
    7  是素数
    11  是素数
    13  是素数
    17  是素数
    19  是素数
    23  是素数
    29  是素数
    31  是素数
    37  是素数
    41  是素数
    43  是素数
    47  是素数
    53  是素数
    59  是素数
    61  是素数
    67  是素数
    71  是素数
    73  是素数
    79  是素数
    83  是素数
    89  是素数
    97  是素数
    ```