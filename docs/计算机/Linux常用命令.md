# Linux常用命令

### 系统管理

- shutdown -h now：立即关机（shutdown -h 10： 指定10分钟后关机）
- shutdown –r now：重新启动计算机（shutdown -r 13：13分后重启）
- reboot：现在重新启动计算机
- passwd：修改用户密码



- su -：会切换root用户，也会把用户变量也切换到root的环境变量
- su ：只是会切换root用户，但是当前的环境变量还是以前用户的环境变量

### 日常操作

- history：显示在终端中所执行过的所有命令的历史（Ctrl+R查找历史命令）
- history -c：清除所有使用过的命令



- Ctrl+K：删除此处至末尾所有内容
- Ctrl+U：删除此处(此处会保留)至开始所有内容



- Ctrl+C：发送信号给前台进程组中的所有进程，强制终止程序的执行
- Ctrl+Z: 发送信号给前台进程组中的所有进程，暂停一个程序，可以使用jobs/fg/bg操作恢复执行前台或后台的进程
- jobs：展示目前正在运行的程序和编号
- fg+编号（fg 1）命令在前台恢复执行被挂起的进程，此时可以使用Ctrl+Z再次挂起该进程
- bg+编号命令在后台恢复执行被挂起的进程，此时将无法使用Ctrl+Z再次挂起该进程
- Ctrl+D：一个特殊的二进制值，表示 EOF，作用相当于在终端中输入exit后回车



- Ctrl+S 中断控制台输出
- Ctrl+Q 恢复控制台输出
- Ctrl+L 清屏（输入clear也能清屏）



- ls(list files/List Directtory Contents)：显示指定工作目录下的内容（列出目前工作目录所含文件及子目录)
- ls -a：显示所有文件及目录(.开头的隐藏文件也会列出)
- ls -l：除文件名称外，亦将文件型态、权限、拥有者、文件大小等资讯详细(long listing fashion)列出
- ls -r：将文件以相反次序显示(原定依英文字母次序)

> 注意：在Linux中，文件以“.”开头就是隐藏文件，并且每个文件，文件夹，设备或者命令都是以文件对待

- lsblk：列出块设备。除了RAM外，以标准的树状输出格式，整齐地显示块设备
- lsblk -l：命令以列表格式显示块设备(而不是树状格式)

> 注意：lsblk是最有用和最简单的方式来了解新插入的USB设备的名字，特别是当你在终端上处理磁盘/块设备时

- uname(Unix Name的简写)：显示机器名，操作系统和内核的详细信息（uname显示内核类别）
- uname -a：显示详细信息



- sudo(super userdo)：命令允许授权用户执行超级用户或者其它用户的命令。通过在sudoers列表的安全策略来指定

> 注意：sudo允许用户借用超级用户的权限，然而"su"命令实际上是允许用户以超级用户登录，所以sudo比su更安全。
>
> 并不建议使用sudo或者su来处理日常用途，因为它可能导致严重的错误如果你意外的做错了事。

- cal：显示当前年月日(cal 2000：显示2000年日历)
- who：命令用于显示系统中有哪些使用者正在上面，显示的资料包含了使用者 ID、使用的终端机、从哪边连上来的、上线时间、呆滞时间、CPU 使用量、动作等等



- lsmod（英文全拼：list modules）命令用于显示已载入系统的模块

  lsmod | grep bbr：查找bbr模块信息



- cd：进入个人的主目录
- cd -： 返回上次所在的目录
- cd ..：返回上一级目录
- cd ../..：返回上两级目录



- pwd（英文全拼：print work directory） 命令显示工作路径



- mv dir1 new_dir：重命名/移动 一个目录/文件

  mv 123.log test：如果当前目录下有test目录，将会把文件移至test目录中；如果没有则把123.log >变更为> test

  mv 123.log abc.log：123.log 更名为 abc.log



- cp file1 file2：复制一个文件
- cp -a dir1 dir2：复制一个目录



- [ln](https://www.runoob.com/linux/linux-comm-ln.html) -s file1 lnk1： 创建一个(lnk1)指向(file1)文件或目录的软链接

  ln dir1 lnk2：提示不允许将硬链接指向目录

  文件可以创建硬链接

### 文件管理

- mkdir -p 文件夹名：-p 确保目录名称存在，不存在的就建一个（mkdir -p halo123/test：本例若不加 -p 参数，且原本 halo123 目录不存在，则产生错误）
- mkdir dir1 dir2：同时创建两个目录
- rmdir：删除目录



- touch a.txt：创建文件

- rm：可删除文件(直接删)，无法删除目录

  rm 123 提示
  rm: cannot remove '123': Is a directory

  rm -r 123：可以删除目录（-r 将目录及里面的文件、目录逐一删除）

  

  rm -i 123.txt：-i 删除前逐一询问确认
  rm: remove regular empty file '123.txt'? y

  

  rm -f file1：删除一个叫做 ‘file1’ 的文件（即使原档案属性设为唯读，直接删除，无需逐一确认）

- [more](https://www.runoob.com/linux/linux-comm-more.html) file1：显示文件内容，带分页

- 与more类似的命令还有[less](https://www.runoob.com/linux/linux-comm-less.html) [cat](https://www.runoob.com/linux/linux-comm-cat.html)

  cat file1：从第一个字节开始正向查看文件的内容

  tac file1：从最后一行开始反向查看一个文件的内容

- [head](https://www.runoob.com/linux/linux-comm-head.html) -2 file1：查看一个文件的前两行

- grep：命令用于查找文件里符合条件的字符串，如输入 “grep -n "我是谁" 123.txt” 输出结果为所在行数和查询内容 “161:我是谁”

  系统报警显示了时间，但是日志文件太大无法直接 cat 查看。(查询含有特定文本的文件，并拿到这些文本所在的行)，解决：

  grep -n '2019-10-24 00:01:11' *.log

- [find](https://www.runoob.com/linux/linux-comm-find.html) ：命令用来在指定目录下查找文件

  find . -name "*.txt"：将当前目录及其子目录下所有文件后缀为 .txt 的文件列出来

  find . -type f：将当前目录及其子目录中所有一般文件列出



- tail 命令可用于查看文件的内容，有一个常用的参数 -f 常用于查阅正在改变的日志文件（持续跟踪）

  tail -f filename：把 filename 文件里的最尾部的内容显示在屏幕上，并且不断刷新，只要 filename 更新就可以看到最新的文件内容（命令开始时默认最后十行）

  要显示 notes.log 文件的最后 10 行，输入命令：

  tail notes.log   # 默认显示最后 10 行

  tail -2 file1：查看一个文件的最后两行



- [dump](https://www.runoob.com/linux/linux-comm-dump.html) 命令用于备份文件系统

- [init](https://baike.baidu.com/item/init/1196449?fr=aladdin)

  #0 停机（千万不能把 initdefault 设置为0）

  #1 单用户模式

  #2 多用户，没有 NFS (没有网络服务) （和级别3相似，会停止部分服务）

  #3 完全多用户模式 (有网络服务) (标准的运行级)

  #4 没有用到 (系统未使用保留给用户)

  #5 x11(Xwindow)（图形界面）

  #6 重新启动（千万不要把 initdefault 设置为6）

- [Shell echo命令](https://www.runoob.com/linux/linux-shell-echo.html)

  **echo 写入的内容 > filename： 覆盖原本文件的内容**

  **echo 写入的内容 >> filename：在原内容追加行**

### Linux 系统目录结构

- [Linux系统目录结构](https://www.runoob.com/linux/linux-system-contents.html)
