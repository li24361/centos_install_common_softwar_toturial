# centos_install_common_softwar_toturial

# CentOS7 安装开发环境常用命令

## 使用yum安装 Node.js 环境

    yum install -y npm

## 下载源码安装 Node.js 环境

### 下载并安装 Node.js
下载最新的稳定版 v6.10.3 到本地

    wget https://nodejs.org/dist/v6.10.3/node-v6.10.3-linux-x64.tar.xz
下载完成后, 将其解压

    tar xvJf node-v6.10.3-linux-x64.tar.xz
将解压的 Node.js 目录移动到 /usr/local 目录下

    mv node-v6.10.3-linux-x64 /usr/local/node-v6
配置 node 软链接到 /bin 目录

    ln -s /usr/local/node-v6/bin/node /bin/node
### 配置和使用 npm
配置 npm
npm 是 Node.js 的包管理和分发工具。它可以让 Node.js 开发者能够更加轻松的共享代码和共用代码片段
下载 node 的压缩包中已经包含了 npm , 我们只需要将其软链接到 bin 目录下即可

    ln -s /usr/local/node-v6/bin/npm /bin/npm
配置环境变量
将 /usr/local/node-v6/bin 目录添加到 $PATH 环境变量中可以方便地使用通过 npm 全局安装的第三方工具

    echo 'export PATH=/usr/local/node-v6/bin:$PATH' >> /etc/profile
生效环境变量

    source /etc/profile
    
使用 npm
通过 npm 安装进程管理模块 forever

    npm install -g forever 
安装源管理软件

    npm install -g nrm
    
更改为淘宝镜像

    npm config set registry http://registry.npm.taobao.org/ 
    npm config set disturl http://npm.taobao.org/mirrors/node
    
    
