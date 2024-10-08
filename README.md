# docker镜像加速源

## 介绍
**本项目是基于cloudflare worker运行的docker镜像加速源** 

## 演示网站
### [https://docker.1panel.dev](https://docker.1panel.dev)

## 使用方法①
#### 原拉取镜像命令：
```
docker pull library/alpine:latest
```
#### 加速拉取镜像命令：
```
docker pull docker.1panel.dev/library/alpine:latest
```

## 使用方法②
#### 一键设置镜像加速：修改文件 /etc/docker/daemon.json（如果不存在则创建）
```
nano /etc/docker/daemon.json
```
#### 修改JSON文件 更改为以下内容 然后保存
```
{
  "registry-mirrors": ["https://docker.1panel.dev"]
}
```
重载systemd管理守护进程配置文件
```
sudo systemctl daemon-reload
```
重启 Docker 服务
```
sudo systemctl restart docker
```

## 使用方法③
#### 为了加速镜像拉取，使用以下命令设置registry mirror：
```
sudo tee /etc/docker/daemon.json <<EOF
{
    "registry-mirrors": ["https://docker.1panel.dev"]
}
EOF
```
重载systemd管理守护进程配置文件
```
sudo systemctl daemon-reload
```
重启 Docker 服务
```
sudo systemctl restart docker
```