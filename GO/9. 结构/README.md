## 数据封装

1. 结构体定义

```go
type Employee struct {
    Id   string
    Name string
    Age  int
}
```

2. 实例创建与初始化

```go
e := Employee{"1", "Bob", 20}
e1 := Employee{Name: "Kay", Age: 30}
e2 := new(Employee)     // 返回引用/指针，相当于 e := &Employee{}
e2.Id = "2"             // 通过指针访问成员，不需要用->
```

## 行为封装

1. 定义
```go
// 值拷贝，实例成员会进行值赋值
func (e Employee) String() string {
    return fmt.Sprintf("ID:%s-Name:%s-Age:%d", e.Id, e.Name, e.Age)
}
// 传指针，避免结构内存拷贝
func (e *Employee) String() string {
    return fmt.Sprintf("ID:%s-Name:%s-Age:%d", e.Id, e.Name, e.Age)
}

e := Employee{"1", "Bob", 20}
t.Log(e.String())
```
