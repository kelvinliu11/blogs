# CentOS7 yum 安装与配置MySQL5.7
或参考：https://www.cnblogs.com/ianduin/p/7679239.html
## 配置YUM源
+ 下载mysql源安装包
```
shell> wget http://dev.mysql.com/get/mysql57-community-release-el7-8.noarch.rpm
```
+ 安装mysql源
```
shell> yum localinstall mysql57-community-release-el7-8.noarch.rpm
```
+ 检查mysql源是否安装成功
```
shell> yum repolist enabled | grep "mysql.*-community.*"
```
看到下图所示表示安装成功。 
![](img/2019-09-25-09-57-41.png)
## 安装MySQL
```
shell> yum install mysql-community-server
```
## 启动MySQL服务
```
shell> systemctl start mysqld
```
## 开机启动
```
shell> systemctl enable mysqld
shell> systemctl daemon-reload
```
## 修改root本地登录密码
mysql安装完成之后，在/var/log/mysqld.log文件中给root生成了一个默认密码。通过下面的方式找到root默认密码，然后登录mysql进行修改：
```
shell> grep 'temporary password' /var/log/mysqld.log
```
![](img/2019-09-25-09-59-02.png)
```
shell> mysql -u root -p
mysql> ALTER USER 'root'@'localhost' IDENTIFIED BY 'MyNewPass4!'; 
```