一、配置国内源
1、按网上说的，打开ubuntu software，然后进入software&updates更换成aliyun，自动更新（apt-get update），失败
2、修改/etc/apt/sources.list文件，切换成aliyun国内镜像，sudo apt-get update失败,报
```
Err http://security.ubuntu.com precise-security InRelease
W: Failed to fetch http://cn.archive.ubuntu.com/ubuntu/dists/precise/InRelease
```
3、看网上说需要修改DNS地址，然后设置DNS地址，
（#这里用的是阿里云的DNS服务器 nameserver 223.5.5.5 nameserver 223.6.6.6）
①临时方法：修改/etc/resolv.conf ，添加nameserver 223.5.5.5
②永久方法：1、/etc/network/interface之中配置dns-nameserver 223.5.5.5
2、/etc/NetworkManager/NetworkManager.conf之中配置dns=223.5.5.5
然而仍然报错
4、最后，将阿里源改为163源，配置成功
配置方法：①拷贝sources.list文件
```
sudo cp -p /etc/apt/sources.list /etc/apt/sources.list.org
```
②编辑sources.list文件
```
sudo gedit /etc/apt/sources.list
```
更换为下面内容
```
deb http://mirrors.163.com/ubuntu/ trusty main multiverse restricted universe 
deb http://mirrors.163.com/ubuntu/ trusty-backports main multiverse restricted universe 
deb http://mirrors.163.com/ubuntu/ trusty-proposed main multiverse restricted universe
deb http://mirrors.163.com/ubuntu/ trusty-security main multiverse restricted universe
deb http://mirrors.163.com/ubuntu/ trusty-updates main multiverse restricted universe
deb-src http://mirrors.163.com/ubuntu/ trusty main multiverse restricted universe
deb-src http://mirrors.163.com/ubuntu/ trusty-backports main multiverse restricted universe 
deb-src http://mirrors.163.com/ubuntu/ trusty-proposed main multiverse restricted universe 
deb-src http://mirrors.163.com/ubuntu/ trusty-security main multiverse restricted universe 
deb-src http://mirrors.163.com/ubuntu/ trusty-updates main multiverse restricted universe
```
③更新源
```
sudo apt-get update
```
二、update和upgrade 区别
sudo apt-get update ：是更新 /etc/apt/sources.list 和 /etc/apt/sources.list.d 中列出的源的地址,这样才能获取到最新的软件包
sudo apt-get upgrade ：是升级已安装的所有软件包，升级之后的版本就是本地地址里的，因此，在执行 upgrade 之前一定要执行 update, 这样才能更新到最新的
三、upgrade和dist-upgrade区别
upgrade:系统将现有的Package升级,如果有相依性的问题,而此相依性需要安装其它新的Package或影响到其它Package的相依性时,此Package就不会被升级,会保留下来. 
dist-upgrade:可以聪明的解决相依性的问题,如果有相依性问题,需要安装/移除新的Package,就会试着去安装/移除它。 (所以通常这个会被认为是有点风险的升级) 
apt-get upgrade 和 apt-get dist-upgrade 本质上是没有什么不同的。只不过，dist-upgrade 
会识别出当依赖关系改变的情形并作出处理，而upgrade对此情形不处理。
四、Xshell连接设置
想通过ssh被连接,ubuntu系统需要有openssh-server,可以通过
```
$ ps -e | grep ssh
```
来查看,如果没有显示sshd则说明没有安装openssh-server
没有安装，可通过
```
$ sudo apt-get install openssh-server
```
来安装openssh-server,如果顺利的话会安装成功,如果遇到
下列软件包有未满足的依赖关系：
 openssh-server : 依赖: openssh-client (= 1:6.6p1-2ubuntu1)
E: 无法修正错误，因为您要求某些软件包保持现状，就是它们破坏了软件包间的依赖关系。
这是因为,openssh-server是依赖于openssh-clien的,那ubuntu不是自带了openssh-client吗?原由是自带的openssh-clien与所要安装的openssh-server所依赖的版本不同,这里所依赖的版本是1:6.6p1-2ubuntu1
所以要安装对应版本的openssh-clien,来覆盖掉ubuntu自带的
```
$ sudo apt-get install openssh-client=1:6.6p1-2ubuntu1
```