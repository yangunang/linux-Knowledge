#                  mysql yum install

#### 1.Adding the MySQL Yum Repository

```
wget https://repo.mysql.com//mysql80-community-release-el7-3.noarch.rpm
```

```
 yum localinstall  mysql80-community-release-el7-3.noarch.rpm
```

```
yum repolist enabled | grep "mysql.*-community.*"
```

<!--You can check that the MySQL Yum repository has been successfully added by the following command:-->

 

#### 2.Selecting a Release Series

```
yum repolist all | grep mysql
```

```
yum-config-manager --disable mysql80-community

yum-config-manager --enable mysql56-community
```

#### 3.Installing MySQL

```
yum install mysql-community-server
```

