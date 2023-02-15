# Linux post-installation steps for Docker Engine

## 1. Manage Docker as a non-root user

The Docker daemon binds to a Unix socket, not a TCP port. By default it’s the root user that owns the Unix socket, and other users can only access it using `sudo`. 

The Docker daemon always runs as the root user.

If you don’t want to preface the docker command with sudo, create a Unix group called `docker` and add users to it. 

When the Docker daemon starts, it creates a Unix socket accessible by members of the docker group. 

On some Linux distributions, the system automatically creates this group when installing Docker Engine using a package manager.

In that case, there is no need for you to manually create the group.

### 1.1 Create the `docker` group:

```
hp@Cyndie:~$ sudo groupadd docker
groupadd: group 'docker' already exists
hp@Cyndie:~$ 

```
Well the group already exists on my end. 

### 1.2 Add your user to the docker group.

```
hp@Cyndie:~$ sudo usermod -aG docker $USER
hp@Cyndie:~$ 
```
### 1.3 Log out and log back in so that your group membership is re-evaluated.

You can also run the following command to activate the changes to groups:

```
hp@Cyndie:~$ newgrp docker
hp@Cyndie:~$ 

```

### 1.4 Verify that you can run docker commands without `sudo`.

```
hp@Cyndie:~$ docker run hello-world

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

hp@Cyndie:~$ 

```

**N.B** If you initially ran Docker CLI commands using `sudo` before adding your user to the docker group, you may see the following error: 

```
WARNING: Error loading config file: /home/user/.docker/config.json -stat /home/user/.docker/config.json: permission denied
```

This error indicates that the permission settings for the `~/.docker/` directory are incorrect, due to having used the `sudo` command earlier.

To fix this problem, either remove the `~/.docker/` directory (it’s recreated automatically, but any custom settings are lost), or change its ownership and permissions using the following commands:

```
sudo chown "$USER":"$USER" /home/"$USER"/.docker -R
sudo chmod g+rwx "$HOME/.docker" -R
```

## 2. Configure Docker to start on Boot;

```
hp@Cyndie:~$ sudo systemctl enable docker.service
[sudo] password for hp: 
Synchronizing state of docker.service with SysV service script with /lib/systemd/systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install enable docker
hp@Cyndie:~$ sudo systemctl enable containerd.service
hp@Cyndie:~$ 
```

## 3. Configure default logging driver

Docker provides logging drivers for collecting and viewing log data from all containers running on a host.

The default logging driver, `json-file`, writes log data to JSON-formatted files on the host filesystem.

Over time, these log files expand in size, leading to potential exhaustion of disk resources.

I'll configure the `json-file` to turn on log rotation;

### 3.1 Set `json-file` as the logging driver;

set the `log-driver` and `log-opts` keys to appropriate values in the `daemon.json` file, located in `/etc/docker/` on Linux hosts.

Create the `daemon.json` file in `/etc/docker` if not already there;

```
hp@Cyndie:/etc/docker$ sudo nano daemon.json
hp@Cyndie:/etc/docker$ cat daemon.json 
{
  "log-driver": "json-file",
  "log-opts": {
    "max-size": "10m",
    "max-file": "3" 
  }
}
hp@Cyndie:/etc/docker$ 

```

This configuration sets the log driver to `json-file` and sets the `max-size` and `max-file` options to enable automatic log-rotation.

Restart Docker for the changes to take effect for newly created containers. 

Note that existing containers do not use the new logging configuration.

```
hp@Cyndie:/etc/docker$ sudo systemctl restart docker.service
hp@Cyndie:/etc/docker$ sudo systemctl restart containerd.service
hp@Cyndie:/etc/docker$ 

```








