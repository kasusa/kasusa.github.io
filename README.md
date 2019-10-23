# [kasusa.github.io](https://kasusa.github.io/)

参考链接（一些）
[html can do that？](https://dev.to/ananyaneogi/html-can-do-that-c0n)
用了里面的`Expand/collapse details`来做`get a life2`的下拉菜单

## 2019-10-22 21:25
> 今天 kasusa 买了一个阿里云的服务器，因为我很**年轻**，所以价格很便宜！`￥9.5/mon`
> 计划把githubpages部署到真正的服务器上试试手。
> 
> 正在参考 [“在自己的服务器上搭建静态博客”](http://listenerri.com/2019/03/31/%E5%9C%A8%E8%87%AA%E5%B7%B1%E7%9A%84%E6%9C%8D%E5%8A%A1%E5%99%A8%E4%B8%8A%E6%90%AD%E5%BB%BA%E9%9D%99%E6%80%81%E5%8D%9A%E5%AE%A2/) 同时我会把一些真正的好文章复制到我的 `markdown` 文件夹里，因为我担心以后某一天链接就失效了（比如博客主人不续费服务器之类的）……

- [x] 博客
- [ ] awtrix--我的钟表
- [ ] mysql服务器来给我的所有其他作业用！

## 让我的服务器可以拉我的github项目
1. [sshkey](https://blog.csdn.net/Felicity294250051/article/details/53606158)
 > my ssh key 
```
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDcwDFDztBsVsizfVI5E4UctEI3lNKHkmubsxKBsSLoi58ItjzDTutcIvLI60InHr4NEQGs1FNVvRcKzkK/HIV+wv82Hcr1UH3OVEVngIO9ibGqQzhqxK4ALaqK2hG5qJaRkplfMA0jEzjIWdvOie07Hlb2rKu6LC1y9gHKcxgrz24fk/h8HGNzBOvVhFhSnfvIOke4mzNE+VNLDwGTXt2AhrDs447bg3IS6KEo8E42TtqWVWQKeW8xvxve5BS9hRfc0n9NcM2jh0XT8xHDnU0BqU6MOkWhF4r8yjCS7C/e3P5A2khOkwIi4lLzbbzHe+5i9P9J4pjHoBTAY4XtTPjF kasusaland@gmail.com
```
2. 设置好key之后就可以让服务器去pull了
```
git clone git@github.com:kasusa/kasusa.github.io.git  /opt/myBlog
```
3. 编辑 `/etc/nginx/nginx.conf ` 文件 | [关闭nginx](https://www.jianshu.com/p/bff86be37308) | [winSCP download](https://sourceforge.net/projects/winscp/)
```
http {
    server {
        location / {
            #这里是网页的根目录
            root /opt/myBlog; 
        }
    }
}
```
## 更改nginx.conf之后重启nginx：
1. 查询nginx主进程号
```
ps -ef | grep nginx
```
2. 发送信号

```
kill -QUIT 主进程号  （从容停止Nginx：）
```
3. 接下来启动 nginx 服务：
```
service nginx start
# 或者如果系统是 systemd 的：
systemctl start nginx
```