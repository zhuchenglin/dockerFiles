# go的基础环境
written by zhuchenglin
### 更换go代码包
1. 从https://studygolang.com/dl网站下载对应的代码包 
2. 修改Dockerfile 中 wget 和 tar 路径

#####运行
1. 进入/DockerFiles/goBaseEnv目录
2.  
```shell script
        docker build -t name:版本  .
        docker run -dit \           
        -p 80:80 -p 443:443 -p 3306:3306 -p 9000:9000 --privileged=true name:版本
```
3. 进入容器
```shell script
    docker exec -it 容器id /bin/bash 
```