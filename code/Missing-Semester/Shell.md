## 使用Shell
``` shell
missing:~$ echo hello
hello
```
上例中，我们让 shell 执行 `echo` ，同时指定参数 `hello`。`echo` 程序将该参数打印出来。 shell 基于空格分割命令并进行解析，然后执行第一个单词代表的程序，并将后续的单词作为程序可以访问的参数。如果您希望传递的参数中包含空格（例如一个名为 My Photos 的文件夹），您要么用使用单引号，双引号将其包裹起来，要么使用转义符号 `\` 进行处理（`My\ Photos`）。

Shell是怎么找到echo或date的？
echo和date都是环境变量$PATH中的程序，Shell会在这里找到echo和date。
```shell
missing:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
missing:~$ which echo
/bin/echo
missing:~$ /bin/echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
```


## Shell的导航
路径 `/` 代表的是系统的根目录，所有的文件夹都包括在这个路径之下。如果某个路径以 `/` 开头，那么它是一个 _绝对路径_，其他的都是 _相对路径_ 。`.`代表的是当前目录，`..`代表的是上一级目录。

大多数的命令接受标记和选项（带有值的标记），它们以 `-` 开头，并可以改变程序的行为。
```shell
missing:~$ ls -l /home
drwxr-xr-x 1 missing  users  4096 Jun 15  2019 missing
```
这个参数可以更加详细地列出目录下文件或文件夹的信息。首先，本行第一个字符 `d` 表示 `missing` 是一个目录。然后接下来的九个字符，每三个字符构成一组。 （`rwx`）. 它们分别代表了文件所有者（`missing`），用户组（`users`） 以及其他所有人具有的权限。其中 `-` 表示该用户不具备相应的权限。从上面的信息来看，只有文件所有者可以修改（`w`），`missing` 文件夹 （例如，添加或删除文件夹中的文件）。为了进入某个文件夹，用户需要具备该文件夹以及其父文件夹的“搜索”权限（以“可执行”：`x`）权限表示。为了列出它的包含的内容，用户必须对该文件夹具备读权限（`r`）。对于文件来说，权限的意义也是类似的。注意，`/bin` 目录下的程序在最后一组，即表示所有人的用户组中，均包含 `x` 权限，也就是说任何人都可以执行这些程序。


## 在程序间创建连接
在 shell 中，程序有两个主要的“流”：它们的输入流和输出流。 当程序尝试读取信息时，它们会从输入流中进行读取，当程序打印信息时，它们会将信息输出到输出流中。 通常，一个程序的输入输出流都是您的终端。也就是，您的键盘作为输入，显示器作为输出。 但是，我们也可以重定向这些流！
最简单的重定向是 `< file` 和 `> file`。这两个命令可以将程序的输入输出流分别重定向到文件：
```shell
missing:~$ echo hello > hello.txt
missing:~$ cat hello.txt
hello
missing:~$ cat < hello.txt
hello
missing:~$ cat < hello.txt > hello2.txt
missing:~$ cat hello2.txt
hello
```
关于`cat < hello.txt > hello2.txt`，我的理解是，任何一个程序都有输入流和输出流，默认输入流为键盘，当使用`< hello.txt`时将输入流重定向为文件`hello.txt`。但是如果给`cat`传输一个文件参数，则会抛弃输入流，专注于打印给定的文件参数，这一点可以通过运行：
```shell
echo < hello.txt hello2.txt
echo hello2.txt < hello.txt
```
来观察到，我们可以看到运行的结果都是`hello2.txt`中的内容，这表明`echo`应该是默认不使用输入流的，只有当没有给定参数时，才会请求使用输入流。
为了验证这一点我还使用了以下命令：
```shell
echo hello.txt hello2.txt > hello3.txt
echo < hello.txt hello2.txt > hello3.txt
echo > hello3.txt
```
结果是第一行里会有两个文件的内容，第二行里`hello3.txt`中只会有`hello2.txt`的内容，第三行里命令会请求用户用键盘输入。

> [!NOTE] 
> 感觉是一种很牛逼的程序设计哲学
> 
> 对于`echo`这种不用输入流的程序，以上无效


还可以使用 `>>` 来向一个文件追加内容。使用管道（ _pipes_ ），我们能够更好的利用文件重定向。 `|` 操作符允许我们将一个程序的输出和另外一个程序的输入连接起来：
```shell
missing:~$ ls -l / | tail -n1
drwxr-xr-x 1 root  root  4096 Jun 20  2019 var
missing:~$ curl --head --silent google.com | grep --ignore-case content-length | cut --delimiter=' ' -f2
219
```


## 一个功能全面又强大的工具
有一件事情是您必须作为根用户才能做的，那就是向 `sysfs` 文件写入内容。系统被挂载在 `/sys` 下，`sysfs` 文件则暴露了一些内核（kernel）参数。 因此，您不需要借助任何专用的工具，就可以轻松地在运行期间配置系统内核。**注意 Windows 和 macOS 没有这个文件**

通过将数值写入`brightness`文件，我们可以改变屏幕的亮度。现在，蹦到您脑袋里的第一个想法可能是：
```sheel
$ sudo find -L /sys/class/backlight -maxdepth 2 -name '*brightness*'
/sys/class/backlight/thinkpad_screen/brightness
$ cd /sys/class/backlight/thinkpad_screen
$ sudo echo 3 > brightness
An error occurred while redirecting file 'brightness'
open: Permission denied
```
出乎意料的是，我们还是得到了一个错误信息。毕竟，我们已经使用了 `sudo` 命令！关于 shell，有件事我们必须要知道。`|`、`>`、和 `<` 是通过 shell 执行的，而不是被各个程序单独执行。 `echo` 等程序并不知道 `|` 的存在，它们只知道从自己的输入输出流中进行读写。 对于上面这种情况， _shell_ (权限为您的当前用户) 在设置 `sudo echo` 前尝试打开 brightness 文件并写入，但是系统拒绝了 shell 的操作因为此时 shell 不是根用户。

明白这一点后，我们可以这样操作：
```sheel
$ echo 3 | sudo tee brightness
```
因为打开 `/sys` 文件的是 `tee` 这个程序，并且该程序以 `root` 权限在运行，因此操作可以进行。 这样您就可以在 `/sys` 中愉快地玩耍了，例如修改系统中各种LED的状态（路径可能会有所不同）：
```sheel
$ echo 1 | sudo tee /sys/class/leds/input6::scrolllock/brightness
```


## Shell脚本
