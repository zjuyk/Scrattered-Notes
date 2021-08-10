# Rust

Rust 语言由 Mozilla 开发，最早发布于 2014 年 9 月。Rust 的编译器是在 MIT License 和 Apache License 2.0 双重协议声明下的免费开源软件。

## 优点

- **高性能** - Rust 速度惊人且内存利用率极高。由于没有运行时和垃圾回收，它能够胜任对性能要求特别高的服务，可以在嵌入式设备上运行，还能轻松和其他语言集成。
- **可靠性** - Rust 丰富的类型系统和所有权模型保证了内存安全和线程安全，让您在编译期就能够消除各种各样的错误。
- **生产力** - Rust 拥有出色的文档、友好的编译器和清晰的错误提示信息， 还集成了一流的工具 —— 包管理器和构建工具， 智能地自动补全和类型检验的多编辑器支持， 以及自动格式化代码等等。


## 特点

1. 可以在命令行利用 cargo 来处理编译等工作
2. cargo 默认使用 git 来管理项目
3. Rust 语言为了高并发安全而做的设计：在语言层面尽量少的让变量的值可以改变。不可变变量
4. Cargo 具有 cargo doc 功能，开发者可以通过这个命令将工程中的说明注释转换成 HTML 格式的说明文档
5. Rust不在乎您在何处定义函数，只需在某个地方定义它们即可
6. Rust 不支持 **++** 和 **--**，因为这两个运算符出现在变量的前后会影响代码可读性，减弱了开发者对变量改变的意识能力。
7. Rust 语言有原生的无限循环结构 —— loop


## 一些参考

- Rust 官方网站：[https://www.rust-lang.org/zh-CN](https://www.rust-lang.org/zh-CN)
- Rust 官方文档：[https://doc.rust-lang.org/](https://doc.rust-lang.org/)
- Rust Play：[https://play.rust-lang.org/](https://play.rust-lang.org/)

《rust by example》会比官方的 TRPL 简单一些，强烈建议看一看