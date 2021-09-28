# Linux
## 文件
在Linux系统中，每个设备都被当成一个文件来对待。
### 设备文件：
SATA{
   命名：/dev/sd[a-p]
   命名规则：按照检测顺序进行命名
   MBR分区:{
      主分区
      扩展分区->逻辑分区
      命名:{
         主分区和扩展分区：/dev/sda[1-4]
         逻辑分区：/dev/sda[>4]
      }
      命名方式：主分区和逻辑分区的分区表只能存储四组数据的空间，编号1-4表示主分区和逻辑分区，往后才表示逻辑分区。
   }
   GPT分区:{
      无分区类别限制，最多128组分区
   }
}

### 常用文件位置
应用程序文档：/usr/share/doc
应用程序日志：/var/log
## 环境配置

### JAVA

> 作者：淡漠丶frozen
> 链接：https://www.jianshu.com/p/4d402abf46e4
> 来源：简书

##### 1. 介绍：

**Java**开发环境包括 **Jdk** 以及各种 **IDE**，最流行的莫过于 **jdk + eclipse \**组合。
 本章将对 \*\*jdk\*\* 以及\** eclipse** 的安装进行讲解。

##### 2. 展示：

![img](https:////upload-images.jianshu.io/upload_images/3107638-d722449c0132b411.png?imageMogr2/auto-orient/strip|imageView2/2/w/1200/format/webp)

**Jdk&Eclipse**

##### 3. 安装(Linux版)：

###### 1) JDK

- [下载 **jdk**](https://link.jianshu.com?t=http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)

![img](https:////upload-images.jianshu.io/upload_images/3107638-e7d2a6afdc6d359a.png?imageMogr2/auto-orient/strip|imageView2/2/w/304/format/webp)

**DOWNLOAD**

点击 **DOWNLOAD**；

![img](https:////upload-images.jianshu.io/upload_images/3107638-fb6e7bcc86da4923.png?imageMogr2/auto-orient/strip|imageView2/2/w/544/format/webp)

**License Agreement**

点击 Accept License Agreement
 　然后选择包：**Linux x64**

** PS **：**Linux x86** 是32位的 **linux** 系统使用

**『** 这里 **Linux x64** 有两种包，分别是 **rpm** 和 **tar.gz** 。
 　两种都可以，只不过安装工具不同 。
 　个人比较喜欢用 **tar.gz** 的，所以本次以 **tar.gz** 介绍 。**』**

- 解压
   root@Cyborg:~/下载# tar -zxvf jdk*.tar.gz

- 再把解压后的文件夹移动到自己喜欢的路径下
   root@Cyborg:~/下载# mv jdk1.8.0_131/ /opt/

- 配置环境变量
   进入 *jdk1.8.0_121/*，得到 **jdk** 的路径 *"/opt/jdk1.8.0_131"*
   打开配置文件：
   root@Cyborg:/opt/jdk1.8.0_131# leafpad /etc/profile
   在弹出的文本文件末尾加上代码：

> JAVA_HOME=/opt/jdk1.8.0_131　　　　　#把值修改成自己的路径
>  CLASSPATH=.:$JAVA_HOME/lib.tools.jar
>  PATH=$JAVA_HOME/bin:$PATH
>  export JAVA_HOME CLASSPATH PATH

保存，退出；
 再更新一下：



```ruby
    root@Cyborg:/opt/jdk1.8.0_131# source /etc/profile
```

- 切换版本
   安装完后需要把默认的**java**切换到刚刚安装的**java**版本上来(**Kali Linux**自带**OpenJdk**版本)
   删除原本默认软链：
   root@Cyborg:/etc# rm /usr/bin/javac && rm /usr/bin/java
   添加新软链：
   root@Cyborg:/# ln -s /opt/jdk1.8.0_131/bin/java /usr/bin/java
   root@Cyborg:/# ln -s /opt/jdk1.8.0_131/bin/javac /usr/bin/javac

- 测试

  

  ```ruby
  root@Cyborg:/opt/jdk1.8.0_131# java -version
  ```

如果返回：
 java version "1.8.0_131"
 Java(TM) SE Runtime Environment (build 1.8.0_131-b11)
 Java HotSpot(TM) 64-Bit Server VM (build 25.131-b11, mixed mode)
 则成功。

###### 2) Eclipse

- 下载
   [直接下载](https://link.jianshu.com?t=http://mirrors.ustc.edu.cn/eclipse/technology/epp/downloads/release/neon/3/eclipse-java-neon-3-linux-gtk-x86_64.tar.gz) / [去官网下载](https://link.jianshu.com?t=https://www.eclipse.org/downloads/packages/eclipse-ide-java-developers/neon3)；
- 解压
   root@Cyborg:~/下载# tar -zxvf eclipse-*.tar.gz
- 再把解压后的文件夹移动到自己喜欢的路径下
   root@Cyborg:~/下载# mv eclipse /opt/
- 配置环境变量
   进入 *eclipse/*，得到 **eclipse** 的路径 *"/opt/eclipse"*
   打开配置文件：
   root@Cyborg:/opt/eclipse# leafpad /etc/profile
   在弹出的文本文件末尾加上代码：

> ECLIPSE=/opt/eclipse　　　　　 #把值修改成自己的路径
>  PATH=$ECLIPSE:$PATH
>  export  ECLIPSE PATH

- 再更新一下：
   root@Cyborg:/opt/eclipse# source /etc/profile
- 启动优化
   每次用**eclipse**都要运行：
   root@Cyborg:/# /opt/eclipse/eclipse
   这无疑很麻烦，现在把 **eclipse** 添加到 */usr/bin* 里每次只要输入**eclipse** 就可以打开使用了。
   root@Cyborg:/# ln -s /opt/eclipse/eclipse /usr/bin/eclipse



