
## 一、Linux服务器yum安装（CentOS6.3 64位）


命令安装mysql
    
    yum install mysql mysql-server mysql-devel -y
最后提示 Complete!  表示安装成功

如果没有发现-sql server包

    wget http://repo.mysql.com/mysql-community-release-el7-5.noarch.rpm
    
安装mysql-community-release-el7-5.noarch.rpm包    
    
    rpm -ivh mysql-community-release-el7-5.noarch.rpm
    yum install mysql-server

    
启动mysql

    service mysqld start 
    
重置密码
    
    mysql -u root
    mysql > use mysql;
    mysql > update user set password=password('123456') where user='root';
    mysql > exit;
    
客户端出现Host not allow connect

    update user set host = '%' where user = 'root'; 
    flush privileges; 
