login to server where pangolin will be installed

```
% ssh root@<myserver>
Welcome to Ubuntu 24.04.2 LTS (GNU/Linux 6.8.0-60-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/pro

 System information as of Tue Jul  1 06:56:23 AM UTC 2025

  System load:  0.0               Processes:             121
  Usage of /:   3.0% of 37.23GB   Users logged in:       0
  Memory usage: 5%                IPv4 address for eth0: 91.99.53.26
  Swap usage:   0%                IPv6 address for eth0: 2a01:4f8:1c1e:5234::1


Expanded Security Maintenance for Applications is not enabled.

0 updates can be applied immediately.

Enable ESM Apps to receive additional future security updates.
See https://ubuntu.com/esm or run: sudo pro status


The list of available updates is more than a week old.
To check for new updates run: sudo apt update

Last login: Tue Jul  1 06:56:23 2025 from 193.175.120.37
root@ubuntu-4gb-nbg1-tunnel:~# 
```

make directory pangolin and download pangolin installer

```
root@ubuntu-4gb-nbg1-tunnel:~# pwd
/root
root@ubuntu-4gb-nbg1-tunnel:~# mkdir pangolin
root@ubuntu-4gb-nbg1-tunnel:~# cd pangolin
root@ubuntu-4gb-nbg1-tunnel:~/pangolin# wget -O installer "https://github.com/fosrl/pangolin/releases/download/1.6.1/installer_linux_$(uname -m | sed 's/x86_64/amd64/;s/aarch64/arm64/')" && chmod +x ./installer
--2025-07-01 07:27:48--  https://github.com/fosrl/pangolin/releases/download/1.6.1/installer_linux_amd64
Resolving github.com (github.com)... 140.82.121.4
Connecting to github.com (github.com)|140.82.121.4|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://objects.githubusercontent.com/github-production-release-asset-2e65be/863835427/9d3fe857-8f98-4565-887c-d64a65bd25f9?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=releaseassetproduction%2F20250701%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250701T072748Z&X-Amz-Expires=1800&X-Amz-Signature=23b0820e7ddbdf64e17cef435ad46bc9f830a84396bad7ac19a2da36135c7895&X-Amz-SignedHeaders=host&response-content-disposition=attachment%3B%20filename%3Dinstaller_linux_amd64&response-content-type=application%2Foctet-stream [following]
--2025-07-01 07:27:48--  https://objects.githubusercontent.com/github-production-release-asset-2e65be/863835427/9d3fe857-8f98-4565-887c-d64a65bd25f9?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=releaseassetproduction%2F20250701%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250701T072748Z&X-Amz-Expires=1800&X-Amz-Signature=23b0820e7ddbdf64e17cef435ad46bc9f830a84396bad7ac19a2da36135c7895&X-Amz-SignedHeaders=host&response-content-disposition=attachment%3B%20filename%3Dinstaller_linux_amd64&response-content-type=application%2Foctet-stream
Resolving objects.githubusercontent.com (objects.githubusercontent.com)... 185.199.108.133, 185.199.109.133, 185.199.110.133, ...
Connecting to objects.githubusercontent.com (objects.githubusercontent.com)|185.199.108.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5322329 (5.1M) [application/octet-stream]
Saving to: ‘installer’

installer                            100%[======================================================================>]   5.08M  --.-KB/s    in 0.03s   

2025-07-01 07:27:49 (145 MB/s) - ‘installer’ saved [5322329/5322329]

root@ubuntu-4gb-nbg1-tunnel:~/pangolin# ls
installer
root@ubuntu-4gb-nbg1-tunnel:~/
```

start installer and set basic configuration according to https://www.youtube.com/watch?v=sXuUODTQekI

```
root@ubuntu-4gb-nbg1-tunnel:~/pangolin# ./installer 

=== Basic Configuration ===
Enter your base domain (no subdomain e.g. example.com): th-luebeck.me
Enter the domain for the Pangolin dashboard (default: pangolin.th-luebeck.me): 
Enter email for Let's Encrypt certificates: horst.hellbrueck@th-luebeck.de
Do you want to use Gerbil to allow tunneled connections (yes/no) (default: yes): 

=== Email Configuration ===
Enable email functionality (SMTP) (yes/no) (default: no): 
Docker is not installed. Would you like to install it? (yes/no) (default: yes): 
Get:1 https://mirror.hetzner.com/ubuntu/packages noble InRelease [256 kB]
Get:2 https://mirror.hetzner.com/ubuntu/packages noble-updates InRelease [126 kB]
Get:3 https://mirror.hetzner.com/ubuntu/packages noble-backports InRelease [126 kB]
Get:4 https://mirror.hetzner.com/ubuntu/security noble-security InRelease [126 kB]
Get:5 https://mirror.hetzner.com/ubuntu/packages noble/main amd64 Packages [1401 kB]
Get:6 https://mirror.hetzner.com/ubuntu/packages noble/main Translation-en [513 kB]
Get:7 https://mirror.hetzner.com/ubuntu/packages noble/main amd64 c-n-f Metadata [30.5 kB]
Get:8 https://mirror.hetzner.com/ubuntu/packages noble/universe amd64 Packages [15.0 MB]
Get:9 https://mirror.hetzner.com/ubuntu/packages noble/universe Translation-en [5982 kB]
Get:10 https://mirror.hetzner.com/ubuntu/packages noble/universe amd64 c-n-f Metadata [301 kB]
Get:11 https://mirror.hetzner.com/ubuntu/packages noble/restricted amd64 Packages [93.9 kB]
Get:12 https://mirror.hetzner.com/ubuntu/packages noble/restricted Translation-en [18.7 kB]
Get:13 https://mirror.hetzner.com/ubuntu/packages noble/restricted amd64 c-n-f Metadata [416 B]
Get:14 https://mirror.hetzner.com/ubuntu/packages noble/multiverse amd64 Packages [269 kB]
Get:15 https://mirror.hetzner.com/ubuntu/packages noble/multiverse Translation-en [118 kB]
Get:16 https://mirror.hetzner.com/ubuntu/packages noble/multiverse amd64 c-n-f Metadata [8328 B]
Get:17 https://mirror.hetzner.com/ubuntu/packages noble-updates/main amd64 Packages [1170 kB]
Get:18 https://mirror.hetzner.com/ubuntu/packages noble-updates/main Translation-en [246 kB]
Get:19 https://mirror.hetzner.com/ubuntu/packages noble-updates/main amd64 c-n-f Metadata [13.5 kB]
Get:20 https://mirror.hetzner.com/ubuntu/packages noble-updates/universe amd64 Packages [1092 kB]
Get:21 https://mirror.hetzner.com/ubuntu/packages noble-updates/universe Translation-en [278 kB]
Get:22 https://mirror.hetzner.com/ubuntu/packages noble-updates/universe amd64 c-n-f Metadata [26.0 kB]
Get:23 https://mirror.hetzner.com/ubuntu/packages noble-updates/restricted amd64 Packages [1279 kB]
Get:24 https://mirror.hetzner.com/ubuntu/packages noble-updates/restricted Translation-en [272 kB]
Get:25 https://mirror.hetzner.com/ubuntu/packages noble-updates/restricted amd64 c-n-f Metadata [492 B]
Get:26 https://mirror.hetzner.com/ubuntu/packages noble-updates/multiverse amd64 Packages [22.1 kB]
Get:27 https://mirror.hetzner.com/ubuntu/packages noble-updates/multiverse Translation-en [4972 B]
Get:28 https://mirror.hetzner.com/ubuntu/packages noble-updates/multiverse amd64 c-n-f Metadata [592 B]
Get:29 https://mirror.hetzner.com/ubuntu/packages noble-backports/main amd64 Packages [39.2 kB]
Get:30 https://mirror.hetzner.com/ubuntu/packages noble-backports/main Translation-en [8676 B]
Get:31 https://mirror.hetzner.com/ubuntu/packages noble-backports/main amd64 c-n-f Metadata [272 B]
Get:32 https://mirror.hetzner.com/ubuntu/packages noble-backports/universe amd64 Packages [27.1 kB]
Get:33 https://mirror.hetzner.com/ubuntu/packages noble-backports/universe Translation-en [16.5 kB]
Get:34 https://mirror.hetzner.com/ubuntu/packages noble-backports/universe amd64 c-n-f Metadata [1304 B]
Get:35 https://mirror.hetzner.com/ubuntu/packages noble-backports/restricted amd64 c-n-f Metadata [116 B]
Get:36 https://mirror.hetzner.com/ubuntu/packages noble-backports/multiverse amd64 c-n-f Metadata [116 B]
Get:37 https://mirror.hetzner.com/ubuntu/security noble-security/main amd64 Packages [920 kB]
Get:38 https://mirror.hetzner.com/ubuntu/security noble-security/main Translation-en [169 kB]
Get:39 https://mirror.hetzner.com/ubuntu/security noble-security/main amd64 c-n-f Metadata [7068 B]
Get:40 https://mirror.hetzner.com/ubuntu/security noble-security/universe amd64 Packages [860 kB]
Get:41 https://mirror.hetzner.com/ubuntu/security noble-security/universe Translation-en [188 kB]
Get:42 https://mirror.hetzner.com/ubuntu/security noble-security/universe amd64 c-n-f Metadata [17.0 kB]
Get:43 https://mirror.hetzner.com/ubuntu/security noble-security/restricted amd64 Packages [1235 kB]
Get:44 https://mirror.hetzner.com/ubuntu/security noble-security/restricted Translation-en [263 kB]
Get:45 https://mirror.hetzner.com/ubuntu/security noble-security/restricted amd64 c-n-f Metadata [468 B]
Get:46 https://mirror.hetzner.com/ubuntu/security noble-security/multiverse amd64 Packages [17.7 kB]
Get:47 https://mirror.hetzner.com/ubuntu/security noble-security/multiverse Translation-en [3792 B]
Get:48 https://mirror.hetzner.com/ubuntu/security noble-security/multiverse amd64 c-n-f Metadata [380 B]
Fetched 32.6 MB in 6s (5717 kB/s)               
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
ca-certificates is already the newest version (20240203).
ca-certificates set to manually installed.
curl is already the newest version (8.5.0-2ubuntu10.6).
software-properties-common is already the newest version (0.99.49.2).
The following NEW packages will be installed:
  apt-transport-https
0 upgraded, 1 newly installed, 0 to remove and 11 not upgraded.
Need to get 3970 B of archives.
After this operation, 36.9 kB of additional disk space will be used.
Get:1 https://mirror.hetzner.com/ubuntu/packages noble-updates/universe amd64 apt-transport-https all 2.8.3 [3970 B]
Fetched 3970 B in 0s (51.6 kB/s)              
Selecting previously unselected package apt-transport-https.
(Reading database ... 38533 files and directories currently installed.)
Preparing to unpack .../apt-transport-https_2.8.3_all.deb ...
Unpacking apt-transport-https (2.8.3) ...
Setting up apt-transport-https (2.8.3) ...
Scanning processes...                                                                                                                               
Scanning linux images...                                                                                                                            

Running kernel seems to be up-to-date.

No services need to be restarted.

No containers need to be restarted.

No user sessions are running outdated binaries.

No VM guests are running outdated hypervisor (qemu) binaries on this host.
Get:1 https://download.docker.com/linux/ubuntu noble InRelease [48.8 kB]
Hit:2 https://mirror.hetzner.com/ubuntu/packages noble InRelease                      
Hit:3 https://mirror.hetzner.com/ubuntu/packages noble-updates InRelease
Hit:4 https://mirror.hetzner.com/ubuntu/packages noble-backports InRelease
Hit:5 https://mirror.hetzner.com/ubuntu/security noble-security InRelease
Get:6 https://download.docker.com/linux/ubuntu noble/stable amd64 Packages [26.9 kB]
Fetched 75.7 kB in 1s (131 kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  docker-buildx-plugin docker-ce-rootless-extras libltdl7 libslirp0 pigz slirp4netns
Suggested packages:
  cgroupfs-mount | cgroup-lite docker-model-plugin
The following NEW packages will be installed:
  containerd.io docker-buildx-plugin docker-ce docker-ce-cli docker-ce-rootless-extras docker-compose-plugin libltdl7 libslirp0 pigz slirp4netns
0 upgraded, 10 newly installed, 0 to remove and 11 not upgraded.
Need to get 103 MB of archives.
After this operation, 429 MB of additional disk space will be used.
Get:1 https://download.docker.com/linux/ubuntu noble/stable amd64 containerd.io amd64 1.7.27-1 [30.5 MB]
Get:2 https://mirror.hetzner.com/ubuntu/packages noble/universe amd64 pigz amd64 2.8-1 [65.6 kB]
Get:3 https://mirror.hetzner.com/ubuntu/packages noble/main amd64 libltdl7 amd64 2.4.7-7build1 [40.3 kB]
Get:4 https://mirror.hetzner.com/ubuntu/packages noble/main amd64 libslirp0 amd64 4.7.0-1ubuntu3 [63.8 kB]
Get:5 https://mirror.hetzner.com/ubuntu/packages noble/universe amd64 slirp4netns amd64 1.2.1-1build2 [34.9 kB]
Get:6 https://download.docker.com/linux/ubuntu noble/stable amd64 docker-ce-cli amd64 5:28.3.0-1~ubuntu.24.04~noble [16.5 MB]
Get:7 https://download.docker.com/linux/ubuntu noble/stable amd64 docker-ce amd64 5:28.3.0-1~ubuntu.24.04~noble [19.7 MB]
Get:8 https://download.docker.com/linux/ubuntu noble/stable amd64 docker-buildx-plugin amd64 0.25.0-1~ubuntu.24.04~noble [15.6 MB]
Get:9 https://download.docker.com/linux/ubuntu noble/stable amd64 docker-ce-rootless-extras amd64 5:28.3.0-1~ubuntu.24.04~noble [6480 kB]
Get:10 https://download.docker.com/linux/ubuntu noble/stable amd64 docker-compose-plugin amd64 2.37.3-1~ubuntu.24.04~noble [14.2 MB]
Fetched 103 MB in 2s (67.1 MB/s)                 
Selecting previously unselected package containerd.io.
(Reading database ... 38537 files and directories currently installed.)
Preparing to unpack .../0-containerd.io_1.7.27-1_amd64.deb ...
Unpacking containerd.io (1.7.27-1) ...
Selecting previously unselected package docker-ce-cli.
Preparing to unpack .../1-docker-ce-cli_5%3a28.3.0-1~ubuntu.24.04~noble_amd64.deb ...
Unpacking docker-ce-cli (5:28.3.0-1~ubuntu.24.04~noble) ...
Selecting previously unselected package docker-ce.
Preparing to unpack .../2-docker-ce_5%3a28.3.0-1~ubuntu.24.04~noble_amd64.deb ...
Unpacking docker-ce (5:28.3.0-1~ubuntu.24.04~noble) ...
Selecting previously unselected package pigz.
Preparing to unpack .../3-pigz_2.8-1_amd64.deb ...
Unpacking pigz (2.8-1) ...
Selecting previously unselected package docker-buildx-plugin.
Preparing to unpack .../4-docker-buildx-plugin_0.25.0-1~ubuntu.24.04~noble_amd64.deb ...
Unpacking docker-buildx-plugin (0.25.0-1~ubuntu.24.04~noble) ...
Selecting previously unselected package docker-ce-rootless-extras.
Preparing to unpack .../5-docker-ce-rootless-extras_5%3a28.3.0-1~ubuntu.24.04~noble_amd64.deb ...
Unpacking docker-ce-rootless-extras (5:28.3.0-1~ubuntu.24.04~noble) ...
Selecting previously unselected package docker-compose-plugin.
Preparing to unpack .../6-docker-compose-plugin_2.37.3-1~ubuntu.24.04~noble_amd64.deb ...
Unpacking docker-compose-plugin (2.37.3-1~ubuntu.24.04~noble) ...
Selecting previously unselected package libltdl7:amd64.
Preparing to unpack .../7-libltdl7_2.4.7-7build1_amd64.deb ...
Unpacking libltdl7:amd64 (2.4.7-7build1) ...
Selecting previously unselected package libslirp0:amd64.
Preparing to unpack .../8-libslirp0_4.7.0-1ubuntu3_amd64.deb ...
Unpacking libslirp0:amd64 (4.7.0-1ubuntu3) ...
Selecting previously unselected package slirp4netns.
Preparing to unpack .../9-slirp4netns_1.2.1-1build2_amd64.deb ...
Unpacking slirp4netns (1.2.1-1build2) ...
Setting up docker-buildx-plugin (0.25.0-1~ubuntu.24.04~noble) ...
Setting up containerd.io (1.7.27-1) ...
Created symlink /etc/systemd/system/multi-user.target.wants/containerd.service → /usr/lib/systemd/system/containerd.service.
Setting up docker-compose-plugin (2.37.3-1~ubuntu.24.04~noble) ...
Setting up libltdl7:amd64 (2.4.7-7build1) ...
Setting up docker-ce-cli (5:28.3.0-1~ubuntu.24.04~noble) ...
Setting up libslirp0:amd64 (4.7.0-1ubuntu3) ...
Setting up pigz (2.8-1) ...
Setting up docker-ce-rootless-extras (5:28.3.0-1~ubuntu.24.04~noble) ...
Setting up slirp4netns (1.2.1-1build2) ...
Setting up docker-ce (5:28.3.0-1~ubuntu.24.04~noble) ...
Created symlink /etc/systemd/system/multi-user.target.wants/docker.service → /usr/lib/systemd/system/docker.service.
Created symlink /etc/systemd/system/sockets.target.wants/docker.socket → /usr/lib/systemd/system/docker.socket.
Processing triggers for man-db (2.12.0-4build2) ...
Processing triggers for libc-bin (2.39-0ubuntu8.4) ...
Scanning processes...                                                                                                                               
Scanning linux images...                                                                                                                            

Running kernel seems to be up-to-date.

No services need to be restarted.

No containers need to be restarted.

No user sessions are running outdated binaries.

No VM guests are running outdated hypervisor (qemu) binaries on this host.
Synchronizing state of docker.service with SysV service script with /usr/lib/systemd/systemd-sysv-install.
Executing: /usr/lib/systemd/systemd-sysv-install enable docker
Docker service started successfully!
Waiting for Docker to start...
Docker is running!
Docker installed successfully!

=== Starting installation ===
Would you like to install and start the containers? (yes/no) (default: yes): 
Pulling the container images...
[+] Pulling 28/28
 ✔ gerbil Pulled                                                                                                                               8.3s 
   ✔ 9cb31e2e37ea Pull complete                                                                                                                5.4s 
   ✔ 0f890e730b30 Pull complete                                                                                                                6.0s 
   ✔ d769b24bf685 Pull complete                                                                                                                6.4s 
   ✔ d6e42e66b7a4 Pull complete                                                                                                                6.5s 
   ✔ 4b9f016be772 Pull complete                                                                                                                6.5s 
 ✔ traefik Pulled                                                                                                                              8.8s 
   ✔ f18232174bc9 Pull complete                                                                                                                0.8s 
   ✔ 22ff649176b0 Pull complete                                                                                                                1.1s 
   ✔ 6bb594ddbc12 Pull complete                                                                                                                7.0s 
   ✔ 64c9803dbe74 Pull complete                                                                                                                7.0s 
 ✔ pangolin Pulled                                                                                                                            41.8s 
   ✔ fe07684b16b8 Pull complete                                                                                                                2.5s 
   ✔ 5432aa916e08 Pull complete                                                                                                                8.8s 
   ✔ 2506673f5536 Pull complete                                                                                                                8.9s 
   ✔ 98c4889b578e Pull complete                                                                                                                8.9s 
   ✔ b7685f597395 Pull complete                                                                                                                8.9s 
   ✔ 84cbd7661967 Pull complete                                                                                                                9.0s 
   ✔ e738455b64dc Pull complete                                                                                                                9.0s 
   ✔ a797f9c855c2 Pull complete                                                                                                               37.8s 
   ✔ 82636d3d95d1 Pull complete                                                                                                               39.7s 
   ✔ 4629b47d1438 Pull complete                                                                                                               39.8s 
   ✔ 40d280198ee0 Pull complete                                                                                                               39.9s 
   ✔ 64e0b4b9356d Pull complete                                                                                                               39.9s 
   ✔ e8550c16d6b0 Pull complete                                                                                                               39.9s 
   ✔ e6149eb31062 Pull complete                                                                                                               39.9s 
   ✔ d41423072a11 Pull complete                                                                                                               40.0s 
   ✔ a9bfc27f8ef6 Pull complete                                                                                                               40.0s 
Starting containers...
[+] Running 4/4
 ✔ Network pangolin    Created                                                                                                                 0.1s 
 ✔ Container pangolin  Healthy                                                                                                                12.1s 
 ✔ Container gerbil    Started                                                                                                                11.3s 
 ✔ Container traefik   Started                                                                                                                12.0s 

=== CrowdSec Install ===
Would you like to install CrowdSec? (yes/no) (default: no): yes
This installer constitutes a minimal viable CrowdSec deployment. CrowdSec will add extra complexity to your Pangolin installation and may not work to the best of its abilities out of the box. Users are expected to implement configuration adjustments on their own to achieve the best security posture. Consult the CrowdSec documentation for detailed configuration instructions.
Are you willing to manage CrowdSec? (yes/no) (default: no): 
Installation complete!

To complete the initial setup, please visit:
https://pangolin.th-luebeck.me/auth/initial-setup
```