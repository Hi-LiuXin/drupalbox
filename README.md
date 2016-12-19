# drupalbox [www.drupalbox.org](http://www.drupalbox.org)
组件：  
1. centos7
2. oneinstack
3. nginx
4. php7
5. opcode
6. redis
7. memcached
8. phpmyadmin
9. mariadb10
10. drush8
11. drupal console1.0.0-rc11





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