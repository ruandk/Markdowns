# Linux部署前端项目

## OS: CentOS 7.6 64位

## 一、配置
```shell
cd /usr/local

# 下载node包 (http://nodejs.cn/download -> 阿里云镜像 -> 搜索'-linux-x64.tar.xz'下载最新node包)
wget https://npm.taobao.org/mirrors/node/v12.13.0/node-v12.13.0-linux-x64.tar.xz

# 解压node包，分别执行以下两指令
xz -d node-v12.13.0-linux-x64.tar.xz

tar -xf node-v12.13.0-linux-x64.tar

# 配置环境变量(全局可用命令)
ln -s /usr/local/node-v12.13.0-linux-x64/bin/node /usr/bin/node

ln -s /usr/local/node-v12.13.0-linux-x64/bin/npm /usr/bin/npm

# 安装cnpm并配置环境变量
npm install -g cnpm --registry=https://registry.npm.taobao.org

ln -s /usr/local/node-v12.13.0-linux-x64/lib/node_modules/cnpm/bin/cnpm /usr/bin/cnpm
```

## 二、创建express项目
* 初始化
```shell
cd /home

mkdir app && cd app

cnpm init -y

cnpm i express -S
```

* 添加app.js、创建public文件夹
```js
const express = require('express')
const path = require('path')
const app = express()

app.use(express.static(path.join(__dirname, 'public')))

app.listen(80, () => {
  console.log(`listening at port 80 public`)
})
```

* 修改package.json
```js
{
  "scripts": {
    "start": "node app"
  }
}
```

## 二、打包并上传到服务器
```shell
npm run build
```
将本地项目打包生成的文件上传到服务器/home/app/public目录


## 三、运行
```shell
# 服务端后台运行
nohup npm run start &   

# 运行后不可直接关闭远程连接客户端
exit                    
```
注意：阿里云安全组配置规则允许访问对应端口

## 四、常用命令
```shell
# 命令历史
history

# 显示所有node进程
ps -ef|grep node

# 结束所有node进程
pkill node

# 结束指定进程
kill -9 ***

# 删除文件
rm -f ***
```