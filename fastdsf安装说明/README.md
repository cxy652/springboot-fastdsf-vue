# 分布式文件系统FastDFS安装教程
##  安装libfastcommon
*   获取libfastcommon安装包：  
    `wget https://github.com/happyfish100/libfastcommon/archive/V1.0.38.tar.gz`  
* 解压安装包：tar -zxvf V1.0.38.tar.gz  
* 进入目录：cd libfastcommon-1.0.38
* 执行编译：./make.sh  
* 安装：./make.sh install  
* 可能遇到的问题：  
`-bash: make: command not found`  
`-bash: gcc: command not found`  
`解决方案：`  
`debian通过apt-get install gcc make安装`  
`centos通过yum -y install gcc make安装`  
##  ￼安装FastDFS  
* 获取fdfs安装包：
`wget https://github.com/happyfish100/fastdfs/archive/V5.11.tar.gz`  
* 解压安装包：tar -zxvf V5.11.tar.gz
* 进入目录：cd fastdfs-5.11
* 执行编译：./make.sh
* 安装：./make.sh install
* 查看可执行命令：ls -la /usr/bin/fdfs*

## 配置Tracker服务
*   进入/etc/fdfs目录，有三个.sample后缀的文件（自动生成的fdfs模板配置文件），通过cp命令拷贝tracker.conf.sample，删除.sample后缀作为正式文件：  
*   编辑tracker.conf：vi tracker.conf，修改相关参数
`base_path=/home/mm/fastdfs/tracker  #tracker存储data和log的跟路径，必须提前创建好`   
`port=23000 #tracker默认23000`  
`http.server_port=80 #http端口，需要和nginx相同`  
*   启动tracker（支持start|stop|restart）：
`/usr/bin/fdfs_trackerd /etc/fdfs/tracker.conf start`
*   查看tracker启动日志：进入刚刚指定的base_path(/home/mm/fastdfs/tracker)中有个logs目录，查看tracker.log文件
*   查看端口情况：netstat -apn|grep fdfs
##  配置Storage服务
*   进入/etc/fdfs目录，有cp命令拷贝storage.conf.sample，删除.sample后缀作为正式文件;
*   编辑storage.conf：vi storage.conf，修改相关参数：
`base_path=/home/mm/fastdfs/storage   #storage存储data和log的跟路径，必须提前创建好`  
`port=23000  #storge默认23000，同一个组的storage端口号必须一致`  
`roup_name=group1  #默认组名，根据实际情况修改`  
`tore_path_count=1  #存储路径个数，需要和store_path个数匹配`  
`tore_path0=/home/mm/fastdfs/storage  #如果为空，则使用base_path`  
`racker_server=10.122.149.211:22122 #配置该storage监听的tracker的ip和port`  
*   启动storage（支持start|stop|restart）：  
`/usr/bin/fdfs_storaged /etc/fdfs/storage.conf start`  
*   查看storage启动日志：进入刚刚指定的base_path(/home/mm/fastdfs/storage)中有个logs目录，查看storage.log文件
*   此时再查看tracker日志：发现已经开始选举，并且作为唯一的一个tracker，被选举为leader
