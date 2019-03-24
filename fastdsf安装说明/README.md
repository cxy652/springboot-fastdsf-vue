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
