## 更新源
1.用vim打开源列表文件   
  sudo vim /etc/apt/sources.list
2.将下面的源粘贴到源列表里    
deb http://mirrors.aliyun.com/ubuntu/ xenial main restricted universe multiverse    
deb http://mirrors.aliyun.com/ubuntu/ xenial-security main restricted universe multiverse   
deb http://mirrors.aliyun.com/ubuntu/ xenial-updates main restricted universe multiverse    
deb http://mirrors.aliyun.com/ubuntu/ xenial-backports main restricted universe multiverse    
##测试版源    
deb http://mirrors.aliyun.com/ubuntu/ xenial-proposed main restricted universe multiverse   
#源码    
deb-src http://mirrors.aliyun.com/ubuntu/ xenial main restricted universe multiverse    
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-security main restricted universe multiverse   
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-updates main restricted universe multiverse    
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-backports main restricted universe multiverse    
##测试版源    
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-proposed main restricted universe multiverse   
#Canonical 合作伙伴和附加   
deb http://archive.canonical.com/ubuntu/ xenial partner   
deb http://extras.ubuntu.com/ubuntu/ xenial main    
## ubuntu安装MySQL
* sudo apt-get update 更新源
* sudo apt-get install mysql-client mysql-server 安装mysql服务器和客户端
* sudo /etc/init.d/mysqld start 启动mysql服务
## Apache安装
* sudo apt-get update
* sudo apt-get install tasksel
* sudo tasksel
## workbench 安装
* sudo apt-get install mysql-workbench

# MySQL 命令行操作

## 连接Mysql 格式： mysql -h 主机地址 -u用户名 －p用户密码

## 连接到本机上的MYSQL
键入命令mysql -u root -p，回车后提示你输密码.注意用户名前可以有空格也可以没有空格，但是密码前必须没有空格，否则让你重新输入密码。如果刚安装好MYSQL，超级用户root是没有密码的，
故直接回车即可进入到MYSQL中了，MYSQL的提示符是： mysql>    
## 连接到远程主机上的MYSQL
假设远程主机的IP为：110.110.110.110，用户名为root,密码为abcd123。则键入以下命令： mysql -h110.110.110.110 -u root -p 123;（注:u与root之间可以不用加空格，其它也一样）

## 退出MYSQL命令： exit （回车）
# 支持中文
1.创建table的时候就使用utf8编码,在每次创建表的时候都在最后加上 character set = utf8 就可以很好的支持中文。    
2.修改已经有的table的编码,当使用默认编码创建了一个table的时候，是不能支持中文的，这时候使用如下语句对information进行修改:   
 * mysql > alter table information convert to character set utf8;   
## 创建数据库
1.注意：创建数据库之前要先连接Mysql服务器    
* 命令：create database <数据库名>
* 例1：建立一个名为xhkdb的数据库 mysql> create database xhkdb;
## 显示数据库
* mysql> show databases
## 删除数据库
* mysql> drop database xhkdb;
## 使用数据库
* use <数据库名>
## 创建数据表
* create table <表名> ( <字段名1> <类型1> [,..<字段名n> <类型n>]);
## 删除表
* drop table <表名>
## 表插入数据
* insert into <表名> [( <字段名1>[,..<字段名n > ])] values ( 值1 )[, ( 值n )]
## 查询表中的数据
1.查询所有行 命令： select <字段1，字段2，...> from < 表名 > where < 表达式 > 例如：查看表 MyClass 中所有数据 mysql> select * from MyClass;

2.查询前几行数据 例如：查看表 MyClass 中前2行数据 mysql> select * from MyClass order by id limit 0,2;

## 修改表中数据
* update 表名 set 字段=新值,... where 条件 mysql> update MyClass set name='Mary' where id=1;
## 增加字段
* alter table 表名 add字段 类型
## 添加索引
1.加索引 mysql> alter table 表名 add index 索引名 (字段名1[，字段名2 ...]);    
2.加主关键字的索引 mysql> alter table 表名 add primary key (字段名);   
3.加唯一限制条件的索引 mysql> alter table 表名 add unique 索引名 (字段名);    

## 查看索引
* show index from 表名
## 删除索引
* mysql> alter table 表名 drop index 索引名;
## MySQL 数据库设计、备份及优化
## 数据库备份
1.导出整个数据库 导出文件默认是存在mysql\bin目录下 mysqldump -u 用户名 -p 数据库名 > 导出的文件名 mysqldump -u user_name -p123456 database_name > outfile_name.sql

2.导出一个表 mysqldump -u 用户名 -p 数据库名 表名> 导出的文件名 mysqldump -u user_name -p database_name table_name > outfile_name.sql

3.导出一个数据库结构 mysqldump -u user_name -p -d –add-drop-table database_name > outfile_name.sql -d 没有数据 –add-drop-table 在每个create语句之前增加一个drop table

4.带语言参数导出 mysqldump -uroot -p –default-character-set=latin1 –set-charset=gbk –skip-opt database_name > outfile_name.sql   

5. 导出表数据到文件中： mysql -uroot -p123456 --default-character-set=utf8 use guanjia; select _from driver into outfile '/tmp/a.txt'; (select_ from crawlDocs order by DocCrawlTime desc limit 2000 into outfile '/tmp/weixinData' FIELDS TERMINATED BY ',';) 一般最好是导出到/tmp目录下，因为这样mysql用户也可以写入。
 
## 数据库导入

1. 导入数据库    
在本地数据库中创建相对应导出的数据库mydb同名的数据库： mysql> create database mydb; 然后退出数据库，再使用以下的 命令导入数据库文件mydb.bak到本地数据库mydb中： mysql -uroot -p123456 mydb < /root/data/mydb.bak;

2. 导入数据表    
然后在mysql中使用source指令来完成数据表的导入，如下： mysql> source /root/data/tb1.bak; // /root/data/tb1.bak是远程数据表tb1导出文件的本地存放位置

3. 表数据导入到数据表中   
 mysql -uroot -p123456 --default-character-set=utf8 use guanjia; load data infile '/tmp/a.txt' into table test CHARACTER SET utf8;

(load data infile '/tmp/weiData' into table crawlDocs CHARACTER SET utf8 FIELDS TERMINATED BY ',';)

如果导入时出现类似 ERROR 29 (HY000): File '/tmp/a.txt' not found (Errcode: 13)的错误，则很可能是因为mysql用户没有权限访问该文件， 则使用 chown mysql:mysql /tmp/a.txt 将该文件的所属设为mysql用户，再次执行上面的命令则一般可以完成导入。
