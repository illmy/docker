# Docker 命令大全
## 容器生命周期管理
run  
start/stop/restart  
kill  
rm  
pause/unpause  
create  创建新容器但不启动
exec  

## 容器操作
ps  
inspect  
top  
attach  
events  
logs  
wait  
export  
port  

## 容器rootfs命令
commit  
cp  
diff  

## 镜像仓库
login  
pull  
push  
search  

## 本地镜像管理
images  
> docker image ls 列出本机的所有image文件
> docker image rm [imageName] 删除image文件  
> docker image pull library/hello-world  
> 拉取image文件 其中library为官方组，可以省略

rmi  
tag  
build  
history  
save  
load  
import  

## info|version  
info  
version  

## 使用步骤

1. 拉取image文件
> docker image pull hello-world

2. 查看image文件
> docker image ls

3. 运行image文件，创建容器
> docker run hello-word  
> docker run命令具有自动抓取 image 文件的功能。如果发现本地没有指定的 image 文件，就会从仓库自动抓取。  
> docker run -it centos /bin/bash  
> -i 交互式操作  
> -t 终端  
> -p 端口映射  
> -d 守护进程  

4. 生产的容器本身也是一个文件
> docker container ls 列出本机正在运行的容器  
> docker container ls -all 列出所有容器,包括终止的容器

5. 终止容器运行
> docker container kill [containerID]

6. 删除容器
> docker container rm [containerID]
> docker container run --rm 容器终止运行后自动删除

7. 启动已经停止的容器文件
> docker container start [containerID]

8. 停止容器运行
> docker container stop [containerID]  
> 前面的docker container kill命令终止容器运行，相当于向容器里面的主进程发出 SIGKILL 信号。而docker container stop命令也是用来终止容器运行，相当于向容器里面的主进程发出 SIGTERM 信号，然后过一段时间再发出 SIGKILL 信号。
> 这两个信号的差别是，应用程序收到 SIGTERM 信号以后，可以自行进行收尾清理工作，但也可以不理会这个信号。如果收到 SIGKILL 信号，就会强行立即终止，那些正在进行中的操作会全部丢失。

9. 查看docker容器的输出
> docker container logs [containerID]
> 查看 docker 容器的输出，即容器里面 Shell 的标准输出。如果docker run命令运行容器的时候，没有使用-it参数，就要用这个命令查看输出。

10. 进入一个正在运行的容器  
> docker container exec 
> docker container exec -it [containerID] /bin/bash  
> 如果docker run命令运行容器的时候，没有使用-it参数，就要用这个命令进入容器。一旦进入了容器，就可以在容器的 Shell 执行命令了。

11. 从正在运行的 Docker 容器里面，将文件拷贝到本机  
> docker container cp
> docker container cp [containID]:[/path/to/file] . 拷贝到当前目录

