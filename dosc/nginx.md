<!--
 * @Description: file content
 * @Author: wanghaoyu
 * @Date: 2023-09-23 19:07:21
 * @LastEditors: wanghaoyu
 * @LastEditTime: 2023-09-27 21:28:10
-->
# 网站页面搭建

1. 云服务

## 选择页面静态服务类型

1. nginx 快捷简便 √  支持 应用web缓存 反向代理 负载均衡
2. node - http 拓展性强 http.createServer().linten(80);

## 服务器nginx环境配置

1. nginx 依赖下载： yum -y install gcc zlib zlib-devel pcre-devel openssl openssl-devel

2. 下载解压 nginx 安装包： wget http://nginx.org/download/nginx-1.13.7.tar.gz && tar -xvf nginx-1.13.7.tar.gz

3. 进入目录 添加ssl模块 安装   cd nginx-1.13.7 && ./configure --with-http_stub_status_module --with-http_ssl_module && make && make install

4. 安装目录在 /usr/local/nginx
