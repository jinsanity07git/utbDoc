# CLI 常用 Linux 命令

## 什么是 Linux 命令？

Linux 命令是在 CLI 上运行的程序或实用程序，也就是一个通过文本和进程与系统交互的控制台。它类似于 Windows 中的命令提示符应用程序。

通过在行尾按`Enter键`在终端上执行 Linux 命令。您可以运行命令来执行各种任务，从安装到用户管理和文件操作。

下面是 Linux 命令的一般语法：

```
CommandName [option(s)] [parameter(s)]
```

一个命令可以包含选项或参数。也可以在没有参数和选项的情况下运行。以下是Linux命令的三个最常见的组成部分：

* `CommandName` ：要执行的命令规则。
* `option(s)`或`flag`：用于标识修改命令操作。要调用它，请使用连字符 ( - ) 或双连字符 ( -- )。
* `Parameter`或`argument`：用于指定命令执行所需的必要信息。

**注意，所有 Linux 命令都区分大小写。**

## CLI 使用技巧

以下是一些常用的CLI提示和技巧：

* 输入`clear`命令以清理终端屏幕。
* 输入带参数的命令后，按`Tab`键自动填充。
* 使用`Ctrl + C`终止正在运行的命令。
* 按`Ctrl + Z`暂停正在运行的命令。
* 使用`Ctrl + S`暂时冻结您的终端。
* 按`Ctrl + Q`撤消终端冻结。
* 使用`Ctrl + A`移至行首。
* 按`Ctrl + E`将您带到行尾。
* 在一行中执行多个命令时，使用 ( ; ) 分隔它们；或者，使用&&只允许在前一个命令成功时运行下一个命令。

## 常用命令

您可以在互联网上搜索查看更多Linux命令使用示例和功能信息，在这里我们仅列出部分常用命令的使用方法、功能选项及参数设置。

### apt-get 命令

apt-get用于安装、管理、更新、和删除软件及其依赖项。

**运行 apt-get 命令需要您使用 sudo 或 root 权限。**

语法如下：

```
apt-get [options] (command)
```

以下是在使用apt-get时最常用的命令：

* `update`：同步更新安装包文件。
* `upgrade`：升级所有已安装软件包到最新版本。
* `check`：更新包缓存并检查损坏的依赖项。

### sudo 命令

sudo是superuser do的缩写，是最流行的基本 Linux 命令之一，可让您执行拥有管理员或 root 权限的任务。

使用 sudo 时，系统会提示用户使用密码进行身份验证。如果您尝试在命令行中运行 sudo 而未对自己进行身份验证，系统会将此记录为安全事件。

如果还未安装sudo命令，则会提示"sudo: command not found"的错误信息，可以输入以下命令安装sudo：

```
apt-get install sudo
```

以下是sudo命令的一般语法：

```
sudo (command)
```

可以在命令中添加选项，例如：

* `-k` 或 `–reset-timestamp`： 使时间戳文件无效。
* `-g` 或 `–group=group`： 以指定的组名或ID运行命令。
* `-h` 或 `–host=host`： 在主机上运行命令。

### pwd 命令

使用 pwd 命令查找当前工作目录的路径。只需输入 pwd 即可返回完整的当前路径，即以正斜杠 ( / ) 开头的所有目录的路径。例如，/home/用户名。

pwd命令使用以下语法：

```
pwd [option]
```

该命令有两个可接受的选项：

* `-L` 或 `–logical`：打印环境变量内容，包括符号链接。
* `-P` 或 `–physical`：打印当前目录的实际路径。

### cd 命令

要浏览OS文件和目录，请使用 cd 命令。根据您所在的当前工作目录，cd命令需要完整路径或目录名称。

在没有任何选项的情况下运行cd命令，将进入到到home文件夹。注意，只有具有sudo权限的用户才能执行。

例如，您在/uos/myfiles/documents中，想跳转到documents的子目录photos。只需要输入以下命令回车即可：

```
cd photos
```

如果你想切换到一个全新的目录，例如/uos/myfiles/movies，则必须在cd命令后输入目录的绝对路径：

```
cd /uos/myfiles/movies
```

以下是一些使用cd命令的快捷方式：

* `cd ~[username]`：转到另一个用户的home目录。
* `cd ..`：进入上一级目录。
* `cd-`：进入之前访问的目录。

### ls 命令

ls 命令用于列出系统中的文件和目录。**在没有参数的情况下，运行ls命令会显示当前工作目录的内容。**

要查看其他目录的内容，请键入ls和所需的路径。例如，要查看/uos/myfiles/documents文件夹中的文件，请输入：

```
ls /uos/myfiles/documents
```

以下是一些与ls命令一起使用的选项：

* `ls -R`：列出子目录中的所有文件。
* `ls -a`：除了可见文件外，还显示隐藏文件。
* `ls -lh`：以易于阅读的格式显示文件大小，例如 MB、GB 和 TB。

### cat 命令

Concatenate 或 cat 是最常用的 Linux 命令之一。它列出、合并文件内容并将其写入标准输出。要运行 cat 命令，请键入cat，后跟文件名及其扩展名。例如：

```
cat filename.txt
```

以下是一些使用 cat 命令的例子：

* `cat > filename.txt`：创建一个新文件。
* `cat filename1.txt filename2.txt > filename3.txt`：合并 filename1.txt 和 filename2.txt 并将输出存储在 filename3.txt 中。
* `tac filename.txt`：以相反的顺序显示内容。

### cp 命令

cp 命令用于复制文件或目录及其内容。请查看以下用例：

例1：将一个文件从当前目录复制到另一个目录，请输入cp，后跟文件名和目标目录。如：

```
cp filename.txt /uos/myfiles/documents
```

例2：复制多个文件，请输入文件名，然后输入目标目录。如：

```
cp filename1.txt filename2.txt filename3.txt /uos/myfiles/documents
```

例3：将文件的内容复制到同一目录中的新文件，请输入cp ，然后输入源文件和目标文件名。如：

```
cp filename1.txt filename2.txt
```

例4：要复制整个目录，请在键入源目录之前传递`-R`标志，然后输入目标目录。如：

```
cp -R /uos/myfiles/documents /uos/myfiles/documents_backup
```

### mv 命令

mv 命令的主要用途是移动和重命名文件和目录，它不会在执行时产生输出。

只需键入mv，后跟文件名和目标目录。例如，想将filename.txt移动到/uos/myfiles/documents 目录，可使用下面的命令：

```
mv filename.txt /uos/myfiles/documents
```

也可以使用mv命令重命名文件，如：

```
mv old_filename.txt new_filename.txt
```

### mkdir 命令

使用 mkdir 命令创建一个或多个目录并为每个目录设置权限。执行此命令的用户必须具有在父目录中创建新文件夹的权限，否则会收到权限被拒绝的错误。

基本语法如下：

```
mkdir [option] directory_name
```

例如，在当前路径下创建一个名为music的目录，可以键入下面命令：

```
mkdir music
```

要在music中创建一个名为songs的新目录，可使用以下命令：

```
mkdir music/songs
```

mkdir命令可以接受许多选项，例如：

* `-p`或`–parents`：在两个现有文件夹之间创建一个目录。例如，`mkdir -p music/2020/songs`在Music和Songs间创建新的名为 2020 的目录。
* `-m`：设置文件权限。例如，要为所有用户创建一个具有完全读取、写入和执行权限的目录，可输入`mkdir -m777 directory_name`。
* `-v`：为每个创建的目录打印一条消息。

### rmdir 命令

要永久删除空目录，可使用 rmdir 命令。注意，运行此命令的用户应该在父目录中具有sudo权限。

例如，想删除一个名为 personal 的空子目录及其主文件夹mydir，可键入：

```
rmdir -p mydir/personal
```

### rm 命令

rm 命令用于删除目录中的文件，应确保执行此命令的用户具有写入权限。

**请确认目录的位置，因为删除文件后无法撤消。**

基本语法如下：

```
rm filename
```

如要删除多个文件，可输入以下命令：

```
rm filename1 filename2 filename3
```

rm命令可接受以下选项：

* `-i`：在删除文件之前提示系统确认。
* `-f`：允许系统在没有确认的情况下删除。
* `-r`：递归删除文件和目录。

### man 命令

man 命令提供了可以在终端中运行的任何命令或实用程序的用户手册，包括名称、描述和选项。由九个部分组成：

* 可执行程序或 shell 命令
* 系统调用
* 库调用
* 游戏
* 特殊文件
* 文件格式和约定
* 系统管理命令
* 内核例程
* 其他类型信息

要显示完整的手册，请输入：

```
man [command_name]
```

例如，想要访问ls命令的手册，可输入：

```
man ls
```

### touch 命令

touch 命令用于创建一个空文件或生成和修改时间戳。

例如，输入以下命令，可以在documents目录中创建一个名为new的 HTML 文件：

```
touch /uos/myfiles/documents/new.html
```

### locate 命令

locate 命令可以在数据库系统中找到一个文件。

此外，添加`-i`参数将关闭区分大小写，即使不记得文件的确切名称也可以搜索文件。

要查找包含两个或更多单词的内容，请使用星号 ( * )。

例如：

```
locate -i apple*orange
```

该命令将搜索包含单词apple和orange的文件，无论它们使用大写还是小写字母。

### find 命令

使用find命令在特定目录下搜索文件并执行后续操作。

语法如下：

```
find [option] [path] [expression]
```

例如，想要在home及其子文件夹中查找名为notes.txt的文件：

```
find /home -name notes.txt
```

其他使用find命令的例子：

* `find -name filename.txt` ：在当前目录中查找文件filename.txt。
* `find ./ -type d -name directoryname`：来查找目录。

### df 命令

使用 df 命令报告系统的磁盘空间使用情况，以百分比和千字节 (KB) 显示。

语法如下：

```
df [options] [file]
```

例如，查看当前目录的系统磁盘空间使用情况，可以输入以下命令：

```
df -h
```

还有一些可接受的使用选项：

* `df -m`：以MB为单位显示文件系统使用情况。
* `df -k`：以KB为单位显示文件系统使用情况。
* `df -T`：在新列中显示文件系统类型。

### du 命令

如果要检查文件或目录占用了多少空间，可以使用du命令。

**注意，使用du命令时必须指定目录路径。例如，要检查/uos/myfiles/documents，请输入：

```
du /uos/myfiles/documents
```

以下flag标志可与 du 命令配合使用，如：

* `-s`：提供指定文件夹的总大小。
* `-m`：以MB为单位提供文件夹和文件信息
* `-k`：以KB为单位显示信息。
* `-h`：通知显示的文件夹和文件的最后修改日期。

### head 与 tail 命令

head命令用来查看文本的前十行。添加选项可更改显示的行数。head命令还可用于将管道数据输出到CLI。

语法如下：

```
head [option] [file]
```

tail 命令显示文件的最后十行，可用于检查文件是否有新数据或读取错误消息。

语法如下：

```
tail [option] [file]
```

### diff 命令

diff命令用于逐行比较两个文件的内容。分析完后，会显示不匹配的部分。

语法如下：

```
diff [option] file1 file2
```

例如，想要比较两个文本文件 note.txt 和 note_update.txt，可输入：

```
diff note.txt note_update.txt
```

以下是一些可使用的添加选项：

* `-c`：以上下文形式显示两个文件之间的差异。
* `-u`：显示没有冗余信息的输出。
* `-i`：使diff命令不区分大小写。

### tar 命令

tar 命令将多个文件归档到一个TAR文件中，TAR是一种类似于ZIP的常见 Linux 格式，具有可选的压缩功能。

语法如下：

```
tar [options] [archive_file] [file or directory to be archived]
```

例如，在当前目录下创建一个名为newarchive.tar的新TAR文件，包含 /var/log 目录下的全部文件，可输入：

```
tar -cvf newarchive.tar /var/log
```

tar命令接受许多选项，如：

* `-x`：提取TAR文件包含的内容。
* `-t`：列出TAR文件包含的内容。

### zip 与 unzip 命令

使用zip命令将文件压缩成 ZIP 文件，可以自动选择最佳压缩率。

语法如下：

```
zip [options] zipfile file1 file2...
```

例如，想将一个名为note.txt的文件压缩为当前目录中的 archive.zip，可输入命令：

```
zip archive.zip note.txt
```

另一方面，unzip命令从存档中提取压缩文件。语法如下：

```
unzip [options] file_name.zip
```

例如，要在当前目录中解压一个名为 archive.zip 的文件，请输入：

```
unzip archive.zip
```

### jobs 命令

jobs 是 shell 启动的进程。jobs命令显示所有正在运行的进程及其状态。注意，此命令仅在csh、bash、tcsh 和 ksh shell 中可用。

语法如下：

```
jobs [options] jobID
```

要检查当前 shell 中的所有进程状态，只需在 CLI 中输入 jobs 即可。

以下是您可以使用的一些选项：

* `-l`：列出进程 ID 及其信息。
* `-n`：列出自上次通知以来状态已更改的进程。
* `-p`：仅列出进程 ID。

### kill 命令

使用 kill 命令手动终止无响应的程序进程。

要终止一个程序进程，需要知道它的进程标识号 (PID)。如果您不知道 PID，请运行以下命令：

```
ps ux
```

获得程序进程的 PID 后，输入以下命令：

```
kill [signal_option] PID
```

signal_option包含64种signals，但这两种signals是最常用的：

* SIGTERM 请求进程停止运行并给它一些时间来保存所有进度。如果输入 kill 命令时没有指定signal_option，系统将默认使用 SIGTERM。
* SIGKILL 强制进程停止，将丢失未保存的进度。

例如，进程的 PID 是 63773，想强制关闭它，可输入：

```
kill SIGKILL 63773
```

### ping 命令

ping 命令用于检查网络或服务器是否可达。此外，它还用于解决各种连接问题。

语法如下：

```
ping [options] [hostname or IP_address]
```

例如，您想知道是否可以连接到Baidu并测量其响应时间：

```
ping baidu.com
```

### wget 命令

使用 wget 命令可以从 Internet 下载文件。并在后台工作，不会妨碍其他正在运行的进程。

wget命令使用 HTTP、HTTPS 和 FTP 协议检索文件。它可以执行递归下载，通过遵循目录结构和链接传输网站部分，创建网页的本地版本。

要使用它，请输入以下命令：

```
wget [option] [URL]
```

例如，在当前目录下载最新版本的 WordPress，可输入下面命令：

```
wget https://wordpress.org/latest.zip
```

### top 命令

top 命令将显示所有正在运行的进程和当前系统的动态实时视图，总结从 CPU 到内存使用的资源利用率。

top 命令还可以帮助识别和终止可能使用过多系统资源的进程。

要运行该命令，只需在 CLI 中输入：

```
top 
```

### history 命令

history 命令会列出最多 500 条之前执行过的命令，让您可以重复使用它们而无需重新输入。注意，只有具有sudo权限的用户才能执行此命令。该实用程序的运行方式还取决于您使用的 Linux shell。

语法如下：

```
history [option]
```

### nano 和 vi 命令

通过文本编辑器（例如nano、vi）来编辑和管理文件。

如果您的虚拟环境没有安装nano，可使用下面命令安装：

```
sudo apt-get -y install nano
```
例如，使用 nano 或者 vi 来编辑文件 main.py，可输入以下命令：

```
nano main.py
```
或者

```
vi main.py
```

### ps 命令

ps命令生成系统中所有正在运行的进程的快照，只需在 CLI 输入：

```
ps
```

执行ps命令将列出 shell 中正在运行的进程以及：

* 进程 ID ( PID )
* 终端类型（TTY）
* 运行时间 ( TIME )
* 启动进程的命令 ( CMD )



