## Go中的面向对象
### 使用 embed type 实现继承
Go 中的嵌入类型 embed type 本质上是一种 composition，Go 不像其它 OO 语言那样提供基于类的继承，那些继承体现的是 is-a 关系，但是 Go 不是。

***Go 通过 embed type，可以实现 method 和 field 的复用。***
```
package main

import (
    "fmt"
)

type Person struct {
    name string
    age  int
}

func (p *Person) sayName() {
    fmt.Println(p.name)
}

type Student struct {
    Person
    name string
}

func main() {
    p := Person{name: "C"}
    p.sayName() // #1 C

    s1 := Student{name: "Java"}
    s1.sayName() // #2 此行输出空字符串

    s2 := Student{name: "Java", Person: Person{name: "VB"}}
    s2.sayName()         // #3 VB
    fmt.Println(s2.name) // #4 Java
    fmt.Println(s2.Person.name) //#5 VB
}
```

### 类型组合的强大魔力
Go 支持任意类型的 embed type，当然也包括 interface type，通过组合就可以实现多种不同行为的任意组合，这也是 Go 倡导以更小的单元实现你的代码功能，然后组合它们的理念。