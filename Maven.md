
# maven安装

### 下载并解压安装包

    cd /home
    wget http://mirrors.shuosc.org/apache/maven/maven-3/3.5.2/binaries/apache-maven-3.5.2-bin.tar.gz

解压压缩包：

    tar xzvf apache-maven-3.5.2-bin.tar.gz
将文件夹移动至 /usr/local/ 目录：

    mv apache-maven-3.5.2 /usr/local/apache-maven
    
    
### 配置环境变量
编辑 /etc/profile，在最下方添加：

    MAVEN_HOME=/usr/local/apache-maven
    export MAVEN_HOME
    export PATH=${PATH}:${MAVEN_HOME}/bin
    
保存文件并刷新

    source /etc/profile
   
   
检查 Maven 是否成功安装：

    mvn -version
   
