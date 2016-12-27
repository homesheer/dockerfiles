# Ubuntu16.04-ssh

## 使用方式： 

### 1. 通过Dockerfile生成镜像

```
docker build -t homesheer/ssh:0.0.1 .

```

### 2. 添加认证key

```
cat ~/.ssh/id_rsa.pub > authorized_keys

```

### 3. 运行容器

```
docker run -d --name ssh -p 2022:22 homesheer/ssh:0.0.1

```

### 4. 测试

```
ssh root@127.0.0.1 -p 2022

```