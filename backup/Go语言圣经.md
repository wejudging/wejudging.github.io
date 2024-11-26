**1. go.mod 是什么？**

作用：go.mod 是 Go 项目模块的描述文件，用于管理项目依赖和版本。
位置：通常位于项目的根目录。
功能：定义模块名称（项目的唯一标识）。
           记录项目依赖的第三方库及其版本。
           支持模块版本管理，方便复现项目构建环境。
           go.mod 的功能类似于其他语言中的依赖管理文件

例如：
           Node.js 的 package.json
           Python 的 requirements.txt
           Rust 的 Cargo.toml
