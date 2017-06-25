# Mac OSX下的nano编辑器设置


## 前言
**工欲善其事，必先利其器。Nano是一个很小巧的编辑器，对于码文字编程序很方便。但是Mac OSX里自带版本较低，各种提示功能比如语法提示等默认没有开启。也没有sample配置文件，无法直接修改。今天我google了半天才配置好，拿出来分享下，也许有人也用的上。**


## Nano的版本升级:

**mac上的nano是2.0.6版。最新版可在官方下载：http://www.nano-editor.org/download.php**

- 下载.tar.gz压缩包，那么下载完后，打开终端，进入下载文件目录下运行
`tar -xzvf nano-2.8.4.tar.gz`

- 进入nano-2.8.4目录运行, 依次执行以下命令安装最新版的nano
    1. `./configure`
    2. `make`
    3. `sudo make install`

- 把软件路径放进PATH里
    1. 查看当前PATH配置
        `echo $PATH`
    2. 如果当前配置不包含 /usr/local/bin, 进行添加
        `export PATH=/usr/local/bin:$PATH`

- 查看当前nano版本,可以运行
`nano -V`

## Nano的配置
nano在启动时会读入文件~/.nanorc里的设置，所以可以通过修改这个文件里的内容来配置nano
输入
nano ~/.nanorc

如果没有这个文件，会自动创建

a.) 各种参数设置
nano 自带了很多参数，一般通过set xxxx或者unset xxxx的内容来开启或关闭
参数列表参考：http://www.nano-editor.org/dist/v2.1/nanorc.5.html
比如，喜欢nano编辑界面一直指示当前光标位置，可以在文件里写入
set const
(如果要关闭写入 unset const)

保存后退出

b.）开启语法提示
对于编程，这个用处最大。
首先创建一个文件夹来放置语法文件，供nano调用
mkdir /usr/share/nano

然后去http://code.google.com/p/nanosyntax/source/browse/trunk/syntax-nanorc/ 这里，可以下载别人配置好的各种语法。
比如我在学c,那找到c-file.nanorc文件，点进去后是一堆别人写好的语法定义。
在刚创建的文件夹里，创建文件
nano /usr/share/nano/c-file.nanorc

复制粘贴进去网上的c-file.nanorc里的内容，调整下格式，和原格式一样（注意不能出现额外的断行）。保存退出。

接下修改nanorc文件，以调用刚刚创建的c-file.nanorc里的语法
nano ~/.nanorc

加入一行
include "/usr/share/nano/c-file.nanorc"

保存后退出

同样操作可以更多别人定义好的语法规则。

## 补充

**可以用nano编辑以下文件**

- ~/.profile(个人配置)
        `nano ~/.profile`

- /private/etc/profile(系统全局)
        `sudo nano /private/etc/profile`


