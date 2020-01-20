## shell配置文件的加载

### 一、登录式的 Shell

1. 首先会读取和执行/etc/profiles，这是所有用户的全局配置文件
2. 接着会到用户主目录中寻找 “~/.bash_profile”， “~/.bash_login” 或者 “~/.profile”，它们都是用户个人的配置文件
3. 如果 ~/.bash_profile 文件存在，那么一切以该文件为准，并且到此结束，不再加载其他的配置文件
4. 接着加载 ~/.bash_login，同上
5. 接着加载 ~/.profile

> 注意，/etc/profiles 文件还会嵌套加载 /etc/profile.d/*.sh

### 二、非登录的 Shell

1.以非登的方式启动Shell，那么就不会读取以上所说的的配置文件，而是直接读取 ~/.bashrc

> 注意，~/.bashrc 文件还会嵌套加载 /etc/bashrc