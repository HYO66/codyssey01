# 터미널 기본 조작 로그

## 실행 명령 및 출력

Windows PowerShell
Copyright (C) Microsoft Corporation. All rights reserved.

PS C:\Users\User\Desktop\codyssey01> Get-Location

Path
----
C:\Users\User\Desktop\codyssey01


PS C:\Users\User\Desktop\codyssey01> Get-ChildItem -Force
PS C:\Users\User\Desktop\codyssey01> mkdir cli-test


    디렉터리: C:\Users\User\Desktop\codyssey01


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2026-11-01   오후 2:19                cli-test


PS C:\Users\User\Desktop\codyssey01> Set-Location cli-test
PS C:\Users\User\Desktop\codyssey01\cli-test> New-Item -ItemType File empty.txt


    디렉터리: C:\Users\User\Desktop\codyssey01\cli-test


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----      2026-11-01   오후 2:19              0 empty.txt


PS C:\Users\User\Desktop\codyssey01\cli-test> Set-Content empty.txt "hello world"
PS C:\Users\User\Desktop\codyssey01\cli-test> Get-Content empty.txt
hello world
PS C:\Users\User\Desktop\codyssey01\cli-test> Copy-Item empty.txt copy.txt
PS C:\Users\User\Desktop\codyssey01\cli-test> Move-Item copy.txt renamed.txt
PS C:\Users\User\Desktop\codyssey01\cli-test> Get-ChildItem


    디렉터리: C:\Users\User\Desktop\codyssey01\cli-test


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----      2026-11-01   오후 2:19             13 empty.txt
-a----      2026-11-01   오후 2:19             13 renamed.txt


PS C:\Users\User\Desktop\codyssey01\cli-test> Set-Location ..
PS C:\Users\User\Desktop\codyssey01> Remove-Item cli-test -Recurse -Force

## 권한 실습 로그

rlagytlr104@5F-115:~$ mkdir -p ~/permission-test
rlagytlr104@5F-115:~$ cd ~/permission-test
rlagytlr104@5F-115:~/permission-test$ touch sample.txt
rlagytlr104@5F-115:~/permission-test$ mkdir sampledir
rlagytlr104@5F-115:~/permission-test$ ls -ld sample.txt sampledir
-rw-r--r-- 1 rlagytlr104 rlagytlr104    0 Nov  1 14:49 sample.txt
drwxr-xr-x 2 rlagytlr104 rlagytlr104 4096 Nov  1 14:49 sampledir
rlagytlr104@5F-115:~/permission-test$ chmod 644 sample.txt
rlagytlr104@5F-115:~/permission-test$ chmod 755 sampledir
rlagytlr104@5F-115:~/permission-test$ ls -ld sample.txt sampledir
-rw-r--r-- 1 rlagytlr104 rlagytlr104    0 Nov  1 14:49 sample.txt
drwxr-xr-x 2 rlagytlr104 rlagytlr104 4096 Nov  1 14:49 sampledir
rlagytlr104@5F-115:~/permission-test$ chmod 600 sample.txt
rlagytlr104@5F-115:~/permission-test$ chmod 700 sampledir
rlagytlr104@5F-115:~/permission-test$ ls -ld sample.txt sampledir
-rw------- 1 rlagytlr104 rlagytlr104    0 Nov  1 14:49 sample.txt
drwx------ 2 rlagytlr104 rlagytlr104 4096 Nov  1 14:49 sampledir


## hello-world / ubuntu 실습 로그

PS C:\Users\User\Desktop\codyssey01> docker run --name hello-test hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
4f55086f7dd0: Pull complete
d5e71e642bf5: Download complete
Digest: sha256:c567b231f65614688711a75f31518a064258a51d442117a3e771a3a8fdba78ef
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/

PS C:\Users\User\Desktop\codyssey01> docker run -it --name ubuntu-test ubuntu bash
root@c475a98fdd1d:/# ls
bin  boot  dev  etc  home  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
root@c475a98fdd1d:/# echo hello from ubuntu container
hello from ubuntu container
root@c475a98fdd1d:/# exit
exit
PS C:\Users\User\Desktop\codyssey01> docker ps -a
CONTAINER ID   IMAGE            COMMAND                  CREATED              STATUS                      PORTS                                     NAMES
c475a98fdd1d   ubuntu           "bash"                   20 seconds ago       Exited (0) 4 seconds ago                                              ubuntu-test
a373480e6969   hello-world      "/hello"                 About a minute ago   Exited (0) 59 seconds ago                                             hello-test
c6be1ad38fe6   ubuntu           "sleep infinity"         3 hours ago          Up 3 hours                                                            vol-test2
17e7228d1122   nginx            "/docker-entrypoint.…"   4 hours ago          Up 4 hours                  0.0.0.0:8080->80/tcp, [::]:8080->80/tcp   mynginx
c744ab8e6f45   practice-image   "bash"                   45 hours ago         Exited (0) 45 hours ago                                               beautiful_murdock

참고: 아래 목록에는 이전 실습에서 생성한 다른 컨테이너도 포함되어 있으며, 본 항목에서 확인한 대상은 `hello-test`와 `ubuntu-test`이다.

## Dockerfile 기반 커스텀 이미지 제작

PS C:\Users\User\Desktop\codyssey01> docker build -t my-nginx:1.0 .
[+] Building 7.0s (7/7) FINISHED                                                                   docker:desktop-linux
 => [internal] load build definition from Dockerfile                                                               0.0s
 => => transferring dockerfile: 108B                                                                               0.0s
 => [internal] load metadata for docker.io/library/nginx:alpine                                                    2.5s
 => [internal] load .dockerignore                                                                                  0.0s
 => => transferring context: 2B                                                                                    0.0s
 => [internal] load build context                                                                                  0.1s
 => => transferring context: 282B                                                                                  0.0s
 => [1/2] FROM docker.io/library/nginx:alpine@sha256:785835ea65db4bba6f021acc0f3be91b0fef76a53fe41f8588c6698d2aed  3.1s
 => => resolve docker.io/library/nginx:alpine@sha256:785835ea65db4bba6f021acc0f3be91b0fef76a53fe41f8588c6698d2aed  0.0s
 => => sha256:b9b388a21ecfde6ac80505f23f527146a2129dfb104e79b029bbd00d4cc1a919 20.53MB / 20.53MB                   2.5s
 => => sha256:9b0f7dfe35b2711a17f60dadd6d4035dc0cdee152538cc5c0987029e94679548 1.40kB / 1.40kB                     0.5s
 => => sha256:2ec5fb117ffa9a78b15fb6a78745ffc569c8da0aee9f36ace4cd67a44b1fef79 1.21kB / 1.21kB                     0.6s
 => => sha256:26185d08a3ec318dd85a6c9f2172e714ec13cececd7f33c533b40b1689f9fedb 404B / 404B                         0.6s
 => => sha256:7cc330898115ce55acccb0cc1e7dd091df4410c8c5f3c540710ee0ac689f5fcb 964B / 964B                         0.2s
 => => sha256:657023555a2a19dc6036468198bb350d2c7feaac7f2d0a3901b4dd3cb25e40c5 629B / 629B                         0.2s
 => => sha256:12b85cff06fd7d383d36a9c96503fe049c9d4bf3dfda5cbb9ffa6ae99b9c07a6 1.94MB / 1.94MB                     0.6s
 => => sha256:7b229517ed222597277036d94892173207d01a731ab3a88eeb1de2e963a2c788 3.85MB / 3.85MB                     0.9s
 => => extracting sha256:7b229517ed222597277036d94892173207d01a731ab3a88eeb1de2e963a2c788                          0.1s
 => => extracting sha256:12b85cff06fd7d383d36a9c96503fe049c9d4bf3dfda5cbb9ffa6ae99b9c07a6                          0.2s
 => => extracting sha256:657023555a2a19dc6036468198bb350d2c7feaac7f2d0a3901b4dd3cb25e40c5                          0.0s
 => => extracting sha256:7cc330898115ce55acccb0cc1e7dd091df4410c8c5f3c540710ee0ac689f5fcb                          0.0s
 => => extracting sha256:26185d08a3ec318dd85a6c9f2172e714ec13cececd7f33c533b40b1689f9fedb                          0.0s
 => => extracting sha256:2ec5fb117ffa9a78b15fb6a78745ffc569c8da0aee9f36ace4cd67a44b1fef79                          0.0s
 => => extracting sha256:9b0f7dfe35b2711a17f60dadd6d4035dc0cdee152538cc5c0987029e94679548                          0.0s
 => => extracting sha256:b9b388a21ecfde6ac80505f23f527146a2129dfb104e79b029bbd00d4cc1a919                          0.3s
 => [2/2] COPY app/index.html /usr/share/nginx/html/index.html                                                     0.1s
 => exporting to image                                                                                             1.0s
 => => exporting layers                                                                                            0.1s
 => => exporting manifest sha256:5bcf2cfe015e64dd406e122966b71b72743404aaaf02cec788765a4c5dceee6a                  0.0s
 => => exporting config sha256:46c978ae1255008b4aad4fcfcdd4be655d116d9dcfde9a0650352416b2f785b7                    0.0s
 => => exporting attestation manifest sha256:f7c4dbdf97b836bc59698b729775e3d331cdab2b83afa152cbea662233a2de49      0.0s
 => => exporting manifest list sha256:32d72b76e6d89b55ae6630a314d7951045ab634e8e25cf0ef25e88576abfd019             0.0s
 => => naming to docker.io/library/my-nginx:1.0                                                                    0.0s
 => => unpacking to docker.io/library/my-nginx:1.0                                                                 0.7s
PS C:\Users\User\Desktop\codyssey01> docker run -d --name my-nginx-web -p 8080:80 my-nginx:1.0
908982233e4b704ed125239c5af33e744c5e9c194696620f24dd32a102fc70bf
docker: Error response from daemon: failed to set up container networking: driver failed programming external connectivity on endpoint my-nginx-web (0667aa13586c920dde03436ebf9193c21b5941291717151e529028945a758a56): Bind for 0.0.0.0:8080 failed: port is already allocated

Run 'docker run --help' for more information

What's next:
    Debug this container error with Gordon → docker ai "help me fix this container error"
PS C:\Users\User\Desktop\codyssey01> docker ps
CONTAINER ID   IMAGE     COMMAND                  CREATED       STATUS       PORTS                                     NAMES
c6be1ad38fe6   ubuntu    "sleep infinity"         4 hours ago   Up 4 hours                                             vol-test2
17e7228d1122   nginx     "/docker-entrypoint.…"   4 hours ago   Up 4 hours   0.0.0.0:8080->80/tcp, [::]:8080->80/tcp   mynginx
PS C:\Users\User\Desktop\codyssey01> docker logs my-nginx-web
PS C:\Users\User\Desktop\codyssey01> docker ps
CONTAINER ID   IMAGE     COMMAND                  CREATED       STATUS       PORTS                                     NAMES
c6be1ad38fe6   ubuntu    "sleep infinity"         4 hours ago   Up 4 hours                                             vol-test2
17e7228d1122   nginx     "/docker-entrypoint.…"   4 hours ago   Up 4 hours   0.0.0.0:8080->80/tcp, [::]:8080->80/tcp   mynginx
PS C:\Users\User\Desktop\codyssey01> docker stop mynginx
mynginx
PS C:\Users\User\Desktop\codyssey01> docker rm mynginx
mynginx
PS C:\Users\User\Desktop\codyssey01> docker ps -a
CONTAINER ID   IMAGE            COMMAND                  CREATED          STATUS                      PORTS     NAMES
908982233e4b   my-nginx:1.0     "/docker-entrypoint.…"   6 minutes ago    Created                               my-nginx-web
c475a98fdd1d   ubuntu           "bash"                   53 minutes ago   Exited (0) 53 minutes ago             ubuntu-test
a373480e6969   hello-world      "/hello"                 54 minutes ago   Exited (0) 54 minutes ago             hello-test
c6be1ad38fe6   ubuntu           "sleep infinity"         4 hours ago      Up 4 hours                            vol-test2
c744ab8e6f45   practice-image   "bash"                   46 hours ago     Exited (0) 46 hours ago               beautiful_murdock
PS C:\Users\User\Desktop\codyssey01> docker rm -f my-nginx-web
my-nginx-web
PS C:\Users\User\Desktop\codyssey01> docker run -d --name my-nginx-web -p 8080:80 my-nginx:1.0
d954290deab86ec3e535b77cc4742c02d622389e1e9ba64f717929970e2aa145
PS C:\Users\User\Desktop\codyssey01> docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED         STATUS         PORTS                                     NAMES
d954290deab8   my-nginx:1.0   "/docker-entrypoint.…"   6 seconds ago   Up 5 seconds   0.0.0.0:8080->80/tcp, [::]:8080->80/tcp   my-nginx-web
c6be1ad38fe6   ubuntu         "sleep infinity"         4 hours ago     Up 4 hours                                               vol-test2
PS C:\Users\User\Desktop\codyssey01> docker logs my-nginx-web
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Sourcing /docker-entrypoint.d/15-local-resolvers.envsh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
2026/11/01 07:13:10 [notice] 1#1: using the "epoll" event method
2026/11/01 07:13:10 [notice] 1#1: nginx/1.31.8
2026/11/01 07:13:10 [notice] 1#1: built by gcc 15.2.0 (Alpine 15.2.0)
2026/11/01 07:13:10 [notice] 1#1: OS: Linux 6.18.54.1-microsoft-standard-WSL2
2026/11/01 07:13:10 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1048576:1048576
2026/11/01 07:13:10 [notice] 1#1: start worker processes
2026/11/01 07:13:10 [notice] 1#1: start worker process 30
2026/11/01 07:13:10 [notice] 1#1: start worker process 31
2026/11/01 07:13:10 [notice] 1#1: start worker process 32
2026/11/01 07:13:10 [notice] 1#1: start worker process 33
2026/11/01 07:13:10 [notice] 1#1: start worker process 34
2026/11/01 07:13:10 [notice] 1#1: start worker process 35
2026/11/01 07:13:10 [notice] 1#1: start worker process 36
2026/11/01 07:13:10 [notice] 1#1: start worker process 37
PS C:\Users\User\Desktop\codyssey01> docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED         STATUS         PORTS                                     NAMES
d954290deab8   my-nginx:1.0   "/docker-entrypoint.…"   8 minutes ago   Up 8 minutes   0.0.0.0:8080->80/tcp, [::]:8080->80/tcp   my-nginx-web
c6be1ad38fe6   ubuntu         "sleep infinity"         4 hours ago     Up 4 hours                                               vol-test2

## 바인드 마운트 반영 확인

PS C:\Users\User\Desktop\codyssey01> docker run -d --name bind-test -p 8080:80 -v ${PWD}\app:/usr/share/nginx/html nginx
docker: Error response from daemon: Conflict. The container name "/bind-test" is already in use by container "33251dcbbf0d66443f13e79de816bc06247aa2e58d4d3dd737eb6c70e526f213". You have to remove (or rename) that container to be able to reuse that name.

Run 'docker run --help' for more information

What's next:
    Debug this container error with Gordon → docker ai "help me fix this container error"
PS C:\Users\User\Desktop\codyssey01> docker rm -f bind-test
bind-test
PS C:\Users\User\Desktop\codyssey01> docker run -d --name bind-test -p 8080:80 -v ${PWD}\app:/usr/share/nginx/html nginx

d64419362c6b3082d80259536685e0ce1b9d23b07451aa8dd538c08b50ae435e
docker: Error response from daemon: failed to set up container networking: driver failed programming external connectivity on endpoint bind-test (46f022b6c4229809d85f39671ef141143d91dd98797421758c8c5bb6879e43a5): Bind for 0.0.0.0:8080 failed: port is already allocated

Run 'docker run --help' for more information

What's next:
    Debug this container error with Gordon → docker ai "help me fix this container error"
PS C:\Users\User\Desktop\codyssey01> docker ps -a
CONTAINER ID   IMAGE            COMMAND                  CREATED             STATUS                    PORTS                                     NAMES
d64419362c6b   nginx            "/docker-entrypoint.…"   41 seconds ago      Created                                                             bind-test
d954290deab8   my-nginx:1.0     "/docker-entrypoint.…"   About an hour ago   Up About an hour          0.0.0.0:8080->80/tcp, [::]:8080->80/tcp   my-nginx-web
c475a98fdd1d   ubuntu           "bash"                   2 hours ago         Exited (0) 2 hours ago                                              ubuntu-test
a373480e6969   hello-world      "/hello"                 2 hours ago         Exited (0) 2 hours ago                                              hello-test
c6be1ad38fe6   ubuntu           "sleep infinity"         5 hours ago         Up 5 hours                                                          vol-test2
c744ab8e6f45   practice-image   "bash"                   47 hours ago        Exited (0) 47 hours ago                                             beautiful_murdock
PS C:\Users\User\Desktop\codyssey01> docker rm -f bind-test
bind-test
PS C:\Users\User\Desktop\codyssey01>  docker ps -a
CONTAINER ID   IMAGE            COMMAND                  CREATED             STATUS                    PORTS                                     NAMES
d954290deab8   my-nginx:1.0     "/docker-entrypoint.…"   About an hour ago   Up About an hour          0.0.0.0:8080->80/tcp, [::]:8080->80/tcp   my-nginx-web
c475a98fdd1d   ubuntu           "bash"                   2 hours ago         Exited (0) 2 hours ago                                              ubuntu-test
a373480e6969   hello-world      "/hello"                 2 hours ago         Exited (0) 2 hours ago                                              hello-test
c6be1ad38fe6   ubuntu           "sleep infinity"         5 hours ago         Up 5 hours                                                          vol-test2
c744ab8e6f45   practice-image   "bash"                   47 hours ago        Exited (0) 47 hours ago                                             beautiful_murdock
PS C:\Users\User\Desktop\codyssey01> docker run -d --name bind-test -p 8080:80 -v ${PWD}\app:/usr/share/nginx/html nginx

3ef1eaaf10305a196205a70e8210092cdd4b078654a45f8e9686e8f4598662f5
docker: Error response from daemon: failed to set up container networking: driver failed programming external connectivity on endpoint bind-test (c96890ccdf8e25dd63834d06a528cebfab42f6e7e4f6dced254ab321302f226e): Bind for 0.0.0.0:8080 failed: port is already allocated

Run 'docker run --help' for more information

What's next:
    Debug this container error with Gordon → docker ai "help me fix this container error"
PS C:\Users\User\Desktop\codyssey01> docker rm -f bind-test
bind-test
PS C:\Users\User\Desktop\codyssey01> docker run -d --name bind-test -p 8082:80 -v ${PWD}\app:/usr/share/nginx/html nginx

551abed4ae1f73ff367bde0808dd55a0c5c8a1eef37dfffd5338a99512d440fa
PS C:\Users\User\Desktop\codyssey01> docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED             STATUS             PORTS                                     NAMES
551abed4ae1f   nginx          "/docker-entrypoint.…"   41 seconds ago      Up 40 seconds      0.0.0.0:8082->80/tcp, [::]:8082->80/tcp   bind-test
d954290deab8   my-nginx:1.0   "/docker-entrypoint.…"   About an hour ago   Up About an hour   0.0.0.0:8080->80/tcp, [::]:8080->80/tcp   my-nginx-web
c6be1ad38fe6   ubuntu         "sleep infinity"         5 hours ago         Up 5 hours                                                   vol-test2

## Docker볼륨 영속성 확인

PS C:\Users\User\Desktop\codyssey01> docker volume create mydata
mydata
PS C:\Users\User\Desktop\codyssey01> docker run -d --name vol-test -v mydata:/data ubuntu sleep infinity
edcfe267788ae884b66b2d0e03c75bf8104c648186a5081f5d3592da678ff079
PS C:\Users\User\Desktop\codyssey01> docker exec -it vol-test bash -lc "echo hello-volume > /data/hello.txt && cat /data/hello.txt"
hello-volume

What's next:
    Try Docker Debug for seamless, persistent debugging tools in any container or image → docker debug vol-test
    Learn more at https://docs.docker.com/go/debug-cli/
PS C:\Users\User\Desktop\codyssey01> docker rm -f vol-test
vol-test
PS C:\Users\User\Desktop\codyssey01> docker run -d --name vol-test2 -v mydata:/data ubuntu sleep infinity
docker: Error response from daemon: Conflict. The container name "/vol-test2" is already in use by container "f3c92baa184b5de0138d4fba8990c3c06b1294e5daadc7de77c980a380360f47". You have to remove (or rename) that container to be able to reuse that name.

Run 'docker run --help' for more information

What's next:
    Debug this container error with Gordon → docker ai "help me fix this container error"
PS C:\Users\User\Desktop\codyssey01> docker rm -f vol-test2
vol-test2
PS C:\Users\User\Desktop\codyssey01> docker run -d --name vol-test2 -v mydata:/data ubuntu sleep infinity
76466708e4996d3e2de4c01c153b68d5fc86835ad56bfce8b4a4cfb33c030e1b
PS C:\Users\User\Desktop\codyssey01> docker exec -it vol-test2 bash -lc "cat /data/hello.txt"
hello-volume

What's next:
    Try Docker Debug for seamless, persistent debugging tools in any container or image → docker debug vol-test2
    Learn more at https://docs.docker.com/go/debug-cli/

## Git연동 확인

PS C:\Users\User\Desktop\codyssey01> git --version
git version 2.56.0.windows.4
PS C:\Users\User\Desktop\codyssey01> git config --global user.name
HYO66
PS C:\Users\User\Desktop\codyssey01> git config --global user.email
rlagytlr104@naver.com
PS C:\Users\User\Desktop\codyssey01> git config --global init.defaultBranch
PS C:\Users\User\Desktop\codyssey01> git config --list
diff.astextplain.textconv=astextplain
filter.lfs.clean=git-lfs clean -- %f
filter.lfs.smudge=git-lfs smudge -- %f
filter.lfs.process=git-lfs filter-process
filter.lfs.required=true
http.sslbackend=schannel
core.autocrlf=true
core.fscache=true
core.symlinks=false
pull.rebase=false
credential.helper=manager
credential.https://dev.azure.com.usehttppath=true
init.defaultbranch=main
user.name=HYO66
user.email=rlagytlr104@naver.com