### 安装 QEMU
```
sudo apt-get update
sudo apt-get install qemu-user 
sudo apt-get install qemu-user-static
```

### 安装 binfmt-support
```
sudo apt-get install binfmt-support
```

### 将 QEMU 模拟器注册到内核
```
sudo update-binfmts --enable
```
