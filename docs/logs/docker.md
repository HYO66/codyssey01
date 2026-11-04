PS C:\Users\User\Desktop\codyssey01> docker --version
Docker version 29.9.2, build a82e528
PS C:\Users\User\Desktop\codyssey01> docker info
Client:
 Version:    29.9.2
 Context:    desktop-linux
 Debug Mode: false
 Plugins:
  agent: Docker AI Agent Runner (Docker Inc.)
    Version:  v1.152.0
    Path:     C:\Users\User\.docker\cli-plugins\docker-agent.exe
  ai: Docker AI Agent - Ask Gordon (Docker Inc.)
    Version:  v1.33.0
    Path:     C:\Users\User\.docker\cli-plugins\docker-ai.exe
  buildx: Docker Buildx (Docker Inc.)
    Version:  v0.38.1
    Path:     C:\Users\User\.docker\cli-plugins\docker-buildx.exe
  compose: Docker Compose (Docker Inc.)
    Version:  v5.6.1
    Path:     C:\Users\User\.docker\cli-plugins\docker-compose.exe
  debug: Get a shell into any image or container (Docker Inc.)
    Version:  0.49.0
    Path:     C:\Users\User\.docker\cli-plugins\docker-debug.exe
  desktop: Docker Desktop commands (Docker Inc.)
    Version:  4.97.0
    Path:     C:\Users\User\.docker\cli-plugins\docker-desktop.exe
  dhi: CLI for managing Docker Hardened Images (Docker Inc.)
    Version:  v0.0.9
    Path:     C:\Users\User\.docker\cli-plugins\docker-dhi.exe
  extension: Manages Docker extensions (Docker Inc.)
    Version:  v0.2.32
    Path:     C:\Users\User\.docker\cli-plugins\docker-extension.exe
  init: Creates Docker-related starter files for your project (Docker Inc.)
    Version:  v1.4.1
    Path:     C:\Users\User\.docker\cli-plugins\docker-init.exe
  mcp: Docker MCP Plugin (Docker Inc.)
    Version:  v0.44.2
    Path:     C:\Users\User\.docker\cli-plugins\docker-mcp.exe
  model: Docker Model Runner (Docker Inc.)
    Version:  v1.2.9
    Path:     C:\Users\User\.docker\cli-plugins\docker-model.exe
  offload: Docker Offload (Docker Inc.)
    Version:  v0.7.21
    Path:     C:\Users\User\.docker\cli-plugins\docker-offload.exe
  pass: Docker Pass Secrets Manager Plugin (beta) (Docker Inc.)
    Version:  v0.3.2
    Path:     C:\Users\User\.docker\cli-plugins\docker-pass.exe
  sandbox: "docker sandbox" is deprecated, use Docker Sandboxes instead (Docker Inc.)
    Version:  v0.13.0
    Path:     C:\Users\User\.docker\cli-plugins\docker-sandbox.exe
  scout: Docker Scout (Docker Inc.)
    Version:  v1.27.0
    Path:     C:\Users\User\.docker\cli-plugins\docker-scout.exe

Server:
 Containers: 3
  Running: 2
  Paused: 0
  Stopped: 1
 Images: 3
 Server Version: 29.9.2
 Storage Driver: overlayfs
  driver-type: io.containerd.snapshotter.v1
 Logging Driver: local
 Cgroup Driver: cgroupfs
 Cgroup Version: 2
 Plugins:
  Volume: local
  Network: bridge host ipvlan macvlan null overlay
  Log: awslogs fluentd gcplogs gelf journald json-file local splunk syslog
 CDI spec directories:
  /etc/cdi
  /var/run/cdi
 Discovered Devices:
  cdi: docker.com/gpu=webgpu
 Swarm: inactive
 Runtimes: io.containerd.runc.v2 nvidia runc
 Default Runtime: runc
 Init Binary: docker-init
 containerd version: b7a25261e029d68978bbf290df0a62fc819b3c51
 runc version: v1.5.2-0-g29dd3dc2
 init version: de40ad0
 Security Options:
  seccomp
   Profile: builtin
  cgroupns
 Kernel Version: 6.18.54.1-microsoft-standard-WSL2
 Operating System: Docker Desktop
 OSType: linux
 Architecture: x86_64
 CPUs: 8
 Total Memory: 7.605GiB
 Name: docker-desktop
 ID: fc34dcf7-b9ff-4276-9637-24050c8d73ff
 Docker Root Dir: /var/lib/docker
 Debug Mode: false
 HTTP Proxy: http.docker.internal:3128
 HTTPS Proxy: http.docker.internal:3128
 No Proxy: hubproxy.docker.internal
 Labels:
  com.docker.desktop.address=npipe://\\.\pipe\docker_cli
 Experimental: false
 Insecure Registries:
  hubproxy.docker.internal:5555
  127.0.0.0/8
  ::1/128
 Live Restore Enabled: false
 Firewall Backend: iptables

PS C:\Users\User\Desktop\codyssey01> docker images
                                                                                                    i Info →   U  In Use
IMAGE                   ID             DISK USAGE   CONTENT SIZE   EXTRA
nginx:latest            5ab5b0b01097        243MB         66.8MB    U
practice-image:latest   a0fe27f1358d        265MB         87.6MB    U
ubuntu:latest           6a06111c3b0a        163MB         45.9MB    U
PS C:\Users\User\Desktop\codyssey01> docker ps
CONTAINER ID   IMAGE     COMMAND                  CREATED       STATUS       PORTS                                     NAMES
c6be1ad38fe6   ubuntu    "sleep infinity"         3 hours ago   Up 3 hours                                             vol-test2
17e7228d1122   nginx     "/docker-entrypoint.…"   3 hours ago   Up 3 hours   0.0.0.0:8080->80/tcp, [::]:8080->80/tcp   mynginx
PS C:\Users\User\Desktop\codyssey01> docker ps -a
CONTAINER ID   IMAGE            COMMAND                  CREATED        STATUS                    PORTS                                     NAMES
c6be1ad38fe6   ubuntu           "sleep infinity"         3 hours ago    Up 3 hours                                                          vol-test2
17e7228d1122   nginx            "/docker-entrypoint.…"   3 hours ago    Up 3 hours                0.0.0.0:8080->80/tcp, [::]:8080->80/tcp   mynginx
c744ab8e6f45   practice-image   "bash"                   45 hours ago   Exited (0) 45 hours ago                                             beautiful_murdock
PS C:\Users\User\Desktop\codyssey01> docker stats --no-stream
CONTAINER ID   NAME        CPU %     MEM USAGE / LIMIT     MEM %     NET I/O         BLOCK I/O         PIDS
c6be1ad38fe6   vol-test2   0.00%     1.559MiB / 7.605GiB   0.02%     872B / 126B     139kB / 4.1kB     1
17e7228d1122   mynginx     0.00%     7.473MiB / 7.605GiB   0.10%     12kB / 6.43kB   9.03MB / 12.3kB   9  
  

- `docker --version` 결과에서 Docker 버전이 정상 출력되는 것을 확인했다.
- `docker info`에서 `Server` 섹션과 컨테이너 수 정보가 표시되어 Docker 데몬이 정상 실행 중임을 확인했다.
- 즉, 단순 설치만 된 상태가 아니라 실제 Docker 서비스가 동작 중인 환경임을 점검했다.


Docker 컨테이너 삭제(정리) 명령 및 결과  
참고: 아래 목록에는 이전 실습에서 생성한 다른 테이터가 포함되어 있음  

PS C:\Users\User\Desktop\practice\pr1> docker create --name temp-cleanup hello-world
e58e84a4535e1082ce973da2c94d82d36454558f283bdc8d545a75bd6fdee7fb
PS C:\Users\User\Desktop\practice\pr1> docker ps -a
CONTAINER ID   IMAGE            COMMAND                  CREATED         STATUS                    PORTS     NAMES
e58e84a4535e   hello-world      "/hello"                 8 seconds ago   Created                             temp-cleanup
76466708e499   ubuntu           "sleep infinity"         2 days ago      Exited (137) 2 days ago             vol-test2
551abed4ae1f   nginx            "/docker-entrypoint.…"   3 days ago      Exited (0) 2 days ago               bind-test
d954290deab8   my-nginx:1.0     "/docker-entrypoint.…"   3 days ago      Exited (0) 2 days ago               my-nginx-web
c475a98fdd1d   ubuntu           "bash"                   3 days ago      Exited (0) 3 days ago               ubuntu-test
a373480e6969   hello-world      "/hello"                 3 days ago      Exited (0) 3 days ago               hello-test
c744ab8e6f45   practice-image   "bash"                   4 days ago      Exited (0) 4 days ago               beautiful_murdock
PS C:\Users\User\Desktop\practice\pr1> docker rm temp-cleanup
temp-cleanup
PS C:\Users\User\Desktop\practice\pr1> docker ps -a
CONTAINER ID   IMAGE            COMMAND                  CREATED      STATUS                    PORTS     NAMES
76466708e499   ubuntu           "sleep infinity"         2 days ago   Exited (137) 2 days ago             vol-test2
551abed4ae1f   nginx            "/docker-entrypoint.…"   3 days ago   Exited (0) 2 days ago               bind-test
d954290deab8   my-nginx:1.0     "/docker-entrypoint.…"   3 days ago   Exited (0) 2 days ago               my-nginx-web
c475a98fdd1d   ubuntu           "bash"                   3 days ago   Exited (0) 3 days ago               ubuntu-test
a373480e6969   hello-world      "/hello"                 3 days ago   Exited (0) 3 days ago               hello-test
c744ab8e6f45   practice-image   "bash"                   4 days ago   Exited (0) 4 days ago               beautiful_murdock

결과: temp-cleanup hello-world가 성공적으로 삭제 되었음.


Docker 이미지 삭제(정리) 명령 및 결과
참고: 아래 목록에는 이전 실습에서 생성한 다른 데이터가 포함되어 있음  

PS C:\Users\User\Desktop\practice\pr1> docker images
                                                                           i Info →   U  In Use
IMAGE                   ID             DISK USAGE   CONTENT SIZE   EXTRA
hello-world:latest      c567b231f656       25.9kB         9.49kB    U
my-nginx:1.0            32d72b76e6d8       93.6MB         26.3MB    U
nginx:latest            5ab5b0b01097        243MB         66.8MB    U
practice-image:latest   a0fe27f1358d        265MB         87.6MB    U
ubuntu:latest           6a06111c3b0a        163MB         45.9MB    U
PS C:\Users\User\Desktop\practice\pr1> docker ps -a
CONTAINER ID   IMAGE            COMMAND                  CREATED      STATUS                    PORTS     NAMES
76466708e499   ubuntu           "sleep infinity"         2 days ago   Exited (137) 2 days ago             vol-test2
551abed4ae1f   nginx            "/docker-entrypoint.…"   3 days ago   Exited (0) 3 days ago               bind-test
d954290deab8   my-nginx:1.0     "/docker-entrypoint.…"   3 days ago   Exited (0) 3 days ago               my-nginx-web
c475a98fdd1d   ubuntu           "bash"                   3 days ago   Exited (0) 3 days ago               ubuntu-test
a373480e6969   hello-world      "/hello"                 3 days ago   Exited (0) 3 days ago               hello-test
c744ab8e6f45   practice-image   "bash"                   4 days ago   Exited (0) 4 days ago               beautiful_murdock
PS C:\Users\User\Desktop\practice\pr1> docker rm a373480e6969
a373480e6969
PS C:\Users\User\Desktop\practice\pr1> docker ps -a
CONTAINER ID   IMAGE            COMMAND                  CREATED      STATUS                    PORTS     NAMES
76466708e499   ubuntu           "sleep infinity"         2 days ago   Exited (137) 2 days ago             vol-test2
551abed4ae1f   nginx            "/docker-entrypoint.…"   3 days ago   Exited (0) 3 days ago               bind-test
d954290deab8   my-nginx:1.0     "/docker-entrypoint.…"   3 days ago   Exited (0) 3 days ago               my-nginx-web
c475a98fdd1d   ubuntu           "bash"                   3 days ago   Exited (0) 3 days ago               ubuntu-test
c744ab8e6f45   practice-image   "bash"                   4 days ago   Exited (0) 4 days ago               beautiful_murdock
PS C:\Users\User\Desktop\practice\pr1> docker rmi hello-world
Untagged: hello-world:latest
Deleted: sha256:c567b231f65614688711a75f31518a064258a51d442117a3e771a3a8fdba78ef
PS C:\Users\User\Desktop\practice\pr1> docker images
                                                                           i Info →   U  In Use
IMAGE                   ID             DISK USAGE   CONTENT SIZE   EXTRA
my-nginx:1.0            32d72b76e6d8       93.6MB         26.3MB    U
nginx:latest            5ab5b0b01097        243MB         66.8MB    U
practice-image:latest   a0fe27f1358d        265MB         87.6MB    U
ubuntu:latest           6a06111c3b0a        163MB         45.9MB    U