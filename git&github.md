### git

一个开源的分布式版本控制系统，可以有效、高速地处理从很小到非常大的项目版本管理。也是为了帮助管理Linux内核开发而开发的一个开放源码的版本控制软件。

版本管理：记录文件变化的方式，以便将来查阅特定版本的文件内容。

git是一个版本管理控制系统（缩写VCS），它可以在任何时间点，将文档的状态（内容）作为更新记录保存起来，也可以在任何时间点，将更新记录恢复回来，git将不同时间段文档的状态进行保存，以便日后将文档恢复到特定的状态中

(SVN）集中式：只有一个中央服务器，而且必须与中央服务器进行连接。N台电脑，如果多个人员同时修改文件不被允许，文件被占用

（GIT)分布式：每一台电脑都是一个小型服务器，多个人员修改文件，有合并的操作。可以离线完成大部分操作

特点：

分布式相比于集中式的最大区别在于开发者可以提交到本地，每个开发者通过克隆（git clone），在本地机器上拷贝一个完整的Git仓库。

如图1所示是经典的git开发过程。

[![图1](https://bkimg.cdn.bcebos.com/pic/a71ea8d3fd1f4134ca7667d8251f95cad0c85ed6?x-bce-process=image/resize,m_lfit,w_440,limit_1/format,f_auto)](https://baike.baidu.com/pic/GIT/12647237/0/a71ea8d3fd1f4134ca7667d8251f95cad0c85ed6?fr=lemma&ct=single)图1

Git的功能特性：

从一般开发者的角度来看，git有以下功能：

1、从服务器上克隆完整的Git仓库（包括代码和版本信息）到单机上。

2、在自己的机器上根据不同的开发目的，创建分支，修改代码。

3、在单机上自己创建的分支上提交代码。

4、在单机上合并分支。

5、把服务器上最新版的代码fetch下来，然后跟自己的主分支合并。

6、生成补丁（patch），把补丁发送给主开发者。

7、看主开发者的反馈，如果主开发者发现两个一般开发者之间有冲突（他们之间可以合作解决的冲突），就会要求他们先解决冲突，然后再由其中一个人提交。如果主开发者可以自己解决，或者没有冲突，就通过。

8、一般开发者之间解决冲突的方法，开发者之间可以使用pull 命令解决冲突，解决完冲突之后再向主开发者提交补丁。

从主开发者的角度（假设主开发者不用开发代码）看，git有以下功能：

1、查看邮件或者通过其它方式查看一般开发者的提交状态。

2、打上补丁，解决冲突（可以自己解决，也可以要求开发者之间解决以后再重新提交，如果是开源项目，还要决定哪些补丁有用，哪些不用）。

3、向公共服务器提交结果，然后通知所有开发人员。

### GitHub

开源社区，是一个面向开源及私有软件项目的托管平台，因为只支持Git作为唯一的版本库格式进行托管，它为开源项目免费提供git存储，无数开源项目开始迁移到Github，包括jQuery、PHP、Hadoop、Hbase等

### git常用命令

##### 创建目录

```git
mkdir <文件名>
mkdir -p <文件名>//重名则不创建，反之创建
```

##### 查看当前目录下的所有文件(看你在哪个目录下打开gitbash)

```git
ls -a
ls -l  #查看创建者、创建时间
ll #查看创建者、创建时间
```

<img src="C:\Users\Huang\AppData\Roaming\Typora\typora-user-images\image-20220226085331465.png" alt="image-20220226085331465" style="zoom:25%;" />

##### 查看文件的绝对路径

```git
pwd
```

##### 进入目录

```git
cd
```

#### 操作文件的时候建议使用-i

##### 删除文件

```git
rm <文件名>//删除文件   目录dir  rmdir
-i //删除的时候询问   rm -i test1
-rf //强制删除，不可逆 rm -rf test1
```

##### 删除目录

```git
rmdir <目录名> //删除目录 要与删除文件区别开
```

https://blog.csdn.net/dengsilinming/article/details/8000622?utm_source=app&app_version=5.0.1&code=app_1562916241&uLinkId=usr1mkqgl919blen

##### 清除屏幕

```git
clear
```

https://github.com/Huangpto/Rainbow-Song/blob/ec58e74c7f5c7fe2314bc82aef2a43362317e436/README.md

找到PERMALINK

进入仓库——读取——右上角省略号——copy permalink

### 将repo pull到本地

也可以先创建一个目录

打开bash 在命令行输入git init

git clone [   Huangpto/remote-repo: A remote repo (github.com)](https://github.com/Huangpto/remote-repo).git

