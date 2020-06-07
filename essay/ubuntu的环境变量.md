# ubuntu的环境变量

最近我经常用redis数据库的作业,我是按照[educoder](https://www.educoder.net/tasks/3wtem9p5iyhv)的办法安装的`redis`，然后每次用redis都需要 ` cd redis-5.0.0/ `然后才能使用那些命令(启动服务器等)。

而且经常不仅仅开一个terminal窗口（每次使用都至少要开一个` redis-server ` 和 ` redis-cli `），每次都要cd是很烦人的一件事情，于是我去搜索了关于ubuntu添加环境变量的教程，下面是一种我认为简单有效的方式，做好之后以后直接开启terminal之后不需要cd，即可直接使用命令。

```sh
#通过修改.bashrc文件:
vim ~/.bashrc 
#在最后一行添上：
export PATH=/usr/local/bin:$PATH
# 比如我要添加 /mnt/c/Users/kasusa/redis-5.0.0 这个目录
# 就写 export PATH=/usr/local/bin:/mnt/c/Users/kasusa/redis-5.0.0
```

* 生效方法：（有以下两种）
  * 1、关闭当前终端窗口，重新打开一个新终端窗口就能生效
  * 2、输入“source ~/.bashrc”命令，立即生效
* 有效期限：永久有效
* 用户局限：仅对当前用户

 后来出现了一个问题,就是我要用系统命令的时候(比如vim),它告诉我不能找到vim,因为它发现 `/usr/bin` 不在环境变量里面

 解决方法就是在刚刚加入的那行后面再加入一行

```sh
export PATH=/usr/local/bin:/mnt/c/Users/kasusa/redis-5.0.0
export PATH=/bin:/usr/bin
```
