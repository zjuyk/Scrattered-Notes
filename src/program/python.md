## pip

pip 是 python 的包管理器，属于勉强能用的水平，如果你在 linux 上，不建议用它，尤其是不要做 sudo pip 这样的操作，容易和本身的包管理器打架。

### 设置国内镜像

临时使用，以阿里云举例

```bash
pip install -i https://mirrors.aliyun.com/pypi/simple/ --trusted-host mirrors.aliyun.com
```

永久配置

```bash
# Linux
mkdir -p ~/.pip
echo """
[global]
index-url = http://mirrors.aliyun.com/pypi/simple/
[install]
trusted-host=mirrors.aliyun.com
""" > ~/.pip/pip.conf
```

```powershell
# Windows: C:\Users\username\pip\pip.ini
[global]
index-url = http://mirrors.aliyun.com/pypi/simple/
[install]
trusted-host=mirrors.aliyun.com
```

## venv

写大工程要隔离这是必须要注意的操作，虚拟环境保证了版本的正常维护

```python
python -m venv /path/to/new/virtual/environment
```

## 注意点

### in

如果涉及的数据很多，一定要用 set，因为 set 的 in 操作是 O(1) 的，用 list 是 O(n) 速度太慢

### pow

注意内置的 pow 和 math 库里的 pow 接收的参数是不一样的，前者可以接受 3 个参数


## 小片段功能代码

- 生成固定长度随机字符串密码

```python
import random
import string
def random_str(length=8):
    return "".join(random.sample(string.ascii_letters, length))
```

```python
from random import Random
def random_str(randomlength=8):
    str = ''
    chars = 'AaBbCcDdEeFfGgHhIiJjKkLlMmNnOoPpQqRrSsTtUuVvWwXxYyZz0123456789'
    length = len(chars) - 1
    random = Random()
    for i in range(randomlength):
        str+=chars[random.randint(0, length)]
    return str
```

- 二进制字符串转普通字符串

每 8 个分成一组，用 int 转 10 进制，再用 chr 转为 ascii 字符
```python
s="0110001101111001"
ans=""
for i in range(0,len(s)//8):
    x = s[i*8:i*8+8]
    ans+=chr(int(x,2))
```

利用 binascii，先用 int 转为 10 进制，然后转为 16 进制字符串，调用 unhexlify 执行翻译

```python
import binascii
s="0110001101111001"
ans=binascii.unhexlify('%x'%int(s,2)).decode()
```

- 符号数与无符号数转换

无符号 -> 有符号
```python
import ctypes
ctypes.c_int64(17039472050328044269).value
```

有符号 -> 无符号

```python
import ctypes
ctypes.c_uint64(-1407272023381507347).value
```

- 捕捉输入的 Ctrl+C

很邪恶的屏蔽用户输入 Ctrl+C 的做法

```python
import signal

def signal_handler(signum,data):
    if signum == signal.SIGINT:
        print("Ctrl+C is pressed!")
        # raise KeyboardInterrupt

if __name__ == '__main__':
    signal.signal(signal.SIGINT, signal_handler)
    sleep(666)
```

- AES 加密字符串

加密
```python
plaintext = "hello world"

import pyaes,base64
aes = pyaes.AESModeOfOperationCTR(b"This_key_for_demo_purposes_only!")
encrypted_text = base64.b64encode(aes.encrypt(plaintext.encode("utf-8")))

print(encrypted_text) # ipkEJevbnsfbEm4=
```

解密
```python
encrypted_text = "ipkEJevbnsfbEm4="

import pyaes, base64
aes = pyaes.AESModeOfOperationCTR(b"This_key_for_demo_purposes_only!")
plaintext = aes.decrypt(base64.b64decode(encrypted_text)).decode()

print(plaintext) # hello world
```
