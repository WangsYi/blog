---
title: "Docker安装gitlab与gitlab runner"
date: 2023-05-10T16:10:11+08:00
draft: false
tags: ["gitlab"]
---

## 设置临时环境变量
> 官方的路径/srv/gitlab在我机器上会有权限问题，暂时放在了用户目录
```
export GITLAB_HOME=/root/gitlab
```

## 运行镜像

``` 
docker run --detach \
  --hostname 10.1.1.11:8880 \
  --publish 8443:443 --publish 8880:8880 --publish 8022:22 \
  --name gitlab \
  --restart always \
  --volume $GITLAB_HOME/config:/etc/gitlab \
  --volume $GITLAB_HOME/logs:/var/log/gitlab \
  --volume $GITLAB_HOME/data:/var/opt/gitlab \
  --shm-size 256m \
  gitlab/gitlab-ce:latest
  
  ```
> hostname中如果有端口，与 -p 8880:8880，这三个端口要一致，不然可能会有问题，具体原因没研究
## 获取密码登录
  ```
  docker exec -it gitlab grep 'Password:' /etc/gitlab/initial_root_password
  ```


## 安装runner
> /srv权限问题，改了

### 运行
  ```
  docker run -d --name gitlab-runner --restart always \
  -v /root/gitlab-runner/config:/etc/gitlab-runner \
  -v /var/run/docker.sock:/var/run/docker.sock \
  gitlab/gitlab-runner:latest
  ```
### 注册runner
```
docker run --rm -it -v /root/gitlab-runner/config:/etc/gitlab-runner gitlab/gitlab-runner register
```
### 重启
`docker restart gitlab-runner`
