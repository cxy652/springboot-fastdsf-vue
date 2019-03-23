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
