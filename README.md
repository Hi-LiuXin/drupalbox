# [drupalbox](http://www.drupalbox.org) 　[下载](https://pan.baidu.com/s/1hsfYFvI#list/path=%2F)

Drupalbox做了哪些事情：  
1. 安装oneinstack  
2. 调整php.ini 注释diable_function  
3. 修改etc-opcache.ini 调整opcache.save_comments=1  
4. 调整nginx php /vagrant目录 用户与用户组为vagrant，从而避免drupal安装模块时的ftp权限问题 
5. 安装drush (phar方式安装)  
6. 安装drupal console（phar方式安装）  
7. 安装composer  
8. 添加drupal8网站配置实例 usr/local/nginx/conf/vhost/  drupal8demo.com.conf  
9. 调整mysql外网登录权限和centos防火墙配置，让你可以在虚拟机外通过mysql客户端连接mysql 

**# 注意：已经做好的网站上传到drupalbox要把sites目录极其所有子目录和文件的权限设置为777，settings.php除外（设为555） #**



组件(drupalbox1.1)：  
1. centos 7.2  
2. oneinstack  
3. nginx 1.10.2  
4. php 7.1  
5. opcode  
6. redis  
7. memcached  
8. phpmyadmin  
9. mariadb 10.1  
10. drush 8.1.8  
11. drupal console 1.0.0-rc11 





账户：  
- Centos------》用户名：root 密码：vagrant  
- mysql-------》用户名：root 密码：vagrant  

oneinstack控制目录：/oninstack  

服务管理  
nginx: `sudo service nginx {start|stop|status|restart|reload|configtest}`  
php:   `sudo service mysqld {start|stop|restart|reload|status}`  
mysql: `sudo service php-fpm {start|stop|restart|reload|status}`  

教程： 


1.  下载drupalbox，然后执行`vagrant box add drupalbox1.0 drupalbox1.0.box`
2.  新建文件夹,并打开命令行进入此文件夹
3.  `vagrant box init <name>`
4.  编辑vagrantfile
5.  config.vm.network "private_network", ip: "192.168.88.0-255" 最后一位随便填个数字编辑私有网络，作用是只限主机可以访问   
6.  config.vm.network "public_network", ip: "192.168.31.31" 这个网络配置作用是局域网内其他用户可以访问，其三位是路由器的网段，小米为192.168.31 Dlink为192.168.0 tplink...
7.  创建虚拟主机，并将目录指向 /vagrant/yourwebname 如果你用的drupal8，要按照/usr/local/nginx/conf/vhost/drupal8demo.com.conf修改
8.  然后你就可以在windows或mac本地的这个文件夹下的yourwebname文件夹内建立你的网站，并可以用本地windows或mac的IDE去编辑
9.  drupal console1.0相较于老版本使用略有不同，需要进入网站根目录执行composer require drupal/console:~1.0 --prefer-dist --optimize-autoloader，并且速度比老版本满了很多，受不了其速度的，可以将其卸载并装老版本（不推荐这样做）


