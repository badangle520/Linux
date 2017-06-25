# oh-my-zsh 中文乱码

## 环境
电脑硬件  macbook pro
系统语言  英文

## 
在Mac下一直都采用iTerm+oh-my-zsh作为终端环境。oh-my-zsh是个很强大的shell。不过默认却对中文支持不好，ls查看中文目录会显示乱码。 google了下原因，发现是因为locale没有设置为utf-8.果然在终端中输入locale发现所有对应的值都为空。所以只要设置一下locale就好了。 zsh代替了bash，所以bash的配置文件都不管用了，修改.bash_profile或.bashrc都不起作用的。所以需要修改.zshrc。 

## 解决方案
1. 备份~/.zshrc原始文件
`cp ~/.zshrc ~/.zshrc_bak`

2. 终端输入一下命令进入编辑器，编辑~/.zshrc
`nano ~/.zshrc`

3. 文件内容末端添加：

 ```
 export LC_ALL=en_US.UTF-8  
 export LANG=en_US.UTF-8
 ```

4. 生效~/.zshrc（以下两种任选其一）
    - source ~/.zshrc
    - 重启终端
  



