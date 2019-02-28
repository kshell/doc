## MySql 整理
### 版本信息

| 版本号 | 日期       | 作者   | 描述 |
| ------ | ---------- | ------ | ---- |
| v1.0   | 2018-07-12 | kshell |      |


### 一、环境

| 项目     | 版本号                                                |
| -------- | ----------------------------------------------------- |
| 操作系统 | Linux Mint 18.3 Sylvia 64 位                          |
| 内核版本 | Linux 4.13.0-43-generic x86_64                        |
| 数据库   | MariaDB-10.2.14+maria~jessie  (docker mariadb:latest) |
| Docker   | Docker version 1.13.1, build 092cba3                  |

## 二、备份

### 1、导出命令用法

```
mysqldump -h 主机地址 -u用戶名 -p密码 -d 数据库名 表名 > 脚本名;
```

### 2、导出整个数据库结构和数据

```
mysqldump -h localhost -uroot -p123456 database > dump.sql
```

### 3、导出单个数据表结构和数据

```
mysqldump -h localhost -uroot -p123456  database table > dump.sql
```

### 4、导出整个数据库结构（不包含数据）

```
mysqldump -h localhost -uroot -p123456  -d database > dump.sql
```

### 5、导出单个数据表结构（不包含数据）

```
mysqldump -h localhost -uroot -p123456  -d database table > dump.sql
```




