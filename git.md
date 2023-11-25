### git

创建分支

```
git checkout -b gh-pages
```

切换分支

```
git  checkout master
```

重命名master分支

```
git branch -m 原分支名 新分支名
```

初始化仓库

```
git init
```

添加文件到暂存区

```
git add .
```

将暂存区内容添加到仓库中

```
git commit 
```

连接远端仓库

```
git remote add origin https://github.com/yeshp-gw/gitbook.git
```

本地推送到远端

```
git push -u origin master
```

------

### gitbook部署在VPS

```
cd /var/www/html/     
```

```
mkdir gitbook
```

```
cd gitbook          
```

```
git init             ## 不能报错
git remote add origin "githu链接"      ##不能报错
git pull origin gh-pages                ##拉取html
```

```
vim /etc/nginx/sites-available/default    ##设置nginx
```

```
root  /var/www/html/gitbook；   ## html后面添加gitbook
```

------

### nginx

```
systemctl status nginx.service     ## 运行状态
nginx -v       ##版本号
```

```
systemctl start nginx     ##启动
systemctl stop nginx      ##停止
systemctl reload nginx    ##重载
```

```
netstat -tnlp          ##端口号占用
ps –ef | grep nginx    ## 查看进程
kill -9 pid            ##杀死进程
```

