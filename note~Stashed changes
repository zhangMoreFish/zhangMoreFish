1.官网下载社区版 service zip文件
2.解压后修改文件夹下的my.ini中的路径，没有新建，内容如下（修改路径）
[mysqld]
# 设置3306端口
port=3306
# 设置mysql的安装目录
basedir=F:\mysql-8.0.25-winx64
# 设置mysql数据库的数据的存放目录
datadir=F:\mysql-8.0.25-winx64\data
# 允许最大连接数
max_connections=200
# 允许连接失败的次数。这是为了防止有人从该主机试图攻击数据库系统
max_connect_errors=10
# 服务端使用的字符集默认为UTF8
character-set-server=utf8
# 创建新表时将使用的默认存储引擎
default-storage-engine=INNODB
# 默认使用“mysql_native_password”插件认证
default_authentication_plugin=mysql_native_password
[mysql]
# 设置mysql客户端默认字符集
default-character-set=utf8
[client]
# 设置mysql客户端连接服务端时默认使用的端口)th%b8Fxz3Qk
port=3306
default-character-set=utf8
3.管理员身份运行cmd，到mysql的bin目录下
执行命令 mysqld --initialize --console，等待几秒，会输出root账号信息，包括密码，记下用于登陆
4.安装服务，执行命令 mysqld --install
6.启动服务，执行命令 net start mysql
7.登陆，执行命令 mysql -uroot -p 后输入前面mysqld --initialize --console命令输出的密码
8.修改密码，执行命令 ALTER USER 'root'@'localhost' identified with mysql_native_password by '新密码';