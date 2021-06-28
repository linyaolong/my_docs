## 定义与实现

1. 接口为非入侵性，实现不依赖于接口定义
2. 接口定义可以包含在接口使用者包内
```go
// 接口定义
type Programmer interface {
    WriteHelloWorld() String
}

// 接口实现
type GoProgrammer struct {
}

func (gp *GoProgrammer) WriteHelloWorld() String {
    return "fmt.Println(\"Hello World\")"
}

// 接口调用
func TestInterface(t *testing.T) {
    var p Programmer
    p = new(GoProgrammer)
    t.Log(p.WriteHelloWorld())
}
```

## 接口变量
