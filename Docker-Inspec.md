```
hp@Cyndie:~$ curl https://omnitruck.chef.io/install.sh | sudo bash -s -- -P inspec
[sudo] password for hp:   % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 23526  100 23526    0     0  13871      0  0:00:01  0:00:01 --:--:-- 13863

Sorry, try again.
[sudo] password for hp: 
ubuntu 20.04 x86_64
Getting information for inspec stable  for ubuntu...
downloading https://omnitruck.chef.io/stable/inspec/metadata?v=&p=ubuntu&pv=20.04&m=x86_64
  to file /tmp/install.sh.15619/metadata.txt
trying wget...
trying curl...
sha1	e9bcd09078d35631c449ccd982a5fc0e2ecf712a
sha256	35ed1da6c885edd1618c19eb0305eaf2836cfae33b21ebd327d31512f15140d7
url	https://packages.chef.io/files/stable/inspec/5.21.29/ubuntu/20.04/inspec_5.21.29-1_amd64.deb
version	5.21.29
downloaded metadata file looks valid...
downloading https://packages.chef.io/files/stable/inspec/5.21.29/ubuntu/20.04/inspec_5.21.29-1_amd64.deb
  to file /tmp/install.sh.15619/inspec_5.21.29-1_amd64.deb
trying wget...
Comparing checksum with sha256sum...

WARNING WARNING WARNING WARNING WARNING WARNING WARNING WARNING WARNING

You are installing a package without a version pin.  If you are installing
on production servers via an automated process this is DANGEROUS and you will
be upgraded without warning on new releases, even to new major releases.
Letting the version float is only appropriate in test, development or
CI/CD environments.

WARNING WARNING WARNING WARNING WARNING WARNING WARNING WARNING WARNING

Installing inspec 
installing with dpkg...
Selecting previously unselected package inspec.
(Reading database ... 231200 files and directories currently installed.)
Preparing to unpack .../inspec_5.21.29-1_amd64.deb ...
You're about to install InSpec!
Unpacking inspec (5.21.29-1) ...
Setting up inspec (5.21.29-1) ...
Thank you for installing Chef InSpec!
hp@Cyndie:~$ ls
Desktop                Downloads         getting-started  package-lock.json            Public     Videos
docker-bench-security  examples.desktop  marketplace      packages-microsoft-prod.deb  snap       vmware
Documents              friend            Music            Pictures                     Templates
hp@Cyndie:~$ git clone https://github.com/dev-sec/cis-docker-benchmark
Cloning into 'cis-docker-benchmark'...
remote: Enumerating objects: 759, done.
remote: Counting objects: 100% (80/80), done.
remote: Compressing objects: 100% (52/52), done.
remote: Total 759 (delta 33), reused 52 (delta 22), pack-reused 679
Receiving objects: 100% (759/759), 257.06 KiB | 668.00 KiB/s, done.
Resolving deltas: 100% (431/431), done.
hp@Cyndie:~$ inspec exec cis-docker-benchmark
+---------------------------------------------+
            Chef License Acceptance

Before you can continue, 1 product license
must be accepted. View the license at
https://www.chef.io/end-user-license-agreement/

License that need accepting:
  * Chef InSpec

Do you accept the 1 product license (yes/no)?

> yes

Persisting 1 product license...
✔ 1 product license persisted.

+---------------------------------------------+

Profile:   CIS Docker Benchmark Profile (cis-docker-benchmark)
Version:   2.1.4
Target:    local://
Target ID: d4a83621-47e7-524a-8ac3-de3c6f4e3b38

  ×  docker-4.2: Use trusted base images for containers
     ×  Environment variable DOCKER_CONTENT_TRUST content is expected to eq "1"
     
     expected: "1"
          got: nil
     
     (compared using ==)

  ↺  docker-4.3: Do not install unnecessary packages in the container
     ↺  Do not install unnecessary packages in the container
  ↺  docker-4.4: Rebuild the images to include security patches
     ↺  Rebuild the images to include security patches
  ×  docker-4.5: Enable Content trust for Docker
     ×  Environment variable DOCKER_CONTENT_TRUST content is expected to eq "1"
     
     expected: "1"
          got: nil
     
     (compared using ==)

  ×  docker-4.7: Do not use update instructions alone in the Dockerfile (3 failed)
     ✔  Command: `docker history --no-trunc sha256:1fca6beaeb5f7ff7bd127ba0547ddf26b3dbdadb6a40aefd952a4ef4c998ea4b| grep -e 'update'` stdout is expected to eq ""
     ✔  Command: `docker history --no-trunc sha256:afac2f17b95aa35b623844a573c88ec43e6f729502939f34fce8f482499839a7| grep -e 'update'` stdout is expected to eq ""
     ✔  Command: `docker history --no-trunc sha256:07e98eb1d549a7680167469834f5c50e12e4c8606866ec820bbf146e25986a31| grep -e 'update'` stdout is expected to eq ""
     ✔  Command: `docker history --no-trunc sha256:7c0d59f05c0ab607d929d040d94dcc75aaa559c04afc1f50e199619829a1c037| grep -e 'update'` stdout is expected to eq ""
     ✔  Command: `docker history --no-trunc sha256:35f80c11b86022d1cbfddd0c13fda1396af872406ca65f0a957f01eed992b1c1| grep -e 'update'` stdout is expected to eq ""
     ✔  Command: `docker history --no-trunc sha256:1ad1b791c4d12224a8e243ec3da3d566ea83cd4f136574242a1e80720a4e350c| grep -e 'update'` stdout is expected to eq ""
     ✔  Command: `docker history --no-trunc sha256:c8df46a73604bfbfa0dd1dd4d1c777090867a716b82cd4187954e7d96cc407fa| grep -e 'update'` stdout is expected to eq ""
     ✔  Command: `docker history --no-trunc sha256:5ce65d7b0fde20d6c6472e817df61f9b2d8ccd349d6d4d70d2f6305a99c73448| grep -e 'update'` stdout is expected to eq ""
     ✔  Command: `docker history --no-trunc sha256:58db3edaf2be6e80f628796355b1bdeaf8bea1692b402f48b7e7b8d1ff100b02| grep -e 'update'` stdout is expected to eq ""
     ×  Command: `docker history --no-trunc sha256:1f83439a7b133710bdc39ddc6b108d75293adc96e316fdbc646c5a7d9186f07e| grep -e 'update'` stdout is expected to eq ""
     
     expected: ""
          got: "<missing>                                                                 3 months ago   RUN /bin/sh...d --no-cache curl # buildkit                                     4.6MB     buildkit.dockerfile.v0\n"
     
     (compared using ==)
     
     Diff:
     @@ -1 +1,2 @@
     +<missing>                                                                 3 months ago   RUN /bin/sh -c apk update && apk add --no-cache curl # buildkit                                     4.6MB     buildkit.dockerfile.v0

     ×  Command: `docker history --no-trunc sha256:43b6816e76c68d5359304334406738b7de10e807834239e5a570390f6c4d92b3| grep -e 'update'` stdout is expected to eq ""
     
     expected: ""
          got: "<missing>                                                                 3 months ago   RUN /bin/sh...                                                                 4.51MB    buildkit.dockerfile.v0\n"
     
     (compared using ==)
     
     Diff:
     @@ -1 +1,2 @@
     +<missing>                                                                 3 months ago   RUN /bin/sh -c apk update && apk add --no-cache postgresql-libs curl # buildkit                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          4.51MB    buildkit.dockerfile.v0

     ✔  Command: `docker history --no-trunc sha256:feb5d9fea6a5e9606aa995e879d862b825965ba48de054caab5ef356dc6b3412| grep -e 'update'` stdout is expected to eq ""
     ×  Command: `docker history --no-trunc sha256:2d4710ed0553536b8eb13d5c72cbc273a792ec1e5c432dc212379722ad29bf72| grep -e 'update'` stdout is expected to eq ""
     
     expected: ""
          got: "<missing>                                                                 3 years ago   /bin/sh -c s...                                                                                       839MB     \n"
     
     (compared using ==)
     
     Diff:
     @@ -1 +1,2 @@
     +<missing>                                                                 3 years ago   /bin/sh -c set -x     && apt-get -y update     && apt-get install -y --no-install-recommends --no-install-suggests         libcurl4-openssl-dev         libssl-dev         jq         ruby-full         libcurl4-openssl-dev         libxml2         libxml2-dev         libxslt1-dev         ruby-dev         build-essential         libgmp-dev         zlib1g-dev         libssl-dev         libffi-dev         python-dev         python-setuptools         libldns-dev         python3-pip         python-pip         python-dnspython         git         rename         nmap         wget         curl         chromium-browser         locales         dnsutils     && apt-get clean autoclean  && apt-get autoremove -y  && rm -rf /var/lib/{apt,dpkg,cache,log}/     && ulimit -n 2048     && localedef -i en_US -c -f UTF-8 -A /usr/share/locale/locale.alias en_US.UTF-8                                                                                                                                                                                                                                                                                       839MB     

  ↺  docker-4.8: Remove setuid and setgid permissions in the images
     ↺  Use DevSec Linux Baseline in Container
  ×  docker-4.9: Use COPY instead of ADD in Dockerfile (12 failed)
     ×  Command: `docker history --no-trunc sha256:1fca6beaeb5f7ff7bd127ba0547ddf26b3dbdadb6a40aefd952a4ef4c998ea4b| grep 'ADD'` stdout is expected to eq ""
     
     expected: ""
          got: "<missing>                                                                 3 weeks ago         /bin/s...                                                                                       5.59MB    \n"
     
     (compared using ==)
     
     Diff:
     @@ -1 +1,2 @@
     +<missing>                                                                 3 weeks ago         /bin/sh -c #(nop) ADD file:cdac18271416ac5bf6876b7ea9af1129108d03f9813589dfda113e5f09d6b80b in /                                                                                                 5.59MB    

     ×  Command: `docker history --no-trunc sha256:afac2f17b95aa35b623844a573c88ec43e6f729502939f34fce8f482499839a7| grep 'ADD'` stdout is expected to eq ""
     
     expected: ""
          got: "<missing>                                                                 3 weeks ago         /bin/s...                                                                                       5.59MB    \n"
     
     (compared using ==)
     
     Diff:
     @@ -1 +1,2 @@
     +<missing>                                                                 3 weeks ago         /bin/sh -c #(nop) ADD file:cdac18271416ac5bf6876b7ea9af1129108d03f9813589dfda113e5f09d6b80b in /                                                                                                 5.59MB    

     ×  Command: `docker history --no-trunc sha256:07e98eb1d549a7680167469834f5c50e12e4c8606866ec820bbf146e25986a31| grep 'ADD'` stdout is expected to eq ""
     
     expected: ""
          got: "<missing>                                                                 3 weeks ago         /bin/s...                                                                                       5.59MB    \n"
     
     (compared using ==)
     
     Diff:
     @@ -1 +1,2 @@
     +<missing>                                                                 3 weeks ago         /bin/sh -c #(nop) ADD file:cdac18271416ac5bf6876b7ea9af1129108d03f9813589dfda113e5f09d6b80b in /                                                                                                 5.59MB    

     ×  Command: `docker history --no-trunc sha256:7c0d59f05c0ab607d929d040d94dcc75aaa559c04afc1f50e199619829a1c037| grep 'ADD'` stdout is expected to eq ""
     
     expected: ""
          got: "<missing>                                                                 3 weeks ago         /bin/s...                                                                                       5.59MB    \n"
     
     (compared using ==)
     
     Diff:
     @@ -1 +1,2 @@
     +<missing>                                                                 3 weeks ago         /bin/sh -c #(nop) ADD file:cdac18271416ac5bf6876b7ea9af1129108d03f9813589dfda113e5f09d6b80b in /                                                                                                 5.59MB    

     ×  Command: `docker history --no-trunc sha256:35f80c11b86022d1cbfddd0c13fda1396af872406ca65f0a957f01eed992b1c1| grep 'ADD'` stdout is expected to eq ""
     
     expected: ""
          got: "<missing>                                                                 3 weeks ago         /bin/s...                                                                                       5.59MB    \n"
     
     (compared using ==)
     
     Diff:
     @@ -1 +1,2 @@
     +<missing>                                                                 3 weeks ago         /bin/sh -c #(nop) ADD file:cdac18271416ac5bf6876b7ea9af1129108d03f9813589dfda113e5f09d6b80b in /                                                                                                 5.59MB    

     ×  Command: `docker history --no-trunc sha256:1ad1b791c4d12224a8e243ec3da3d566ea83cd4f136574242a1e80720a4e350c| grep 'ADD'` stdout is expected to eq ""
     
     expected: ""
          got: "<missing>                                                                 3 weeks ago         /bin/s...                                                                                       5.59MB    \n"
     
     (compared using ==)
     
     Diff:
     @@ -1 +1,2 @@
     +<missing>                                                                 3 weeks ago         /bin/sh -c #(nop) ADD file:cdac18271416ac5bf6876b7ea9af1129108d03f9813589dfda113e5f09d6b80b in /                                                                                                 5.59MB    

     ×  Command: `docker history --no-trunc sha256:c8df46a73604bfbfa0dd1dd4d1c777090867a716b82cd4187954e7d96cc407fa| grep 'ADD'` stdout is expected to eq ""
     
     expected: ""
          got: "<missing>                                                                 3 weeks ago         /bin/s...                                                                                       5.59MB    \n"
     
     (compared using ==)
     
     Diff:
     @@ -1 +1,2 @@
     +<missing>                                                                 3 weeks ago         /bin/sh -c #(nop) ADD file:cdac18271416ac5bf6876b7ea9af1129108d03f9813589dfda113e5f09d6b80b in /                                                                                                 5.59MB    

     ×  Command: `docker history --no-trunc sha256:5ce65d7b0fde20d6c6472e817df61f9b2d8ccd349d6d4d70d2f6305a99c73448| grep 'ADD'` stdout is expected to eq ""
     
     expected: ""
          got: "<missing>                                                                 3 weeks ago   /bin/sh -c #...nop) ADD file:cdac18271416ac5bf6876b7ea9af1129108d03f9813589dfda113e5f09d6b80b in /    5.59MB    \n"
     
     (compared using ==)
     
     Diff:
     @@ -1 +1,2 @@
     +<missing>                                                                 3 weeks ago   /bin/sh -c #(nop) ADD file:cdac18271416ac5bf6876b7ea9af1129108d03f9813589dfda113e5f09d6b80b in /    5.59MB    

     ×  Command: `docker history --no-trunc sha256:58db3edaf2be6e80f628796355b1bdeaf8bea1692b402f48b7e7b8d1ff100b02| grep 'ADD'` stdout is expected to eq ""
     
     expected: ""
          got: "<missing>                                                                 5 weeks ago   /bin/sh -c #...nop) ADD file:18e71f049606f6339ce7a995839623f50e6ec6474bfd0a3a7ca799db726f47f6 in /    77.8MB    \n"
     
     (compared using ==)
     
     Diff:
     @@ -1 +1,2 @@
     +<missing>                                                                 5 weeks ago   /bin/sh -c #(nop) ADD file:18e71f049606f6339ce7a995839623f50e6ec6474bfd0a3a7ca799db726f47f6 in /    77.8MB    

     ×  Command: `docker history --no-trunc sha256:1f83439a7b133710bdc39ddc6b108d75293adc96e316fdbc646c5a7d9186f07e| grep 'ADD'` stdout is expected to eq ""
     
     expected: ""
          got: "<missing>                                                                 3 months ago   /bin/sh -c ...nop) ADD file:ceeb6e8632fafc657116cbf3afbd522185a16963230b57881073dad22eb0e1a3 in /    5.54MB    \n"
     
     (compared using ==)
     
     Diff:
     @@ -1 +1,2 @@
     +<missing>                                                                 3 months ago   /bin/sh -c #(nop) ADD file:ceeb6e8632fafc657116cbf3afbd522185a16963230b57881073dad22eb0e1a3 in /    5.54MB    

     ×  Command: `docker history --no-trunc sha256:43b6816e76c68d5359304334406738b7de10e807834239e5a570390f6c4d92b3| grep 'ADD'` stdout is expected to eq ""
     
     expected: ""
          got: "<missing>                                                                 6 months ago   /bin/sh -c ...                                                                                       5.59MB    \n"
     
     (compared using ==)
     
     Diff:
     @@ -1 +1,2 @@
     +<missing>                                                                 6 months ago   /bin/sh -c #(nop) ADD file:f77e3f51f020890d22997e6c2ca98968b75b8bc8c463341a2010ff0655d4c88f in /                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         5.59MB    

     ✔  Command: `docker history --no-trunc sha256:feb5d9fea6a5e9606aa995e879d862b825965ba48de054caab5ef356dc6b3412| grep 'ADD'` stdout is expected to eq ""
     ×  Command: `docker history --no-trunc sha256:2d4710ed0553536b8eb13d5c72cbc273a792ec1e5c432dc212379722ad29bf72| grep 'ADD'` stdout is expected to eq ""
     
     expected: ""
          got: "<missing>                                                                 3 years ago   /bin/sh -c #...                                                                                       63.2MB    \n"
     
     (compared using ==)
     
     Diff:
     @@ -1 +1,2 @@
     +<missing>                                                                 3 years ago   /bin/sh -c #(nop) ADD file:a48a5dc1b9dbfc632f6cf86fe27b770b63f07a115c98c4465dc184e303a4efa1 in /                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           63.2MB    

  ↺  docker-4.10: Do not store secrets in Dockerfiles
     ↺  Manually verify that you have not used secrets in images
  ↺  docker-4.11: Install verified packages only
     ↺  Manually verify that you installed verified packages
  ↺  docker-5.2: Verify SELinux security options, if applicable
     ↺  Skipped control due to only_if condition.
  ✔  docker-5.22: Do not docker exec commands with privileged option
     ✔  is expected to be empty
  ✔  docker-5.23: Do not docker exec commands with user option
     ✔  is expected to be empty
  ↺  docker-5.27: Ensure docker commands always get the latest version of the image
     ↺  Ensure docker commands always get the latest version of the image
  ↺  docker-5.29: Do not use Docker's default bridge docker0
     ↺  Not implemented yet
  ×  docker-2.1: Restrict network traffic between containers
     ×  JSON /etc/docker/daemon.json ["icc"] is expected to eq false
     
     expected: false
          got: nil
     
     (compared using ==)

  ×  docker-2.2: Set the logging level
     ×  JSON /etc/docker/daemon.json ["log-level"] is expected to eq "info"
     
     expected: "info"
          got: nil
     
     (compared using ==)

  ×  docker-2.3: Allow Docker to make changes to iptables
     ×  JSON /etc/docker/daemon.json ["iptables"] is expected to eq true
     
     expected: true
          got: nil
     
     (compared using ==)

  ×  docker-2.4: Do not use insecure registries
     ×  JSON /etc/docker/daemon.json ["insecure-registries"] is expected to be empty
     expected nil to respond to `empty?`
  ✔  docker-2.5: Do not use the aufs storage driver
     ✔  JSON /etc/docker/daemon.json ["storage-driver"] is expected not to eq "aufs"
  ×  docker-2.6: Configure TLS authentication for Docker daemon (5 failed)
     ×  JSON /etc/docker/daemon.json ["tls"] is expected to eq true
     
     expected: true
          got: nil
     
     (compared using ==)

     ×  JSON /etc/docker/daemon.json ["tlsverify"] is expected to eq true
     
     expected: true
          got: nil
     
     (compared using ==)

     ×  JSON /etc/docker/daemon.json ["tlscacert"] is expected to eq "/etc/docker/ssl/ca.pem"
     
     expected: "/etc/docker/ssl/ca.pem"
          got: nil
     
     (compared using ==)

     ×  JSON /etc/docker/daemon.json ["tlscert"] is expected to eq "/etc/docker/ssl/server_cert.pem"
     
     expected: "/etc/docker/ssl/server_cert.pem"
          got: nil
     
     (compared using ==)

     ×  JSON /etc/docker/daemon.json ["tlskey"] is expected to eq "/etc/docker/ssl/server_key.pem"
     
     expected: "/etc/docker/ssl/server_key.pem"
          got: nil
     
     (compared using ==)

  ×  docker-2.7: Set default ulimit as appropriate (2 failed)
     ×  JSON /etc/docker/daemon.json ["default-ulimits", "nproc"] is expected to eq "1024:2408"
     
     expected: "1024:2408"
          got: nil
     
     (compared using ==)

     ×  JSON /etc/docker/daemon.json ["default-ulimits", "nofile"] is expected to eq {:"100"=>"200"}
     
     expected: {:"100"=>"200"}
          got: nil
     
     (compared using ==)

  ×  docker-2.8: Enable user namespace support (1 failed)
     ×  JSON /etc/docker/daemon.json ["userns-remap"] is expected to eq "default"
     
     expected: "default"
          got: nil
     
     (compared using ==)

     ✔  File /etc/subuid is expected to exist
     ✔  File /etc/subuid is expected to be file
     ✔  File /etc/subgid is expected to exist
     ✔  File /etc/subgid is expected to be file
  ×  docker-2.9: Confirm default cgroup usage
     ×  JSON /etc/docker/daemon.json ["cgroup-parent"] is expected to eq "docker"
     
     expected: "docker"
          got: nil
     
     (compared using ==)

  ×  docker-2.10: Do not change base device size until needed
     ×  JSON /etc/docker/daemon.json ["storage-opts"] is expected to eq ["dm.basesize=10G"]
     
     expected: ["dm.basesize=10G"]
          got: nil
     
     (compared using ==)

  ×  docker-2.11: Use authorization plugin (2 failed)
     ×  JSON /etc/docker/daemon.json ["authorization-plugins"] is expected not to be empty
     expected nil to respond to `empty?`
     ×  JSON /etc/docker/daemon.json ["authorization-plugins"] is expected to eq ["authz-broker"]
     
     expected: ["authz-broker"]
          got: nil
     
     (compared using ==)

  ×  docker-2.12: Configure centralized and remote logging (2 failed)
     ✔  JSON /etc/docker/daemon.json ["log-driver"] is expected not to be empty
     ×  JSON /etc/docker/daemon.json ["log-driver"] is expected to eq "syslog"
     
     expected: "syslog"
          got: "json-file"
     
     (compared using ==)

     ×  JSON /etc/docker/daemon.json ["log-opts"] is expected to include "syslog-address"
     expected {"max-file" => "3", "max-size" => "10m"} to include "syslog-address"
     Diff:
     @@ -1,2 +1,3 @@
     -["syslog-address"]
     +"max-file" => "3",
     +"max-size" => "10m",

  ×  docker-2.13: Disable operations on legacy registry (v1)
     ×  JSON /etc/docker/daemon.json ["disable-legacy-registry"] is expected to eq true
     
     expected: true
          got: nil
     
     (compared using ==)

  ×  docker-2.14: Enable live restore
     ×  JSON /etc/docker/daemon.json ["live-restore"] is expected to eq true
     
     expected: true
          got: nil
     
     (compared using ==)

  ✔  docker-2.15: Do not enable swarm mode, if not needed
     ✔  #<Hashie::Mash Architecture="x86_64" BridgeNfIp6tables=true BridgeNfIptables=true CPUSet=true CPUShares=true CgroupDriver="cgroupfs" CgroupVersion="1" ClientInfo=#<Hashie::Mash Context="default" Debug=false Plugins=#<Hashie::Array [#<Hashie::Mash Name="buildx" Path="/usr/libexec/docker/cli-plugins/docker-buildx" SchemaVersion="0.1.0" ShortDescription="Docker Buildx" Vendor="Docker Inc." Version="v0.10.2">, #<Hashie::Mash Name="compose" Path="/usr/libexec/docker/cli-plugins/docker-compose" SchemaVersion="0.1.0" ShortDescription="Docker Compose" Vendor="Docker Inc." Version="v2.16.0">, #<Hashie::Mash Name="scan" Path="/usr/libexec/docker/cli-plugins/docker-scan" SchemaVersion="0.1.0" ShortDescription="Docker Scan" Vendor="Docker Inc." Version="v0.23.0">]> Warnings=nil> ContainerdCommit=#<Hashie::Mash Expected="2456e983eb9e37e47538f59ea18f2043c9a73640" ID="2456e983eb9e37e47538f59ea18f2043c9a73640"> Containers=0 ContainersPaused=0 ContainersRunning=0 ContainersStopped=0 CpuCfsPeriod=true CpuCfsQuota=true Debug=false DefaultRuntime="runc" DockerRootDir="/var/lib/docker" Driver="overlay2" DriverStatus=#<Hashie::Array [#<Hashie::Array ["Backing Filesystem", "extfs"]>, #<Hashie::Array ["Supports d_type", "true"]>, #<Hashie::Array ["Using metacopy", "false"]>, #<Hashie::Array ["Native Overlay Diff", "true"]>, #<Hashie::Array ["userxattr", "false"]>]> ExperimentalBuild=false GenericResources=nil HttpProxy="" HttpsProxy="" ID="fb06fcfa-6c67-4fd3-bcfe-11bc2af50e79" IPv4Forwarding=true Images=13 IndexServerAddress="https://index.docker.io/v1/" InitBinary="docker-init" InitCommit=#<Hashie::Mash Expected="de40ad0" ID="de40ad0"> Isolation="" KernelMemoryTCP=true KernelVersion="5.4.0-139-generic" Labels=#<Hashie::Array []> LiveRestoreEnabled=false LoggingDriver="json-file" MemTotal=8212205568 MemoryLimit=true NCPU=4 NEventsListener=0 NFd=24 NGoroutines=35 Name="Cyndie" NoProxy="" OSType="linux" OSVersion="20.04" OomKillDisable=true OperatingSystem="Ubuntu 20.04.5 LTS" PidsLimit=true Plugins=#<Hashie::Mash Authorization=nil Log=#<Hashie::Array ["awslogs", "fluentd", "gcplogs", "gelf", "journald", "json-file", "local", "logentries", "splunk", "syslog"]> Network=#<Hashie::Array ["bridge", "host", "ipvlan", "macvlan", "null", "overlay"]> Volume=#<Hashie::Array ["local"]>> RegistryConfig=#<Hashie::Mash AllowNondistributableArtifactsCIDRs=nil AllowNondistributableArtifactsHostnames=nil IndexConfigs=#<Hashie::Mash docker.io=#<Hashie::Mash Mirrors=#<Hashie::Array []> Name="docker.io" Official=true Secure=true>> InsecureRegistryCIDRs=#<Hashie::Array ["127.0.0.0/8"]> Mirrors=nil> RuncCommit=#<Hashie::Mash Expected="v1.1.4-0-g5fd4c4d" ID="v1.1.4-0-g5fd4c4d"> Runtimes=#<Hashie::Mash io.containerd.runc.v2=#<Hashie::Mash path="runc"> runc=#<Hashie::Mash path="runc">> SecurityOptions=#<Hashie::Array ["name=apparmor", "name=seccomp,profile=builtin"]> ServerVersion="23.0.1" SwapLimit=false Swarm=#<Hashie::Mash ControlAvailable=false Error="" LocalNodeState="inactive" NodeAddr="" NodeID="" RemoteManagers=nil> SystemTime="2023-03-04T14:10:48.165209987+03:00" Warnings=#<Hashie::Array ["WARNING: No swap limit support"]>> Swarm.LocalNodeState is expected to eq "inactive"
  ↺  docker-2.16: Control the number of manager nodes in a swarm
     ↺  Skipped control due to only_if condition.
  ↺  docker-2.17: Bind swarm services to a specific host interface
     ↺  Skipped control due to only_if condition.
  ×  docker-2.18: Disable Userland Proxy (2 failed)
     ×  JSON /etc/docker/daemon.json ["userland-proxy"] is expected to eq false
     
     expected: false
          got: nil
     
     (compared using ==)

     ×  ["/usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock"] is expected to include "userland-proxy=false"
     expected ["/usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock"] to include "userland-proxy=false"
  ↺  docker-2.19: Encrypt data exchanged between containers on different nodes on the overlay network
     ↺  Skipped control due to only_if condition.
  ×  docker-2.20: Apply a daemon-wide custom seccomp profile, if needed (2 failed)
     ×  JSON /etc/docker/daemon.json ["seccomp-profile"] is expected not to eq nil
     
     expected: value != nil
          got: nil
     
     (compared using ==)

     ×  JSON /etc/docker/daemon.json ["seccomp-profile"] is expected to eq "default"
     
     expected: "default"
          got: nil
     
     (compared using ==)

  ✔  docker-2.21: Avoid experimental features in production
     ✔  false is expected to eq "false"
  ↺  docker-2.22: Use Docker's secret management commands for managing secrets in a Swarm cluster
     ↺  Skipped control due to only_if condition.
  ↺  docker-2.23: Run swarm manager in auto-lock mode
     ↺  Skipped control due to only_if condition.
  ✔  docker-3.1: Verify that docker.service file ownership is set to root:root
     ✔  File /lib/systemd/system/docker.service is expected to exist
     ✔  File /lib/systemd/system/docker.service is expected to be file
     ✔  File /lib/systemd/system/docker.service is expected to be owned by "root"
     ✔  File /lib/systemd/system/docker.service is expected to be grouped into "root"
  ✔  docker-3.2: Verify that docker.service file permissions are set to 644 or more restrictive
     ✔  File /lib/systemd/system/docker.service is expected to exist
     ✔  File /lib/systemd/system/docker.service is expected to be file
     ✔  File /lib/systemd/system/docker.service is expected to be readable by owner
     ✔  File /lib/systemd/system/docker.service is expected to be writable by owner
     ✔  File /lib/systemd/system/docker.service is expected to be readable by group
     ✔  File /lib/systemd/system/docker.service is expected not to be writable by group
     ✔  File /lib/systemd/system/docker.service is expected to be readable by other
     ✔  File /lib/systemd/system/docker.service is expected not to be writable by other
     ✔  File /lib/systemd/system/docker.service is expected not to be executable
  ✔  docker-3.3: Verify that docker.socket file ownership is set to root:root
     ✔  File /lib/systemd/system/docker.socket is expected to exist
     ✔  File /lib/systemd/system/docker.socket is expected to be file
     ✔  File /lib/systemd/system/docker.socket is expected to be owned by "root"
     ✔  File /lib/systemd/system/docker.socket is expected to be grouped into "root"
  ✔  docker-3.4: Verify that docker.socket file permissions are set to 644 or more restrictive
     ✔  File /lib/systemd/system/docker.socket is expected to exist
     ✔  File /lib/systemd/system/docker.socket is expected to be file
     ✔  File /lib/systemd/system/docker.socket is expected to be readable by owner
     ✔  File /lib/systemd/system/docker.socket is expected to be writable by owner
     ✔  File /lib/systemd/system/docker.socket is expected to be readable by group
     ✔  File /lib/systemd/system/docker.socket is expected not to be writable by group
     ✔  File /lib/systemd/system/docker.socket is expected to be readable by other
     ✔  File /lib/systemd/system/docker.socket is expected not to be writable by other
     ✔  File /lib/systemd/system/docker.socket is expected not to be executable
  ✔  docker-3.5: Verify that /etc/docker directory ownership is set to root:root
     ✔  File /etc/docker is expected to exist
     ✔  File /etc/docker is expected to be directory
     ✔  File /etc/docker is expected to be owned by "root"
     ✔  File /etc/docker is expected to be grouped into "root"
  ✔  docker-3.6: Verify that /etc/docker directory permissions are set to 755 or more restrictive
     ✔  File /etc/docker is expected to exist
     ✔  File /etc/docker is expected to be directory
     ✔  File /etc/docker is expected to be readable by owner
     ✔  File /etc/docker is expected to be writable by owner
     ✔  File /etc/docker is expected to be executable by owner
     ✔  File /etc/docker is expected to be readable by group
     ✔  File /etc/docker is expected not to be writable by group
     ✔  File /etc/docker is expected to be executable by group
     ✔  File /etc/docker is expected to be readable by other
     ✔  File /etc/docker is expected not to be writable by other
     ✔  File /etc/docker is expected to be executable by other
  ×  docker-3.7: Verify that registry certificate file ownership is set to root:root (12 failed)
     ×  File /etc/docker/certs.d is expected to exist
     expected File /etc/docker/certs.d to exist
     ×  File /etc/docker/certs.d is expected to be directory
     expected `File /etc/docker/certs.d.directory?` to be truthy, got false
     ×  File /etc/docker/certs.d is expected to be owned by "root"
     expected `File /etc/docker/certs.d.owned_by?("root")` to be truthy, got false
     ×  File /etc/docker/certs.d is expected to be grouped into "root"
     expected `File /etc/docker/certs.d.grouped_into?("root")` to be truthy, got false
     ×  File /etc/docker/certs.d/registry_hostname:port is expected to exist
     expected File /etc/docker/certs.d/registry_hostname:port to exist
     ×  File /etc/docker/certs.d/registry_hostname:port is expected to be directory
     expected `File /etc/docker/certs.d/registry_hostname:port.directory?` to be truthy, got false
     ×  File /etc/docker/certs.d/registry_hostname:port is expected to be owned by "root"
     expected `File /etc/docker/certs.d/registry_hostname:port.owned_by?("root")` to be truthy, got false
     ×  File /etc/docker/certs.d/registry_hostname:port is expected to be grouped into "root"
     expected `File /etc/docker/certs.d/registry_hostname:port.grouped_into?("root")` to be truthy, got false
     ×  File /etc/docker/certs.d/registry_hostname:port/ca.crt is expected to exist
     expected File /etc/docker/certs.d/registry_hostname:port/ca.crt to exist
     ×  File /etc/docker/certs.d/registry_hostname:port/ca.crt is expected to be file
     expected `File /etc/docker/certs.d/registry_hostname:port/ca.crt.file?` to be truthy, got false
     ×  File /etc/docker/certs.d/registry_hostname:port/ca.crt is expected to be owned by "root"
     expected `File /etc/docker/certs.d/registry_hostname:port/ca.crt.owned_by?("root")` to be truthy, got false
     ×  File /etc/docker/certs.d/registry_hostname:port/ca.crt is expected to be grouped into "root"
     expected `File /etc/docker/certs.d/registry_hostname:port/ca.crt.grouped_into?("root")` to be truthy, got false
  ×  docker-3.8: Verify that registry certificate file permissions are set to 444 or more restrictive (3 failed)
     ×  File /etc/docker/certs.d/registry_hostname:port/ca.crt is expected to exist
     expected File /etc/docker/certs.d/registry_hostname:port/ca.crt to exist
     ×  File /etc/docker/certs.d/registry_hostname:port/ca.crt is expected to be file
     expected `File /etc/docker/certs.d/registry_hostname:port/ca.crt.file?` to be truthy, got false
     ×  File /etc/docker/certs.d/registry_hostname:port/ca.crt is expected to be readable
     expected File /etc/docker/certs.d/registry_hostname:port/ca.crt to be readable
     ✔  File /etc/docker/certs.d/registry_hostname:port/ca.crt is expected not to be executable
     ✔  File /etc/docker/certs.d/registry_hostname:port/ca.crt is expected not to be writable
  ×  docker-3.9: Verify that TLS CA certificate file ownership is set to root:root (4 failed)
     ×  File  is expected to exist
     expected File  to exist
     ×  File  is expected to be file
     expected `File .file?` to be truthy, got false
     ×  File  is expected to be owned by "root"
     expected `File .owned_by?("root")` to be truthy, got false
     ×  File  is expected to be grouped into "root"
     expected `File .grouped_into?("root")` to be truthy, got false
  ×  docker-3.10: Verify that TLS CA certificate file permissions are set to 444 or more restrictive (3 failed)
     ×  File  is expected to exist
     expected File  to exist
     ×  File  is expected to be file
     expected `File .file?` to be truthy, got false
     ×  File  is expected to be readable
     expected File  to be readable
     ✔  File  is expected not to be executable
     ✔  File  is expected not to be writable
  ×  docker-3.11: Verify that Docker server certificate file ownership is set to root:root (4 failed)
     ×  File  is expected to exist
     expected File  to exist
     ×  File  is expected to be file
     expected `File .file?` to be truthy, got false
     ×  File  is expected to be owned by "root"
     expected `File .owned_by?("root")` to be truthy, got false
     ×  File  is expected to be grouped into "root"
     expected `File .grouped_into?("root")` to be truthy, got false
  ×  docker-3.12: Verify that Docker server certificate file permissions are set to 444 or more restrictive (3 failed)
     ×  File  is expected to exist
     expected File  to exist
     ×  File  is expected to be file
     expected `File .file?` to be truthy, got false
     ×  File  is expected to be readable
     expected File  to be readable
     ✔  File  is expected not to be executable
     ✔  File  is expected not to be writable
  ×  docker-3.13: Verify that Docker server certificate key file ownership is set to root:root (4 failed)
     ×  File  is expected to exist
     expected File  to exist
     ×  File  is expected to be file
     expected `File .file?` to be truthy, got false
     ×  File  is expected to be owned by "root"
     expected `File .owned_by?("root")` to be truthy, got false
     ×  File  is expected to be grouped into "root"
     expected `File .grouped_into?("root")` to be truthy, got false
  ×  docker-3.14: Verify that Docker server certificate key file permissions are set to 444 or more restrictive (3 failed)
     ×  File  is expected to exist
     expected File  to exist
     ×  File  is expected to be file
     expected `File .file?` to be truthy, got false
     ×  File  is expected to be readable
     expected File  to be readable
     ✔  File  is expected not to be executable
     ✔  File  is expected not to be writable
  ✔  docker-3.15: Verify that Docker socket file ownership is set to root:docker
     ✔  File /var/run/docker.sock is expected to exist
     ✔  File /var/run/docker.sock is expected to be socket
     ✔  File /var/run/docker.sock is expected to be owned by "root"
     ✔  File /var/run/docker.sock is expected to be grouped into "docker"
  ✔  docker-3.16: Verify that Docker socket file permissions are set to 660 or more restrictive
     ✔  File /var/run/docker.sock is expected to exist
     ✔  File /var/run/docker.sock is expected to be socket
     ✔  File /var/run/docker.sock is expected to be readable by owner
     ✔  File /var/run/docker.sock is expected to be writable by owner
     ✔  File /var/run/docker.sock is expected not to be executable by owner
     ✔  File /var/run/docker.sock is expected to be readable by group
     ✔  File /var/run/docker.sock is expected to be writable by group
     ✔  File /var/run/docker.sock is expected not to be executable by group
     ✔  File /var/run/docker.sock is expected not to be readable by other
     ✔  File /var/run/docker.sock is expected not to be writable by other
     ✔  File /var/run/docker.sock is expected not to be executable by other
  ✔  docker-3.17: Verify that daemon.json file ownership is set to root:root
     ✔  File /etc/docker/daemon.json is expected to exist
     ✔  File /etc/docker/daemon.json is expected to be file
     ✔  File /etc/docker/daemon.json is expected to be owned by "root"
     ✔  File /etc/docker/daemon.json is expected to be grouped into "root"
  ✔  docker-3.18: Verify that /etc/docker/daemon.json file permissions are set to 644 or more restrictive
     ✔  File /etc/docker/daemon.json is expected to exist
     ✔  File /etc/docker/daemon.json is expected to be file
     ✔  File /etc/docker/daemon.json is expected to be readable by owner
     ✔  File /etc/docker/daemon.json is expected to be writable by owner
     ✔  File /etc/docker/daemon.json is expected not to be executable by owner
     ✔  File /etc/docker/daemon.json is expected to be readable by group
     ✔  File /etc/docker/daemon.json is expected not to be writable by group
     ✔  File /etc/docker/daemon.json is expected not to be executable by group
     ✔  File /etc/docker/daemon.json is expected to be readable by other
     ✔  File /etc/docker/daemon.json is expected not to be writable by other
     ✔  File /etc/docker/daemon.json is expected not to be executable by other
  ✔  docker-3.19: Verify that /etc/default/docker file ownership is set to root:root
     ✔  File /etc/default/docker is expected to exist
     ✔  File /etc/default/docker is expected to be file
     ✔  File /etc/default/docker is expected to be owned by "root"
     ✔  File /etc/default/docker is expected to be grouped into "root"
  ✔  docker-3.20: Verify that /etc/default/docker file permissions are set to 644 or more restrictive
     ✔  File /etc/default/docker is expected to exist
     ✔  File /etc/default/docker is expected to be file
     ✔  File /etc/default/docker is expected to be readable by owner
     ✔  File /etc/default/docker is expected to be writable by owner
     ✔  File /etc/default/docker is expected not to be executable by owner
     ✔  File /etc/default/docker is expected to be readable by group
     ✔  File /etc/default/docker is expected not to be writable by group
     ✔  File /etc/default/docker is expected not to be executable by group
     ✔  File /etc/default/docker is expected to be readable by other
     ✔  File /etc/default/docker is expected not to be writable by other
     ✔  File /etc/default/docker is expected not to be executable by other
  ↺  docker-6.1: Perform regular security audits of your host system and containers
     ↺  Perform regular security audits of your host system and containers
  ↺  docker-6.2: Monitor Docker containers usage, performance and metering
     ↺  Monitor Docker containers usage, performance and metering
  ↺  docker-6.3: Backup container data
     ↺  Backup container data
  ×  host-6.4: Avoid image sprawl
     ×  ["sha256:1fca6beaeb5f7ff7bd127ba0547ddf26b3dbdadb6a40aefd952a4ef4c998ea4b", "sha256:5ce65d7b0fde20d6c6472e817df61f9b2d8ccd349d6d4d70d2f6305a99c73448", "sha256:58db3edaf2be6e80f628796355b1bdeaf8bea1692b402f48b7e7b8d1ff100b02", "sha256:1f83439a7b133710bdc39ddc6b108d75293adc96e316fdbc646c5a7d9186f07e", "sha256:43b6816e76c68d5359304334406738b7de10e807834239e5a570390f6c4d92b3", "sha256:feb5d9fea6a5e9606aa995e879d862b825965ba48de054caab5ef356dc6b3412", "sha256:2d4710ed0553536b8eb13d5c72cbc273a792ec1e5c432dc212379722ad29bf72"] is expected to be empty
     expected `["sha256:1fca6beaeb5f7ff7bd127ba0547ddf26b3dbdadb6a40aefd952a4ef4c998ea4b", "sha256:5ce65d7b0fde20d6c...de054caab5ef356dc6b3412", "sha256:2d4710ed0553536b8eb13d5c72cbc273a792ec1e5c432dc212379722ad29bf72"].empty?` to be truthy, got false
  ✔  host-6.5: Avoid container sprawl
     ✔  0 is expected to be <= 25
  ×  host-1.1: Create a separate partition for containers
     ×  Mount /var/lib/docker is expected to be mounted
     
     Mount /var/lib/docker is not mounted

  ✔  host-1.2: Use the updated Linux Kernel
     ✔  true is expected to eq true
  ↺  host-1.3: Harden the container host
     ↺  Harden the container host. Use the Dev-Sec Hardening Framework
  ↺  host-1.4: Remove all non-essential services from the host
     ↺  Remove all non-essential services from the host. Use the Dev-Sec Hardening Framework
  ✔  host-1.5: Keep Docker up to date
     ✔  Docker Host version.Client.Version is expected to cmp >= "17.06"
     ✔  Docker Host version.Server.Version is expected to cmp >= "17.06"
  ×  host-1.6: Only allow trusted users to control Docker daemon (1 failed)
     ✔  Group docker is expected to exist
     ×  #<Inspec::Resources::EtcGroupView:0x00007fa1e2e40af8> users is expected to include "vagrant"
     expected ["hp"] to include "vagrant"
  ×  host-1.7: Audit docker daemon (4 failed)
     ×  Auditd Rules 
     Command `/sbin/auditctl` does not exist
     ×  Service auditd is expected to be installed
     expected that `Service auditd` is installed
     ×  Service auditd is expected to be enabled
     expected that `Service auditd` is enabled
     ×  Service auditd is expected to be running
     expected that `Service auditd` is running
  ×  host-1.8: Audit Docker files and directories - /var/lib/docker
     ×  Auditd Rules 
     Command `/sbin/auditctl` does not exist
  ×  host-1.9: Audit Docker files and directories - /etc/docker
     ×  Auditd Rules 
     Command `/sbin/auditctl` does not exist
  ×  host-1.10: Audit Docker files and directories - docker.service
     ×  Auditd Rules 
     Command `/sbin/auditctl` does not exist
  ×  host-1.11: Audit Docker files and directories - docker.socket
     ×  Auditd Rules 
     Command `/sbin/auditctl` does not exist
  ×  host-1.12: Audit Docker files and directories - /etc/default/docker
     ×  Auditd Rules 
     Command `/sbin/auditctl` does not exist
  ×  host-1.13: Audit Docker files and directories - /etc/docker/daemon.json
     ×  Auditd Rules 
     Command `/sbin/auditctl` does not exist
  ×  host-1.14: Audit Docker files and directories - /usr/bin/docker-containerd
     ×  Auditd Rules 
     Command `/sbin/auditctl` does not exist
  ×  host-1.15: Audit Docker files and directories - /usr/bin/docker-runc
     ×  Auditd Rules 
     Command `/sbin/auditctl` does not exist


Profile Summary: 20 successful controls, 39 control failures, 18 controls skipped
Test Summary: 120 successful, 92 failures, 18 skipped

```
