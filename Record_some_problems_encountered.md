# 记录一些设置电脑遇到的小问题 #



#### 编码问题——菱形方块乱码 ####

用__UTF-8__打开__GBK__编码导致。在**Chrome**上安装_Set Character Encoding_插件后右键单击页面，改成用GBK即可解决。

#### 如何查看异常中断/无法中止的进程并强行退出？ ####

```powershell
top
```

然后按下 `P` 排序 CPU 使用率，按下 `M` 排序内存使用率。可以找到想要中止的进程，记住其ID，按`q`退出界面后，使用以下命令结束：

```powershell
kill 1234
kill -9 1234 # -9是强制中止
```

#### 如何关闭在X Server的页面上打开的应用？ ####

在命令行中输入：`Ctrl+C`，就可以回到命令行继续输入其他命令。

#### Docker相关 ####

- 创建Dockerfile

  ```
  touch Dockerfile
  ```

- **Dockerfile**的某种格式

  ```dockerfile
  FROM node:14-alpine
  COPY index.js /index.js #COPY source dest
  CMD node /index.js #CMD name_of_executable_app parameter
  ```

- 命令行中的构建镜像命令

  ```
  docker build -t hello-docker .
  ```

  其中`hello-docker`为镜像名称，而`.`表示目录位置。

  而后可以用`docker images`查看已有镜像。

- 运行

  `docker run hello-docker`

  或者上传到docker hub后使用`docker pull ...`来拉取自己的/直接拉取别人的镜像。

- **Docker Desktop**的使用

  简而言之，可以简化命令行的操作。

- **Volume 逻辑卷**

  容器中的数据卷不能持久化，需要利用Volume把某目录映射到宿主机的磁盘上。

- Docker Compose

  使用`docker-compose.yml`来解决各个服务的关联关系。

  执行`docker compose up`来安装各种环境。

#### Conda相关操作 ####

- 删除某一环境

  ```
  conda remove --name [name] --all #删除该环境及之中所有的软件
  ```

- 查看已有环境 & 删除特定环境

  ```
  conda env list
   
  conda env remove -p [/path/to/your/env]
  conda env remove -p /home/kuucoss/anaconda3/envs/tfpy36   #example
  ```

- 查看某一容器的文件

  - `ls -al /` 查看根目录文件

    `ls -alR /` 递归查看所有文件（_可能会太多_）

    `find / -name "*.py"` 查找特定文件

    `tree /` 以层级结构显示（需要安装 `tree`）

    **在宿主机使用 `docker exec` 也可以查看容器文件**