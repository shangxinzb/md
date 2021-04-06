service firewalld stop

#修改 /etc/selinux/config 
SELINUX=disabled
####################
init 6

rpm -qa | grep mariadb
yum remove mariadb-libs-5.5.64-1.el7.x86_64
wget https://dev.mysql.com/get/mysql80-community-release-el7-3.noarch.rpm
rpm -ivh mysql80-community-release-el7-3.noarch.rpm
yum install mysql-community-server
mkdir -p /home/data/mysql/data/mysql-bin
chown -R mysql:mysql /home/data/mysql/data
mkdir -p /home/log
touch /home/log/mysql-error.log
touch /home/log/slow.log
chown -R mysql:mysql /home/log

#修改 /etc/my.cnf

[mysqld]
server-id=1
datadir=/home/data/mysql/data
socket=/var/lib/mysql/mysql.sock
log_error=/home/log/mysql-error.log
pid_file=/var/run/mysqld/mysqld.pid
transaction_isolation=READ-COMMITTED
max_connections=3000
max_connect_errors=6000
max_allowed_packet=128M
interactive_timeout=3600
wait_timeout=3600
tmp_table_size=268435456
max_heap_table_size=268435456
slow_query_log=1
slow_query_log_file=/home/log/slow.log
log_queries_not_using_indexes=1
log_throttle_queries_not_using_indexes=5
log_slow_slave_statements=1
long_query_time=2
min_examined_row_limit=100
back_log=600
sort_buffer_size=4M
join_buffer_size=4M
thread_cache_size=512
key_buffer_size=2048M
log_bin=/home/data/mysql/data/mysql-bin
binlog_cache_size=4M
max_binlog_cache_size=8M
max_binlog_size=1024M
expire_logs_days=10
read_buffer_size=2M
read_rnd_buffer_size=16M
bulk_insert_buffer_size=64M
innodb_buffer_pool_size=2048M
innodb_data_file_path=ibdata1:1024M:autoextend
innodb_file_per_table=1
lower_case_table_names=2
####################
systemctl start mysqld.service


#获取临时密码
grep "password" /home/log/mysql-error.log
2020-03-04T09:44:58.251332Z 5 [Note] [MY-010454] [Server] A temporary password is generated for root@localhost: xUG!xQtt0eV<

#修改密码
mysql -uroot -p

ALTER USER 'root'@'localhost' IDENTIFIED BY 'AmHe123!@#';
CREATE USER 'koubei'@'%' IDENTIFIED BY 'Koubei123!@#';
GRANT ALL PRIVILEGES ON *.* TO 'koubei'@'%';
flush privileges;

#主库
CREATE USER 'repl'@'%' IDENTIFIED WITH mysql_native_password BY 'Slave123!@#';
GRANT REPLICATION SLAVE ON *.* TO 'repl'@'%';
flush privileges;
show master status;
# mysql-bin.000002

# 1878

#从库
CHANGE MASTER TO
MASTER_HOST='10.135.111.21',
MASTER_USER='repl',
MASTER_PASSWORD='Slave123!@#',
MASTER_LOG_FILE='mysql-bin.000002',
MASTER_LOG_POS=1878;

start slave;

show slave status\G