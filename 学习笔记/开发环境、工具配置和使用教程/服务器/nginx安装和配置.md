# Window版本

## 下载并安装nginx

官网的地址：`https://nginx.org/en/`

去这个官网下载最新版的**nginx**

<img src="nginx%E5%AE%89%E8%A3%85%E5%92%8C%E9%85%8D%E7%BD%AE_images/image-20230219190731375.png" alt="image-20230219190731375" style="zoom: 33%;" />

下载稳定版的就好，免得出现一些奇奇怪怪的**bug**

<img src="nginx%E5%AE%89%E8%A3%85%E5%92%8C%E9%85%8D%E7%BD%AE_images/image-20230219190906439.png" alt="image-20230219190906439" style="zoom: 33%;" />

下载完成之后，解压到你自己的文件夹去，尽量不要有中文，免得出现编码错误的问题

<img src="nginx%E5%AE%89%E8%A3%85%E5%92%8C%E9%85%8D%E7%BD%AE_images/image-20230219191055496.png" alt="image-20230219191055496" style="zoom: 50%;" />



## 启动Nginx

- 解压出 `nginx`的文件之后，直接进入这个文件。
  - ![image-20230219191352149](nginx%E5%AE%89%E8%A3%85%E5%92%8C%E9%85%8D%E7%BD%AE_images/image-20230219191352149.png)

- 然后在当前目录下打开终端运行如下命令：

  - ```cmd
    start nginx
    ```

    ![image-20230219191444765](nginx%E5%AE%89%E8%A3%85%E5%92%8C%E9%85%8D%E7%BD%AE_images/image-20230219191444765.png)

- 这个时候`nginx`的服务就启动了

- 在浏览器中访问`localhost`，就能看到`nginx`的初始化界面。
  - <img src="nginx%E5%AE%89%E8%A3%85%E5%92%8C%E9%85%8D%E7%BD%AE_images/image-20230219191518196.png" alt="image-20230219191518196" style="zoom: 33%;" />

- 到这里就成功了。

>如果要关闭`nginx`就运行`nginx -s stop`就能停止服务

## 全局变量

- 前面的使用都是在，`nginx`解压的目录里面使用命令，这样很不方便，我们希望在所有地方都可以使用。那么就需要配置一下系统的全局变量。

- 把当前这个`nginx`的文件地址复制下来：

  - ```shell
    E:\code development\nginx-1.22.1
    ```

    - 这是我本机`nginx`的位置

- 打开系统的环境变量
  - <img src="nginx%E5%AE%89%E8%A3%85%E5%92%8C%E9%85%8D%E7%BD%AE_images/image-20230219192140457.png" alt="image-20230219192140457" style="zoom: 33%;" />

- 在变量中找到`path`打开编辑页面，将前面复制的地址`copy`进去。
  - <img src="nginx%E5%AE%89%E8%A3%85%E5%92%8C%E9%85%8D%E7%BD%AE_images/image-20230219192319764.png" alt="image-20230219192319764" style="zoom:33%;" />
- 测试一下是否可以
  - <img src="nginx%E5%AE%89%E8%A3%85%E5%92%8C%E9%85%8D%E7%BD%AE_images/image-20230219192416602.png" alt="image-20230219192416602" style="zoom:33%;" />
- 我在我的桌面下使用`nginx`相关命令，成功输出结果。
- 这就成功了。