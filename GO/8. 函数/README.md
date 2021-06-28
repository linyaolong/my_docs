 函数式编程
1. 可以返回多个值
2. 所有参数都是值传递
3. 可以作为变量的值
4. 可以作为参数和返回值
```go
// 计算一个函数执行时间
func timeCost(inner func(op int) int) func (op int) int {
    return func(n int) int {
        start := time.Now()
        ret := inner(n)
        fmt.Pringln("time cost:", time.Since(start).Seconds())
        return ret
    }
}
```

## 可变参数

入参会被转化为数组
```go
func sum(ops ...int) int {
    s := 0
    for _, op := range ops {
        s += op
    }
    return s
 }
```

## 延迟执行函数 defer 函数

在函数返回前执行，类似于try catch finally中的finally

```go
func TestDefer(t *testing.T) {
    defer func() {          // 匿名函数，也可以不用匿名函数
        t.Log("Clear")
    }()
    t.Log("start")
    panic("error")          // 异常中断函数，依然会执行defer函数
    t.Log("finish")         // 不会执行
}
```
