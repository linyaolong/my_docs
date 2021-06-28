## 基本使用

1. string是数据类型，不是引用或指针，零值是""
2. string是只读byte slice，len可以计算byte数
3. string的byte数组可以存放任何数据

```go
s := "hello"
s[1] = '1'      // 报错！string是不可变的
```

## Unicode UTF8

1. Unicode是一种字符集
2. UTF8是unicode的存储实现（转换为字节序列的规则）

```go
s := "中"
c := []rune(s)      // rune是go的内置机制，取出字符串里的Unicode

t.Log(len(s))       // byte数，3
t.Log(len(c))       // 1
t.Log("unicode %x", c[0])       // unicode 4e2d
t.Log("UTF 8 %x", s)            // UTF8 e4b8ad
```

3. 字符串遍历会转成rune而不是byte
```go
s := "中华"
for _, c := range s {
    t.Logf("%[1]c, %[1]x", c)
}
// 中 4e2d
// 华 534e
```

## 常用功能

1. strings包
2. strconv包
```go
// 分割
s := "a,b,c"
parts := strings.Split(s, ",")
// 连接
join := strings.Join(parts, "-")
// 转换
snum := strconv.Itoa(10)
num, err := strconv.Atoi("10")
```