# Installing Docker Engine on Ubuntu

## 1. Check if there are any previous versions installed so as to remove them

```
hp@Cyndie:~$ sudo apt-get remove docker docker-engine docker.io containerd runc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'docker-engine' is not installed, so not removed
Package 'docker' is not installed, so not removed
Package 'containerd' is not installed, so not removed
Package 'runc' is not installed, so not removed
Package 'docker.io' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

```

## 2. Installing Docker;

There are 3 different methods of installation;

**1. Installing Docker engine with [Docker Desktop for Linux](https://docs.docker.com/desktop/install/linux-install/)**

**2. Setup and install using the [Docker `apt` repository](https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository)**

**3. Install and manage upgrades [manually](https://docs.docker.com/engine/install/ubuntu/#install-from-a-package)**

I will use the repository method.

### 2.1 Set up the repository
Update the `apt` package index and install packages to allow `apt` to use a repository over HTTPS:

```
hp@Cyndie:~$ sudo apt-get update
.....
Fetched 6,533 kB in 2s (3,756 kB/s)                                
Reading package lists... Done
hp@Cyndie:~$ sudo apt-get install \
>     ca-certificates \
>     curl \
>     gnupg \
>     lsb-release
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lsb-release is already the newest version (11.1.0ubuntu2).
ca-certificates is already the newest version (20211016ubuntu0.20.04.1).
curl is already the newest version (7.68.0-1ubuntu2.15).
gnupg is already the newest version (2.2.19-3ubuntu2.2).
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
hp@Cyndie:~$ 

```

Add Docker’s official GPG key:

```
hp@Cyndie:~$ sudo mkdir -m 0755 -p /etc/apt/keyrings
hp@Cyndie:~$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
hp@Cyndie:~$ 
```

Use the following command to set up the repository:

```
hp@Cyndie:~$ echo \
>   "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
>   $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
hp@Cyndie:~$ 

```
### 2.2 Install Docker engine

Update the `apt` package index;

```
hp@Cyndie:~$ sudo apt-get update
....
Fetched 82.2 kB in 1s (61.0 kB/s)
Reading package lists... Done
hp@Cyndie:~$ 

```

**N.B** If you receive a `GPG ERROR` when updating apt, try granting read permission for the Docker public key file before updating the package index:

```
sudo chmod a+r /etc/apt/keyrings/docker.gpg
sudo apt-get update
```

Install Docker Engine, containerd, and Docker Compose.

```
hp@Cyndie:~$ sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  docker-ce-rootless-extras docker-scan-plugin pigz slirp4netns
Suggested packages:
  aufs-tools cgroupfs-mount | cgroup-lite
The following NEW packages will be installed:
  containerd.io docker-buildx-plugin docker-ce docker-ce-cli docker-ce-rootless-extras docker-compose-plugin docker-scan-plugin pigz
  slirp4netns
.......
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for systemd (245.4-4ubuntu3.19) ...
hp@Cyndie:~$ 

```

Verify that the Docker Engine installation is successful by running the hello-world image:

```
hp@Cyndie:~$ sudo docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
2db29710123e: Pull complete 
Digest: sha256:aa0cc8055b82dc2509bed2e19b275c8f463506616377219d9642221ab53cf9fe
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

```

