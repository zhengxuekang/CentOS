lnmp_install
===================
1.本脚本主要用于lnmp环境自定义参数配置，避免过多人工干预，后期可用于saltstack以及ansibel的批量安装等;<br>  
2.脚本中变量mysql_password可以自己定义，config下的.dbp密码也要与mysql_password值是一样的；mysql_port可以自已定义，其他变量基本与路径相关，这块不建议修改，后面配置文件也会引用到，如果要修改，建议把脚本逻辑看清楚再修改，Mem变量值可根据系统内存值自定义，后面my.cnf一些优化项会根据Mem值进行判断，此外，init.d下拷贝过去的关于mysql操作的脚本检查，开启，关闭都可直接执行;<br>
<br>
3.nginx这块没有太多可以说的，主要是脚本中预配置了一个虚拟主机，端口使用81，文件根目录放在/data/html下，这块根据实际情况可做调整;<br>  
4.php提供了两个安装包，一个是7.2.1，一个是5.6，php_version可在这两个版本间挑一个，只修改这里，后面无须做其他调整，另外，php-fpm服务采用socket形式，启动php-fpm是看不到端口的，这个不是报错，在nginx虚拟主机配置中有写到这个，后面可根据该配置进行主机配置;<br>  
5.因为脚本执行时间较长，为防止中途断开连接，在执行脚本前可使用screen新建一个控制终端，格式screen -S 名字(如lnmp_install)，在执行脚本，这样即使断网操作也不会中断，安装过程会保存在当前路径下的screenlog.0文件中，如果有报错可到改文件中查看；<br>  
6.上面修改好后直接执行main.sh脚本即可。