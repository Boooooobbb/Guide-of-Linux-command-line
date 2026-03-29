# Linux 命令行使用指南

> 适用于 Bash 环境的 Linux 命令行基础使用指南

## 目录

- [终端基本操作](#终端基本操作)
- [目录管理](#目录管理)
- [文件管理](#文件管理)
- [文件权限管理](#文件权限管理)
- [文件内容查看](#文件内容查看)
- [文件搜索](#文件搜索)
- [进程管理](#进程管理)
- [网络命令](#网络命令)
- [为长命令配置别名](#为长命令配置别名)

---

## 终端基本操作

- 改变命令行字体大小：按住`Ctrl`,上下滑动鼠标滚轮
- 清屏：`clear`
- 复制：使用光标选中需要复制的内容即可
- 粘贴：滚轮中键或右键
- 中断当前命令：`Ctrl + C`
- 暂停当前命令（挂起到后台）：`Ctrl + Z`
- 退出终端：`exit`

---

## 目录管理

- `cd`：**c**hange **d**irectory 切换目录
	- `cd`：回到默认目录（家目录）
	- `cd ~`：回到家目录
	- `cd ..`：回到上一目录
	- `cd -`：回到上一次所在的目录
- `ls`：**l**i**s**t directory 显示当前目录下文件
	- `ls -l`：显示当前目录下文件的**详细信息**
	- `ls -al`：显示当前目录下所有文件（包括**隐藏文件**）的**详细信息**
	- `ls -lh`：以人类可读的方式（如 KB、MB）显示文件大小
- `pwd`：**p**rint **w**orking **d**irectory 显示当前所在的目录
- `tree`：以树形结构显示目录内容
	- 例：`tree -L 2` 显示当前目录下两层深度的树形结构

---

## 文件管理

- `touch`：新建文件
	- 例：`touch gitcode.txt` 新建一个名为`gitcode.txt`的文本文档
- `mkdir`：**m**a**k**e **dir**ectory 新建文件夹
	- 例：`mkdir git` 在当前目录下新建一个名为`git`的文件夹
	- 例：`mkdir -p git/src/lib` 递归创建多层目录
- `rm`：**r**e**m**ove 删除文件
	- 例：`rm gitcode.txt` 删除名为`gitcode.txt`的文本文档
	- 例：`rm -r git` 删除名为`git`的文件夹（ ⚠ **警告**：`rm -r` 会永久删除文件夹，不会进入回收站，操作前请确认）
	- 例：`rm -i gitcode.txt` 删除前进行确认提示
- `mv`：**m**o**v**e 移动/重命名文件
	- 例：`mv gitcode.txt git/` 将`gitcode.txt`移动至`git`文件夹下
	- 例：`mv gitcode.txt git.txt` 将`gitcode.txt`重命名为`git.txt`（因为`git.txt`原本不存在，所以起到的是重命名功能）
- `cp`：**c**o**p**y 复制文件
	- 例：`cp gitcode.txt backup/` 将`gitcode.txt`文件复制到`backup`文件夹下
	- 例：`cp -r git/ git_backup/` 递归复制整个目录

---

## 文件权限管理

Linux 文件权限由三组字符表示：**所有者(u)**、**所属组(g)**、**其他人(o)**，每组分别对应读(r=4)、写(w=2)、执行(x=1)。

- `chmod`：**ch**ange **mod**e 修改文件权限
	- 例：`chmod 755 script.sh` 设置文件权限为 `rwxr-xr-x`
	- 例：`chmod +x script.sh` 为所有用户添加执行权限
	- 例：`chmod u-w file.txt` 移除所有者的写权限
- `chown`：**ch**ange **own**er 修改文件所有者
	- 例：`chown user file.txt` 将`file.txt`的所有者改为`user`
	- 例：`chown user:group file.txt` 同时修改所有者和所属组

---

## 文件内容查看

- `cat`：🐱**c**onc**a**tena**t**e 查看文件内容
	- 例：`cat gitcode.txt` 将`gitcode.txt`中的内容打印到屏幕
	- 例：`cat -n gitcode.txt` 显示内容并带上行号
- `less`：分页查看文件内容（按`q`退出，按空格/`b`前后翻页，按方向键逐行滚动，按`/`搜索）
	- 例：`less gitcode.txt`
- `head`：查看文件头部内容
	- 例：`head -n 10 gitcode.txt` 查看前 10 行
- `tail`：查看文件尾部内容
	- 例：`tail -n 10 gitcode.txt` 查看最后 10 行
	- 例：`tail -f log.txt` 实时监控文件末尾新增内容（常用于查看日志）

---

## 文件搜索

- `find`：在目录中搜索文件
	- 例：`find . -name "*.txt"` 在当前目录下搜索所有`.txt`文件
	- 例：`find /home -type d -name "git"` 在`/home`下搜索名为`git`的目录
	- 例：`find . -mtime -7` 查找最近 7 天内修改过的文件
- `grep`：在文件内容中搜索文本
	- 例：`grep "hello" gitcode.txt` 在`gitcode.txt`中搜索含有`hello`的行
	- 例：`grep -r "hello" .` 在当前目录下递归搜索含有`hello`的文件
	- 例：`grep -n "hello" gitcode.txt` 搜索并显示行号
	- 例：`grep -i "hello" gitcode.txt` 忽略大小写搜索

---

## 进程管理

- `ps`：查看当前运行的进程
	- 例：`ps aux` 显示所有用户的进程详情
	- 例：`ps -ef | grep python` 搜索名称含`python`的进程
- `top`：实时动态查看进程资源占用情况（按`q`退出）
- `kill`：终止进程
	- 例：`kill 1234` 向进程号为`1234`的进程发送终止信号
	- 例：`kill -9 1234` 强制终止进程号为`1234`的进程
- `jobs`：查看当前终端的后台任务
- `bg`：将挂起的任务放到后台运行
- `fg`：将后台任务调到前台运行

---

## 网络命令

- `ping`：测试与目标主机的网络连通性
	- 例：`ping google.com`
	- 例：`ping -c 4 google.com` 发送 4 个数据包后停止
- `wget`：从网络下载文件
	- 例：`wget https://example.com/file.zip`
	- 例：`wget -O myfile.zip https://example.com/file.zip` 下载并指定保存的文件名
	- 例：`wget -c https://example.com/file.zip` 断点续传，继续未完成的下载
- `curl`：发送网络请求或下载文件
	- 例：`curl https://example.com` 获取网页内容
	- 例：`curl -O https://example.com/file.zip` 下载文件并保留原文件名
- `ssh`：**S**ecure **Sh**ell 远程登录
	- 例：`ssh user@192.168.1.100` 使用用户名`user`登录远程主机
- `scp`：通过 SSH 安全传输文件
	- 例：`scp file.txt user@192.168.1.100:/home/user/` 将本地文件传输到远程主机

---

## 为长命令配置别名

1. 创建 Bash 配置文件（如果之前已经创建，请忽略该步骤）
	```bash
	touch ~/.bashrc
	```
2. 使用 Vim 编辑器编辑配置文件
	```bash
	vim ~/.bashrc
	```
	
	![Linux 命令行基本用法-为长命令配置别名-1](images/Linux%20命令行基本用法-为长命令配置别名-1.png)
	
3. 按一下键盘上的`i`进入编辑模式
	
	![Linux 命令行基本用法-为长命令配置别名-2](images/Linux%20命令行基本用法-为长命令配置别名-2.png)
	
4. 输入以下内容设置别名（请将`<shortcommand>`替换为需要设置的别名，别名可以根据个人的喜好确定，请将`<longcommand>`替换为需要设置别名的命令）
	```
	alias <shortcommand>='<longcommand>'
	```
5. 按下`Esc`键退出编辑模式，直接输入`：wq`并按回车键`Enter`，保存并退出 Vim 编辑器
	
	![Linux 命令行基本用法-为长命令配置别名-3](images/Linux%20命令行基本用法-为长命令配置别名-3.png)
	
6. 输入以下指令使配置文件生效
	```bash
	source ~/.bashrc
	```

---

## 贡献

欢迎提交 Issue 或 Pull Request 来完善本指南！

