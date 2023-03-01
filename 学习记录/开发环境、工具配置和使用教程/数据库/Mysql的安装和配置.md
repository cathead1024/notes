# Window版本安装

## 安装

- 官网：`https://dev.mysql.com`

- 在官网找到下载的界面，下载社区服务器
  - <img src="Mysql%E7%9A%84%E5%AE%89%E8%A3%85%E5%92%8C%E9%85%8D%E7%BD%AE_images/image-20230215221108731.png" alt="image-20230215221108731" style="zoom:25%;" />

- 有两个版本，一个是有安装界面的版本，一个是直接解压使用，我们直接下载解压包。
- 使用配置会比较方便
  - <img src="Mysql%E7%9A%84%E5%AE%89%E8%A3%85%E5%92%8C%E9%85%8D%E7%BD%AE_images/image-20230215221900339.png" alt="image-20230215221900339" style="zoom:25%;" />

- 下载完成之后，解压到自己的文件夹里面去即可。

## 配置

- 之后需要在解压出来的文件夹里面创建一个`my.ini`配置文件
  - <img src="Mysql%E7%9A%84%E5%AE%89%E8%A3%85%E5%92%8C%E9%85%8D%E7%BD%AE_images/image-20230215222443495.png" alt="image-20230215222443495" style="zoom:25%;" />
  - 这是我的解压文件，直接创建文件`my.ini`并编写。

```ini
[client]
# 设置mysql客户端默认字符集
default-character-set=utf8
 
[mysqld]
# 设置8711端口，我的8711端口用于mysql数据库
port = 8711
# 设置mysql的安装目录
basedir=E:\code development\mysql-8.0.32-winx64
# 设置 mysql数据库的数据的存放目录，MySQL 8+ 不需要以下配置，系统自己生成即可，否则有可能报错
# datadir=C:\\web\\sqldata
# 允许最大连接数
max_connections=20
# 服务端使用的字符集默认为8比特编码的latin1字符集
character-set-server=utf8
# 创建新表时将使用的默认存储引擎
default-storage-engine=INNODB
```

## 初始化服务

- 编写完配置文件之后，进入`bin`文件，在`bin`文件的目录下访问`mysql`服务，并输入如下命令

- ```mysql
  mysqld --initialize --user=mysql --console
  ```

  - 这段命令是初始化`mysql`，并且输出相关信息，里面包含有`root`用户的默认密码

  - 默认情况下`window powershell` 不会从当前位置加载命令。如果出现报错请根据`window powershell`的提示输入

  - 例：

    - ```mysql
      .\mysqld --initialize --console
      ```

      - 需要在开头加`.\`

- <img src="Mysql%E7%9A%84%E5%AE%89%E8%A3%85%E5%92%8C%E9%85%8D%E7%BD%AE_images/image-20230215224103663.png" alt="image-20230215224103663" style="zoom: 25%;" />

- 成功之后，就可以看到出现了一堆信息，其中这个就是我们需要的`root`用户的初始密码`iYZ1O0rbd9&g`

>这里会出现很多问题，大部分问题都是端口被占用的问题，如果出现端口被占用的问题，就把对应的端口杀掉，重新测试几次就可以了。

- 输入命令安装`mysql`服务

  - ```
    mysqld install 或 .\mysqld install
    ```

    - ![image-20230215225940211](Mysql%E7%9A%84%E5%AE%89%E8%A3%85%E5%92%8C%E9%85%8D%E7%BD%AE_images/image-20230215225940211.png)

- 安装成功之后就可以开启服务了。

- ```mysql
  net start mysql 
  ```

  - 使用这个命令开启`mysql`服务
  - 如果在这个过程遇到问题就用：`mysqld --console`打印一下。
    - 我在这里就遇到端口被占用的问题，我的选择是直接换一个端口是使用。

- ```mysql
  mysql -u root -p
  ```

  - 服务启动成功的话就可以用这个命令访问本机的`mysql`服务器

  - 如果要访问其他主机的`mysql`可以使用 :

    - ```
      mysql -h 主机名称 -u root -p
      ```

  - 进入之后，就会出现需要你输入密码的地方，把前面复制来的初始密码输入即可。

    - 把前面复制的初始密码输入就可以了。
    - <img src="Mysql%E7%9A%84%E5%AE%89%E8%A3%85%E5%92%8C%E9%85%8D%E7%BD%AE_images/image-20230218152913296.png" alt="image-20230218152913296" style="zoom:25%;" />

    - 这里就进入了`mysql`的命令界面

## 修改密码

- `Mysql8.0`修改密码和之前的版本不太一样，因为8.0没有`password`这个函数和字段。所以需要用新的命令才可以

  - ```mysql
    ALTER user 'root'@'localhost' IDENTIFIED BY 'root';// 将密码修改为 root
    ```

- 修改完成之后刷新一下权限 不用刷新也是可以的。

  - ```mysql
    flush privileges;
    ```

## 全局变量

- 

## 问题汇总

## 日志

- 后面需要补充：
- linux 安装 mysql8.0 
- docker 安装 mysql 8.0 
- 遇到的问题汇总
  - 服务启动失败
  - 密码更新失败
    - 密码更新的方式和之前有所不同
  - 修改驱动的密码
  - 全局变量的设置