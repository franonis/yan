0、查看php及php扩展
yum install php
yum install openssl-devel
yum install php-pdo
yum install php-gd
yum install php-devel
yum install php-mbstring
yum install php-fpm
yum install php-mcrypt
yum install php-mysql
yum install php-xml
yum install php-xmlrpc
yum install 
1、获取源码
git clone
scp
都行
cd /path/to/here/
sudo chmod -R 777 storage bootstrap/cache
php artisan key:generate
2、配置mysql
vi .env
查看database相关设置
安装mysql
#建库
create database databasename #databasename与.env中一致
#建用户
grant all on databasename.* to 'username'@'%' identified by 'passwd';   #username和passwd与.env中一致
#生效
flush privileges;
#数据导入
mysql -uusername -ppasswd databasename <../ooo.sql
3、安装
composer install
(没有composer就yum install composer)
4、网络
安装nginx
yum install nginx
修改配置文件
vi /etc/nginx/nginx.conf
默认是这个路径，也可能不是这个路径，locate nginx.conf找一下
把我们服务器上的拷过去，1、root后面的路径改了，全路径，以public结尾，2、user 改成他们的【这个与后面fpm的一致】
安装php-fpm
yum install php-fpm
修改配置文件，路径不一定
php-fpm.d/www.conf
修改user group，与nginx的user一致
php-fpm -R &保持运行状态
