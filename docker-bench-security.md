```
hp@Cyndie:~$ docker images
REPOSITORY    TAG       IMAGE ID       CREATED         SIZE
ubuntu        latest    58db3edaf2be   5 weeks ago     77.8MB
hello-world   latest    feb5d9fea6a5   17 months ago   13.3kB
hp@Cyndie:~$ docker ps -a
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
hp@Cyndie:~$ docker pull soaringswine/lazyrecon_docker
Using default tag: latest
latest: Pulling from soaringswine/lazyrecon_docker
7ddbc47eeb70: Pull complete 
c1bbdc448b72: Pull complete 
8c3b70e39044: Pull complete 
45d437916d57: Pull complete 
f654d2687cae: Pull complete 
6873ed8dfa50: Pull complete 
c4d48f4186bc: Pull complete 
2055bcbd6f82: Pull complete 
a50daaff89ff: Pull complete 
a7b404c21e86: Pull complete 
f8ab6277e282: Pull complete 
46edeb6ee2ac: Pull complete 
5caf9012322f: Pull complete 
126b6908b9b3: Pull complete 
92834742d865: Pull complete 
885df031229d: Pull complete 
4d333a5411a1: Pull complete 
15f772fbf8df: Pull complete 
c7571f2e3a3f: Pull complete 
dcebad2f1ce5: Pull complete 
8f6bab6ae278: Pull complete 
83c9c435374b: Pull complete 
f528c3681329: Pull complete 
Digest: sha256:04beaab98d33ae845156ec0f14bad306040a2bc88a9930fabd257fb8e8324f2e
Status: Downloaded newer image for soaringswine/lazyrecon_docker:latest
docker.io/soaringswine/lazyrecon_docker:latest
hp@Cyndie:~$ docker pull crapi/crapi-workshop
Using default tag: latest
latest: Pulling from crapi/crapi-workshop
9621f1afde84: Pull complete 
7dcbe358f5cf: Pull complete 
71eabd403984: Pull complete 
f8d8c03363a5: Pull complete 
c4cb4cbcdacf: Pull complete 
7680e9a25a6d: Pull complete 
4f4fb700ef54: Pull complete 
4a4a2030658a: Pull complete 
ccd01ce5f892: Pull complete 
Digest: sha256:6e5aa7561f55ef767e3174ac56c7fcdd73cde42ca7fa5556f8e5773adb3a3ef0
Status: Downloaded newer image for crapi/crapi-workshop:latest
docker.io/crapi/crapi-workshop:latest
hp@Cyndie:~$ docker pull crapi/crapi-community
Using default tag: latest
latest: Pulling from crapi/crapi-community
ca7dd9ec2225: Pull complete 
d795d5628a61: Pull complete 
8ac530d516ad: Pull complete 
a76194326b17: Pull complete 
4f4fb700ef54: Pull complete 
Digest: sha256:92a0037e15c0bf13b6e933c373fc613ee98def0710b6e5fb7e4017557341a0db
Status: Downloaded newer image for crapi/crapi-community:latest
docker.io/crapi/crapi-community:latest
hp@Cyndie:~$ docker images
REPOSITORY                      TAG       IMAGE ID       CREATED         SIZE
ubuntu                          latest    58db3edaf2be   5 weeks ago     77.8MB
crapi/crapi-community           latest    1f83439a7b13   3 months ago    25.3MB
crapi/crapi-workshop            latest    43b6816e76c6   3 months ago    107MB
hello-world                     latest    feb5d9fea6a5   17 months ago   13.3kB
soaringswine/lazyrecon_docker   latest    2d4710ed0553   3 years ago     1.15GB
hp@Cyndie:~$ git clone https://github.com/docker/docker-bench-security.git
Cloning into 'docker-bench-security'...
remote: Enumerating objects: 2525, done.
remote: Counting objects: 100% (603/603), done.
remote: Compressing objects: 100% (152/152), done.
remote: Total 2525 (delta 489), reused 459 (delta 451), pack-reused 1922
Receiving objects: 100% (2525/2525), 4.12 MiB | 2.55 MiB/s, done.
Resolving deltas: 100% (1767/1767), done.
hp@Cyndie:~$ ls
Desktop                Downloads         getting-started  package-lock.json            Public     Videos
docker-bench-security  examples.desktop  marketplace      packages-microsoft-prod.deb  snap       vmware
Documents              friend            Music            Pictures                     Templates
hp@Cyndie:~$ cd docker-bench-security/
hp@Cyndie:~/docker-bench-security$ docker build --no-cache -t docker-bench-security .
[+] Building 20.2s (3/3) FINISHED                                                                                                      
 => [internal] load .dockerignore                                                                                                 0.2s
 => => transferring context: 100B                                                                                                 0.0s
 => [internal] load build definition from Dockerfile                                                                              0.2s
 => => transferring dockerfile: 508B                                                                                              0.0s
 => ERROR [internal] load metadata for docker.io/library/alpine:3.15                                                             20.0s
------
 > [internal] load metadata for docker.io/library/alpine:3.15:
------
Dockerfile:1
--------------------
   1 | >>> FROM alpine:3.15
   2 |     
   3 |     LABEL \
--------------------
ERROR: failed to solve: alpine:3.15: failed to do request: Head "https://registry-1.docker.io/v2/library/alpine/manifests/3.15": dial tcp: lookup registry-1.docker.io: no such host
hp@Cyndie:~/docker-bench-security$ ls
CONTRIBUTING.md  distros                   docker-compose.yml  functions  LICENSE.md   README.md  Vagrantfile
CONTRIBUTORS.md  docker-bench-security.sh  Dockerfile          img        MAINTAINERS  tests
hp@Cyndie:~/docker-bench-security$ docker-compose run --rm docker-bench-security

Command 'docker-compose' not found, but can be installed with:

sudo snap install docker          # version 20.10.17, or
sudo apt  install docker-compose  # version 1.25.0-1

See 'snap info docker' for additional versions.

hp@Cyndie:~/docker-bench-security$ sudo apt  install docker-compose
[sudo] password for hp: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  python3-attr python3-cached-property python3-docker python3-dockerpty python3-docopt python3-importlib-metadata python3-jsonschema
  python3-more-itertools python3-pyrsistent python3-texttable python3-websocket python3-zipp
Suggested packages:
  python-attr-doc python-jsonschema-doc
Recommended packages:
  docker.io
The following NEW packages will be installed:
  docker-compose python3-attr python3-cached-property python3-docker python3-dockerpty python3-docopt python3-importlib-metadata
  python3-jsonschema python3-more-itertools python3-pyrsistent python3-texttable python3-websocket python3-zipp
0 upgraded, 13 newly installed, 0 to remove and 8 not upgraded.
Need to get 445 kB of archives.
After this operation, 2,574 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ke.archive.ubuntu.com/ubuntu focal/universe amd64 python3-cached-property all 1.5.1-4 [10.9 kB]
Get:2 http://ke.archive.ubuntu.com/ubuntu focal/universe amd64 python3-websocket all 0.53.0-2ubuntu1 [32.3 kB]
Get:3 http://ke.archive.ubuntu.com/ubuntu focal/universe amd64 python3-docker all 4.1.0-1 [83.8 kB]
Get:4 http://ke.archive.ubuntu.com/ubuntu focal/universe amd64 python3-dockerpty all 0.4.1-2 [11.1 kB]
Get:5 http://ke.archive.ubuntu.com/ubuntu focal/universe amd64 python3-docopt all 0.6.2-2.2ubuntu1 [19.7 kB]
Get:6 http://ke.archive.ubuntu.com/ubuntu focal/main amd64 python3-attr all 19.3.0-2 [33.9 kB]
Get:7 http://ke.archive.ubuntu.com/ubuntu focal/main amd64 python3-more-itertools all 4.2.0-1build1 [39.4 kB]
Get:8 http://ke.archive.ubuntu.com/ubuntu focal/main amd64 python3-zipp all 1.0.0-1 [5,312 B]
Get:9 http://ke.archive.ubuntu.com/ubuntu focal/main amd64 python3-importlib-metadata all 1.5.0-1 [9,992 B]
Get:10 http://ke.archive.ubuntu.com/ubuntu focal/main amd64 python3-pyrsistent amd64 0.15.5-1build1 [52.1 kB]
Get:11 http://ke.archive.ubuntu.com/ubuntu focal/main amd64 python3-jsonschema all 3.2.0-0ubuntu2 [43.1 kB]
Get:12 http://ke.archive.ubuntu.com/ubuntu focal/universe amd64 python3-texttable all 1.6.2-2 [11.0 kB]
Get:13 http://ke.archive.ubuntu.com/ubuntu focal/universe amd64 docker-compose all 1.25.0-1 [92.7 kB]
Fetched 445 kB in 3s (142 kB/s)           
Selecting previously unselected package python3-cached-property.
(Reading database ... 230819 files and directories currently installed.)
Preparing to unpack .../00-python3-cached-property_1.5.1-4_all.deb ...
Unpacking python3-cached-property (1.5.1-4) ...
Selecting previously unselected package python3-websocket.
Preparing to unpack .../01-python3-websocket_0.53.0-2ubuntu1_all.deb ...
Unpacking python3-websocket (0.53.0-2ubuntu1) ...
Selecting previously unselected package python3-docker.
Preparing to unpack .../02-python3-docker_4.1.0-1_all.deb ...
Unpacking python3-docker (4.1.0-1) ...
Selecting previously unselected package python3-dockerpty.
Preparing to unpack .../03-python3-dockerpty_0.4.1-2_all.deb ...
Unpacking python3-dockerpty (0.4.1-2) ...
Selecting previously unselected package python3-docopt.
Preparing to unpack .../04-python3-docopt_0.6.2-2.2ubuntu1_all.deb ...
Unpacking python3-docopt (0.6.2-2.2ubuntu1) ...
Selecting previously unselected package python3-attr.
Preparing to unpack .../05-python3-attr_19.3.0-2_all.deb ...
Unpacking python3-attr (19.3.0-2) ...
Selecting previously unselected package python3-more-itertools.
Preparing to unpack .../06-python3-more-itertools_4.2.0-1build1_all.deb ...
Unpacking python3-more-itertools (4.2.0-1build1) ...
Selecting previously unselected package python3-zipp.
Preparing to unpack .../07-python3-zipp_1.0.0-1_all.deb ...
Unpacking python3-zipp (1.0.0-1) ...
Selecting previously unselected package python3-importlib-metadata.
Preparing to unpack .../08-python3-importlib-metadata_1.5.0-1_all.deb ...
Unpacking python3-importlib-metadata (1.5.0-1) ...
Selecting previously unselected package python3-pyrsistent:amd64.
Preparing to unpack .../09-python3-pyrsistent_0.15.5-1build1_amd64.deb ...
Unpacking python3-pyrsistent:amd64 (0.15.5-1build1) ...
Selecting previously unselected package python3-jsonschema.
Preparing to unpack .../10-python3-jsonschema_3.2.0-0ubuntu2_all.deb ...
Unpacking python3-jsonschema (3.2.0-0ubuntu2) ...
Selecting previously unselected package python3-texttable.
Preparing to unpack .../11-python3-texttable_1.6.2-2_all.deb ...
Unpacking python3-texttable (1.6.2-2) ...
Selecting previously unselected package docker-compose.
Preparing to unpack .../12-docker-compose_1.25.0-1_all.deb ...
Unpacking docker-compose (1.25.0-1) ...
Setting up python3-cached-property (1.5.1-4) ...
Setting up python3-more-itertools (4.2.0-1build1) ...
Setting up python3-attr (19.3.0-2) ...
Setting up python3-texttable (1.6.2-2) ...
Setting up python3-docopt (0.6.2-2.2ubuntu1) ...
Setting up python3-zipp (1.0.0-1) ...
Setting up python3-pyrsistent:amd64 (0.15.5-1build1) ...
Setting up python3-websocket (0.53.0-2ubuntu1) ...
update-alternatives: using /usr/bin/python3-wsdump to provide /usr/bin/wsdump (wsdump) in auto mode
Setting up python3-dockerpty (0.4.1-2) ...
Setting up python3-importlib-metadata (1.5.0-1) ...
Setting up python3-docker (4.1.0-1) ...
Setting up python3-jsonschema (3.2.0-0ubuntu2) ...
Setting up docker-compose (1.25.0-1) ...
Processing triggers for man-db (2.9.1-1) ...
hp@Cyndie:~/docker-bench-security$ docker-compose run --rm docker-bench-security
Building docker-bench-security
Step 1/8 : FROM alpine:3.15
3.15: Pulling from library/alpine
895e193edb51: Pull complete
Digest: sha256:689659b1f08e9fdfb85190144098c378beb5a53b328f7ced7883a74a1157c709
Status: Downloaded newer image for alpine:3.15
 ---> 5ce65d7b0fde
Step 2/8 : LABEL   org.label-schema.name="docker-bench-security"   org.label-schema.url="https://dockerbench.com"   org.label-schema.vcs-url="https://github.com/docker/docker-bench-security.git"
 ---> Running in 865d48bb703b
Removing intermediate container 865d48bb703b
 ---> c8df46a73604
Step 3/8 : RUN apk add --no-cache iproute2                        docker-cli                        dumb-init
 ---> Running in 0cee73de1b05
fetch https://dl-cdn.alpinelinux.org/alpine/v3.15/main/x86_64/APKINDEX.tar.gz
fetch https://dl-cdn.alpinelinux.org/alpine/v3.15/community/x86_64/APKINDEX.tar.gz
(1/14) Installing ca-certificates (20220614-r0)
(2/14) Installing docker-cli (20.10.16-r0)
(3/14) Installing dumb-init (1.2.5-r1)
(4/14) Installing iproute2 (5.15.0-r0)
Executing iproute2-5.15.0-r0.post-install
(5/14) Installing libbz2 (1.0.8-r1)
(6/14) Installing fts (1.2.7-r1)
(7/14) Installing xz-libs (5.2.5-r1)
(8/14) Installing libelf (0.185-r0)
(9/14) Installing libmnl (1.0.4-r2)
(10/14) Installing libnftnl (1.2.1-r0)
(11/14) Installing iptables (1.8.7-r1)
(12/14) Installing iproute2-tc (5.15.0-r0)
(13/14) Installing iproute2-minimal (5.15.0-r0)
(14/14) Installing iproute2-ss (5.15.0-r0)
Executing busybox-1.34.1-r7.trigger
Executing ca-certificates-20220614-r0.trigger
OK: 62 MiB in 28 packages
Removing intermediate container 0cee73de1b05
 ---> 1ad1b791c4d1
Step 4/8 : COPY . /usr/local/bin/
 ---> 35f80c11b860
Step 5/8 : HEALTHCHECK CMD exit 0
 ---> Running in b1fce22cc73a
Removing intermediate container b1fce22cc73a
 ---> 07e98eb1d549
Step 6/8 : WORKDIR /usr/local/bin
 ---> Running in c8c522a47725
Removing intermediate container c8c522a47725
 ---> afac2f17b95a
Step 7/8 : ENTRYPOINT [ "/usr/bin/dumb-init", "/bin/sh", "docker-bench-security.sh" ]
 ---> Running in b77f42dcd0a9
Removing intermediate container b77f42dcd0a9
 ---> 7c0d59f05c0a
Step 8/8 : CMD [""]
 ---> Running in ff737af95c39
Removing intermediate container ff737af95c39
 ---> 1fca6beaeb5f
Successfully built 1fca6beaeb5f
Successfully tagged docker-bench-security_docker-bench-security:latest
WARNING: Image for service docker-bench-security was built because it did not already exist. To rebuild this image you must use `docker-compose build` or `docker-compose up --build`.
# --------------------------------------------------------------------------------------------
# Docker Bench for Security v1.3.6
#
# Docker, Inc. (c) 2015-2023
#
# Checks for dozens of common best-practices around deploying Docker containers in production.
# Based on the CIS Docker Benchmark 1.4.0.
# --------------------------------------------------------------------------------------------

Initializing 2023-03-04T10:01:04


Section A - Check results

[INFO] 1 - Host Configuration
[INFO] 1.1 - Linux Hosts Specific Configuration
WARNING: No swap limit support
[WARN] 1.1.1 - Ensure a separate partition for containers has been created (Automated)
[INFO] 1.1.2 - Ensure only trusted users are allowed to control Docker daemon (Automated)
[INFO]       * Users: hp
[WARN] 1.1.3 - Ensure auditing is configured for the Docker daemon (Automated)
[WARN] 1.1.4 - Ensure auditing is configured for Docker files and directories -/run/containerd (Automated)
[WARN] 1.1.5 - Ensure auditing is configured for Docker files and directories - /var/lib/docker (Automated)
[WARN] 1.1.6 - Ensure auditing is configured for Docker files and directories - /etc/docker (Automated)
[INFO] 1.1.7 - Ensure auditing is configured for Docker files and directories - docker.service (Automated)
[INFO]        * File not found
[INFO] 1.1.8 - Ensure auditing is configured for Docker files and directories - containerd.sock (Automated)
[INFO]        * File not found
[INFO] 1.1.9 - Ensure auditing is configured for Docker files and directories - docker.socket (Automated)
[INFO]        * File not found
[WARN] 1.1.10 - Ensure auditing is configured for Docker files and directories - /etc/default/docker (Automated)
[WARN] 1.1.11 - Ensure auditing is configured for Dockerfiles and directories - /etc/docker/daemon.json (Automated)
[WARN] 1.1.12 - 1.1.12 Ensure auditing is configured for Dockerfiles and directories - /etc/containerd/config.toml (Automated)
[INFO] 1.1.13 - Ensure auditing is configured for Docker files and directories - /etc/sysconfig/docker (Automated)
[INFO]        * File not found
[INFO] 1.1.14 - Ensure auditing is configured for Docker files and directories - /usr/bin/containerd (Automated)
[INFO]         * File not found
[INFO] 1.1.15 - Ensure auditing is configured for Docker files and directories - /usr/bin/containerd-shim (Automated)
[INFO]         * File not found
[INFO] 1.1.16 - Ensure auditing is configured for Docker files and directories - /usr/bin/containerd-shim-runc-v1 (Automated)
[INFO]         * File not found
[INFO] 1.1.17 - Ensure auditing is configured for Docker files and directories - /usr/bin/containerd-shim-runc-v2 (Automated)
[INFO]         * File not found
[INFO] 1.1.18 - Ensure auditing is configured for Docker files and directories - /usr/bin/runc (Automated)
[INFO]         * File not found
[INFO] 1.2 - General Configuration
[NOTE] 1.2.1 - Ensure the container host has been Hardened (Manual)
[PASS] 1.2.2 - Ensure that the version of Docker is up to date (Manual)
[INFO]        * Using 23.0.1, verify is it up to date as deemed necessary

[INFO] 2 - Docker daemon configuration
[NOTE] 2.1 - Run the Docker daemon as a non-root user, if possible (Manual)
[WARN] 2.2 - Ensure network traffic is restricted between containers on the default bridge (Scored)
[PASS] 2.3 - Ensure the logging level is set to 'info' (Scored)
[PASS] 2.4 - Ensure Docker is allowed to make changes to iptables (Scored)
[PASS] 2.5 - Ensure insecure registries are not used (Scored)
[PASS] 2.6 - Ensure aufs storage driver is not used (Scored)
[INFO] 2.7 - Ensure TLS authentication for Docker daemon is configured (Scored)
[INFO]      * Docker daemon not listening on TCP
[INFO] 2.8 - Ensure the default ulimit is configured appropriately (Manual)
[INFO]      * Default ulimit doesn't appear to be set
[WARN] 2.9 - Enable user namespace support (Scored)
[PASS] 2.10 - Ensure the default cgroup usage has been confirmed (Scored)
[PASS] 2.11 - Ensure base device size is not changed until needed (Scored)
[WARN] 2.12 - Ensure that authorization for Docker client commands is enabled (Scored)
[WARN] 2.13 - Ensure centralized and remote logging is configured (Scored)
[WARN] 2.14 - Ensure containers are restricted from acquiring new privileges (Scored)
[WARN] 2.15 - Ensure live restore is enabled (Scored)
[WARN] 2.16 - Ensure Userland Proxy is Disabled (Scored)
[INFO] 2.17 - Ensure that a daemon-wide custom seccomp profile is applied if appropriate (Manual)
[INFO] Ensure that experimental features are not implemented in production (Scored) (Deprecated)

[INFO] 3 - Docker daemon configuration files
[INFO] 3.1 - Ensure that the docker.service file ownership is set to root:root (Automated)
[INFO]      * File not found
[INFO] 3.2 - Ensure that docker.service file permissions are appropriately set (Automated)
[INFO]      * File not found
[INFO] 3.3 - Ensure that docker.socket file ownership is set to root:root (Automated)
[INFO]      * File not found
[INFO] 3.4 - Ensure that docker.socket file permissions are set to 644 or more restrictive (Automated)
[INFO]      * File not found
[PASS] 3.5 - Ensure that the /etc/docker directory ownership is set to root:root (Automated)
[PASS] 3.6 - Ensure that /etc/docker directory permissions are set to 755 or more restrictively (Automated)
[INFO] 3.7 - Ensure that registry certificate file ownership is set to root:root (Automated)
[INFO]      * Directory not found
[INFO] 3.8 - Ensure that registry certificate file permissions are set to 444 or more restrictively (Automated)
[INFO]      * Directory not found
[INFO] 3.9 - Ensure that TLS CA certificate file ownership is set to root:root (Automated)
[INFO]      * No TLS CA certificate found
[INFO] 3.10 - Ensure that TLS CA certificate file permissions are set to 444 or more restrictively (Automated)
[INFO]       * No TLS CA certificate found
[INFO] 3.11 - Ensure that Docker server certificate file ownership is set to root:root (Automated)
[INFO]       * No TLS Server certificate found
[INFO] 3.12 - Ensure that the Docker server certificate file permissions are set to 444 or more restrictively (Automated)
[INFO]       * No TLS Server certificate found
[INFO] 3.13 - Ensure that the Docker server certificate key file ownership is set to root:root (Automated)
[INFO]       * No TLS Key found
[INFO] 3.14 - Ensure that the Docker server certificate key file permissions are set to 400 (Automated)
[INFO]       * No TLS Key found
[PASS] 3.15 - Ensure that the Docker socket file ownership is set to root:docker (Automated)
[PASS] 3.16 - Ensure that the Docker socket file permissions are set to 660 or more restrictively (Automated)
[PASS] 3.17 - Ensure that the daemon.json file ownership is set to root:root (Automated)
[PASS] 3.18 - Ensure that daemon.json file permissions are set to 644 or more restrictive (Automated)
[PASS] 3.19 - Ensure that the /etc/default/docker file ownership is set to root:root (Automated)
[INFO] 3.20 - Ensure that the /etc/sysconfig/docker file permissions are set to 644 or more restrictively (Automated)
[INFO]       * File not found
[INFO] 3.21 - Ensure that the /etc/sysconfig/docker file ownership is set to root:root (Automated)
[INFO]       * File not found
[PASS] 3.22 - Ensure that the /etc/default/docker file permissions are set to 644 or more restrictively (Automated)
[INFO] 3.23 - Ensure that the Containerd socket file ownership is set to root:root (Automated)
[INFO]       * File not found
[INFO] 3.24 - Ensure that the Containerd socket file permissions are set to 660 or more restrictively (Automated)
[INFO]       * File not found

[INFO] 4 - Container Images and Build File
[INFO] 4.1 - Ensure that a user for the container has been created (Automated)
[INFO]      * No containers running
[NOTE] 4.2 - Ensure that containers use only trusted base images (Manual)
[NOTE] 4.3 - Ensure that unnecessary packages are not installed in the container (Manual)
[NOTE] 4.4 - Ensure images are scanned and rebuilt to include security patches (Manual)
[WARN] 4.5 - Ensure Content trust for Docker is Enabled (Automated)
[WARN] 4.6 - Ensure that HEALTHCHECK instructions have been added to container images (Automated)
[WARN]      * No Healthcheck found: [alpine:3.15]
[WARN]      * No Healthcheck found: [ubuntu:latest]
[WARN]      * No Healthcheck found: [crapi/crapi-community:latest]
[WARN]      * No Healthcheck found: [crapi/crapi-workshop:latest]
[WARN]      * No Healthcheck found: [hello-world:latest]
[WARN]      * No Healthcheck found: [soaringswine/lazyrecon_docker:latest]
[INFO] 4.7 - Ensure update instructions are not used alone in the Dockerfile (Manual)
[INFO]      * Update instruction found: [crapi/crapi-community:latest]
[INFO]      * Update instruction found: [crapi/crapi-workshop:latest]
[INFO]      * Update instruction found: [soaringswine/lazyrecon_docker:latest]
[NOTE] 4.8 - Ensure setuid and setgid permissions are removed (Manual)
[INFO] 4.9 - Ensure that COPY is used instead of ADD in Dockerfiles (Manual)
[INFO]      * ADD in image history: [ubuntu:latest]
[NOTE] 4.10 - Ensure secrets are not stored in Dockerfiles (Manual)
[NOTE] 4.11 - Ensure only verified packages are installed (Manual)
[NOTE] 4.12 - Ensure all signed artifacts are validated (Manual)

[INFO] 5 - Container Runtime
[INFO]   * No containers running, skipping Section 5

[INFO] 6 - Docker Security Operations
[INFO] 6.1 - Ensure that image sprawl is avoided (Manual)
[INFO]      * There are currently: 7 images
[INFO]      * Only 1 out of 7 are in use
[INFO] 6.2 - Ensure that container sprawl is avoided (Manual)
[INFO]      * There are currently a total of 1 containers, with 1 of them currently running

[INFO] 7 - Docker Swarm Configuration
[PASS] 7.1 - Ensure swarm mode is not Enabled, if not needed (Automated)
[PASS] 7.2 - Ensure that the minimum number of manager nodes have been created in a swarm (Automated) (Swarm mode not enabled)
[PASS] 7.3 - Ensure that swarm services are bound to a specific host interface (Automated) (Swarm mode not enabled)
[PASS] 7.4 - Ensure that all Docker swarm overlay networks are encrypted (Automated)
[PASS] 7.5 - Ensure that Docker's secret management commands are used for managing secrets in a swarm cluster (Manual) (Swarm mode not enabled)
[PASS] 7.6 - Ensure that swarm manager is run in auto-lock mode (Automated) (Swarm mode not enabled)
[PASS] 7.7 - Ensure that the swarm manager auto-lock key is rotated periodically (Manual) (Swarm mode not enabled)
[PASS] 7.8 - Ensure that node certificates are rotated as appropriate (Manual) (Swarm mode not enabled)
[PASS] 7.9 - Ensure that CA certificates are rotated as appropriate (Manual) (Swarm mode not enabled)
[PASS] 7.10 - Ensure that management plane traffic is separated from data plane traffic (Manual) (Swarm mode not enabled)


Section C - Score

[INFO] Checks: 86
[INFO] Score: 2

```
