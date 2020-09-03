#             mysql change   slave  user passwd 

## 1. change passwd and lock all dbs *on master*

```
use mysql
SET PASSWORD FOR 'slaveuser'@'%' = PASSWORD('8yz_QqJHPgqG');
OR 
ALTER USER 'slaveuser'@'%' IDENTIFIED BY '8yz_QqJHPgqG';
```

###### local table

```
FLUSH TABLES WITH READ LOCK;
SET GLOBAL read_only = 1;
```

###### show master current info

```
show master status\G
```

## 2. on slave server

###### stop slave 

```
stop  SLAVE;
```

###### change replication info

```
CHANGE MASTER TO MASTER_HOST='10.89.65.113',MASTER_USER='slaveuser', MASTER_PASSWORD='8yz_QqJHPgqG', MASTER_LOG_FILE='mysql-bin.000003', MASTER_LOG_POS=103769788;
```

###### start slave 

```
START SLAVE;
```

###### show slave status

```
SHOW SLAVE STATUS\G
```

######  If there is an issue in connecting, you can try starting slave with a command to skip over it:

```
SET GLOBAL SQL_SLAVE_SKIP_COUNTER = 1; SLAVE START; 
```

## 3. unlock master mysql

```
SET GLOBAL read_only = 0;
UNLOCK TABLES;
```