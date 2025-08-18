# Linux 文档

## Linux 命令行基本用法

>适用于 Bash 环境的 Linux 命令行基础使用指南

### 终端基本操作

- 改变命令行字体大小：按住`Ctrl`,上下滑动鼠标滚轮
- 清屏：`clear`
- 复制：使用光标选中需要复制的内容即可 ^quote-of-copy
- 粘贴：滚轮中键或右键

---

### 目录管理

- `cd`：**c**hange **d**irectory 切换目录
	- `cd`：回到默认目录
	- `cd ..`：回到上一目录
- `ls`：**l**i**s**t directory 显示当前目录下文件
	- `ls -l`：显示当前目录下文件的**详细信息**
	- `ls -al`：显示当前目录下所有文件（包括**隐藏文件**）的**详细信息**
- `pwd`：**p**rint **w**orking **d**irectory 显示当前所在的目录

---

### 文件管理

- `touch`：新建文件
	- 例：`touch gitcode.txt` 新建一个名为`gitcode.txt`的文本文档
- `cat`：🐱**c**onc**a**tena**t**e 查看文件内容
	- 例：`cat gitcode.txt` 将`gitcode.txt`中的内容打印到屏幕
- `mkdir`：**m**a**k**e **dir**ectory 新建文件夹
	- 例：`mkdir git` 在当前目录下新建一个名为`git`的文件夹
- `rm`：**r**e**m**ove 删除文件
	- 例：`rm gitcode.txt` 删除名为`gitcode.txt`的文本文档
	- 例：`rm -r git` 删除名为`git`的文件夹（ ⚠ **警告**：`rm -r` 会永久删除文件夹，不会进入回收站，操作前请确认）
- `mv`：**m**o**v**e 移动/重命名文件
	- 例：`mv gitcode.txt git/` 将`gitcode.txt`移动至`git`文件夹下
	- 例：`mv gitcode.txt git.txt` 将`gitcode.txt`重命名为`git.txt`（因为`git.txt`原本不存在，所以起到的是重命名功能）
- `cp`：**c**o**p**y 复制文件
	- 例：`cp gitcode.txt backup/` 将`gitcode.txt`文件复制到`backup`文件夹下

---

### 为长命令配置别名

1. 创建 Bash 配置文件（如果之前已经创建，请忽略该步骤）
	```bash
	touch ~/.bashrc
	```
2. 使用 Vim 编辑器编辑配置文件
	```bash
	vim ~/.bashrc
	```
	
	![[Linux 命令行基本用法-为长命令配置别名-1.png|500]]
	
3. 按一下键盘上的`i`进入编辑模式
	
	![[Linux 命令行基本用法-为长命令配置别名-2.png|500]]
	
4. 输入以下内容设置别名（请将`<shortcommand>`替换为需要设置的别名，别名可以根据个人的喜好确定，请将`<longcommand>`替换为需要设置别名的命令）
	```
	alias <shortcommand>='<longcommand>'
	```
5. 按下`Esc`键退出编辑模式，直接输入`：wq`并按回车键`Enter`，保存并退出 Vim 编辑器
	
	![[Linux 命令行基本用法-为长命令配置别名-3.png|500]]
	
6. 输入以下指令使配置文件生效
	```bash
	source ~/.bashrc
	```

---

