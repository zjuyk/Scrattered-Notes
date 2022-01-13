### 四则运算

使用 `$(())` 来计算，注意涉及到不同进制的四则运算可以这样

```bash
# 5+0xa+0b1010
echo $((5+16#a+2#1010))
```

### 判断参数是否为空

```bash
if [ -z "$1" ] && [ -z "$2" ]; then
    echo "Usage: $0 <parameter1> <parameter2>"
fi
```

### 生成数字列表

注意终点的数字是包含的
```bash
for i in $(seq 1 $END); do echo $i; done
```

### 判断文件不存在

注意这里 `]` 前面的空格是不能省略的
```bash
if [ ! -f "somefile" ]; then
    curl ...
fi
```
