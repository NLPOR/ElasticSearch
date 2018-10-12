# 所需工具/原料
## Elasticsearch
## JDK8

# 方法/步骤
* 1.进入终端系统，先升级apt-get源
* 2.ES是使用java开发的，所以需要JVM才可以跑起来。因此首先要安装一下JDK（或JRE）,我们这里Elasticsearch的最新版本需要JDK8（JRE8）及以上，执行：
sudo apt-get install default-jdk
来安装JDK环境。安装完成后，执行
java -version
来查看是否安装成功
* 3.JDK安装完成后，就可以来下载Elasticsearch的压缩包了。（此处使用压缩包的方式安装，还有很多其他安装方式）<p>
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-5.4.0.zip
* 4.下载完成后，来对下载的压缩包进行一下校验。<p>
sha1sum elasticsearch-5.4.0.zip
* 5.校验通过后，就可以进行解压了<p>
unzip elasticsearch-5.4.0.zip
* 6.解压完成，后就已经安装成功，然后进入Elasticsearch安装目录<p>   
cd /elasticsearch-5.4.0/bin/elasticsearch启动服务。

# 启动过程出现的一些报错信息以及解决方案
## 1.不能以root身份启动的情况

需要创建一个新的用户，执行如下命令创建一个用户（elsearch）组及elsearch用户

* groupped elsearch
* useradd elsearch -g elsearch -p elasticsearch

然后更改elasticsearch文件夹及内部文件的所属用户及组为elsearch:elsearch
* chown -R elsearch:elsearch elasticsearch-5.4.0
<font color='red'>
elasticsearch-5.4.0是你的ES安装目录名称
</font>

切换到elsearch再启动

* su elsearch
* cd elasticsearch/bin
* ./elasticsearch

之后启动需要切换账户，查看后台命令是否启动成功
* ps aux|grep elasticsearch

