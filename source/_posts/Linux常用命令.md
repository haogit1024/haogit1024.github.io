---
title: Linux常用命令
date: 2019-04-11 10:01:23
tags:
---
### 解压

```base
tar –xvf file.tar //解压 tar包
tar -xzvf file.tar.gz //解压tar.gz
tar -xjvf file.tar.bz2 //解压 tar.bz2
tar –xZvf file.tar.Z //解压tar.Z
unrar e file.rar //解压rar
unzip file.zip //解压zip
```

1. .tar 用 tar –xvf 解压
2. .gz 用 gzip -d或者gunzip 解压
3. .tar.gz和.tgz 用 tar –xzf 解压
4. .bz2 用 bzip2 -d或者用bunzip2 解压
5. .tar.bz2用tar –xjf 解压
6. .Z 用 uncompress 解压
7. .tar.Z 用tar –xZf 解压
8. .rar 用 unrar e解压
9. .zip 用 unzip 解压

---

### 文件操作

#### 重命名

例子：将目录A重命名为B

```base
mv A B
```

#### 移动文件

例子：将/a目录移动到/b下，并重命名为c

```base
mv /a /b/c
```

#### 查看内存占用

```base
sudo atop
free -h
top
```

例如

```base
ps -ef|grep java
```

```base
czh       25068   1702  3 19:08 ?        00:00:50 /usr/bin/java -Djava.util.logging.config.file=/home/czh/tomcat9/conf/logging.properties -Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager -Djdk.tls.ephemeralDHKeySize=2048 -Djava.protocol.handler.pkgs=org.apache.catalina.webresources -Dorg.apache.catalina.security.SecurityListener.UMASK=0027 -Dignore.endorsed.dirs= -classpath /home/czh/tomcat9/bin/bootstrap.jar:/home/czh/tomcat9/bin/tomcat-juli.jar -Dcatalina.base=/home/czh/tomcat9 -Dcatalina.home=/home/czh/tomcat9 -Djava.io.tmpdir=/home/czh/tomcat9/temp org.apache.catalina.startup.Bootstrap start
czh       29588  29549  0 19:32 pts/0    00:00:00 grep --color=auto java
```
查到了java的进程id为 25068

```base
top -p 25068
```

```base
 25068 czh       20   0 4102344 668584  16360 S   0.3 16.7   0:50.79 java 
```

#### 防火墙

用ufw管理防火墙和开放端口
```base
1.安装
sudo apt-get install ufw
2.启用
sudo ufw enable
sudo ufw default deny
运行以上两条命令后，开启了防火墙，并在系统启动时自动开启。关闭所有外部对本机的访问，但本机访问外部正常。
3.开启/禁用
sudo ufw allow|deny [service]
打开或关闭某个端口，例如：
sudo ufw allow smtp　允许所有的外部IP访问本机的25/tcp (smtp)端口
sudo ufw allow 22/tcp 允许所有的外部IP访问本机的22/tcp (ssh)端口
sudo ufw allow 53 允许外部访问53端口(tcp/udp)
sudo ufw allow from 192.168.1.100 允许此IP访问所有的本机端口
sudo ufw allow proto udp 192.168.0.1 port 53 to 192.168.0.2 port 53
sudo ufw deny smtp 禁止外部访问smtp服务
sudo ufw delete allow smtp 删除上面建立的某条规则
```
