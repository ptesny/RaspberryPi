vscode
=========================

https://www.raspberrypi.org/forums/viewtopic.php?t=231073


```
mkdir vstudio
cd vstudio
wget -O apt.sh https://code.headmelted.com/installers/apt.sh
chmod +x apt.sh
nano apt.sh
# change these two lines (comment out) so we now have:
#apt-get install -t ${repo_name} -y ${code_executable_name};
apt-get install -t ${repo_name} -y --allow-unauthenticated ${code_executable_name};
save and exit
sudo ./apt.sh
```

```
pi@phoscon:~ $ mkdir vstudio
pi@phoscon:~ $ cd vstudio/
pi@phoscon:~/vstudio $ wget -O apt.sh https://code.headmelted.com/installers/apt.sh
--2020-02-20 14:42:11--  https://code.headmelted.com/installers/apt.sh
Resolving code.headmelted.com (code.headmelted.com)... 104.27.186.80, 104.27.187.80, 2606:4700:3035::681b:bb50, ...
Connecting to code.headmelted.com (code.headmelted.com)|104.27.186.80|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [application/x-sh]
Saving to: ‘apt.sh’

apt.sh                                                     [ <=>                                                                                                                        ]   2.30K  --.-KB/s    in 0s      

2020-02-20 14:42:11 (9.61 MB/s) - ‘apt.sh’ saved [2352]

pi@phoscon:~/vstudio $ chmod +x apt.sh
pi@phoscon:~/vstudio $ sudo nano apt.sh 
pi@phoscon:~/vstudio $ sudo ./apt.sh 
Detecting architecture...
Ensuring curl is installed
Reading package lists... Done
Building dependency tree       
Reading state information... Done
curl is already the newest version (7.64.0-4).
The following packages were automatically installed and are no longer required:
  libjs-sphinxdoc libjs-underscore python-dbus python-secretstorage
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 133 not upgraded.
Architecture detected as armv7l...
Retrieving GPG key [headmelted] (https://packagecloud.io/headmelted/codebuilds/gpgkey)...
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
100  3949  100  3949    0     0   4757      0 --:--:-- --:--:-- --:--:--  4757
Removing any previous entry to headmelted repository
Installing [headmelted] repository...
Updating APT cache...
Hit:1 http://raspbian.raspberrypi.org/raspbian buster InRelease
Hit:2 http://archive.raspberrypi.org/debian buster InRelease
Hit:3 https://download.docker.com/linux/raspbian buster InRelease
Hit:4 http://phoscon.de/apt/deconz buster-beta InRelease
Hit:5 https://deb.nodesource.com/node_10.x buster InRelease
Get:7 https://packagecloud.io/headmelted/codebuilds/debian stretch InRelease [23.4 kB]
Hit:6 https://cf-cli-debian-repo.s3.amazonaws.com stable InRelease
Get:8 https://packagecloud.io/headmelted/codebuilds/debian stretch/main armhf Packages [4,134 B]
Fetched 27.5 kB in 3s (8,018 B/s)
Reading package lists...
Done!
Repository install complete.
Installing Visual Studio Code from [stretch]...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libjs-sphinxdoc libjs-underscore python-dbus python-secretstorage
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  code-oss
0 upgraded, 1 newly installed, 0 to remove and 133 not upgraded.
Need to get 60.4 MB of archives.
After this operation, 234 MB of additional disk space will be used.
Get:1 https://packagecloud.io/headmelted/codebuilds/debian stretch/main armhf code-oss armhf 1.43.0-1581920809 [60.4 MB]
Fetched 60.4 MB in 44s (1,371 kB/s)                                                                                                                                                                                       
Selecting previously unselected package code-oss.
(Reading database ... 163229 files and directories currently installed.)
Preparing to unpack .../code-oss_1.43.0-1581920809_armhf.deb ...
Unpacking code-oss (1.43.0-1581920809) ...
Setting up code-oss (1.43.0-1581920809) ...
Retrieving GPG key [headmelted] (https://packagecloud.io/headmelted/codebuilds/gpgkey)...
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
gpg: no valid OpenPGP data found.
Removing any previous entry to headmelted repository
Installing [headmelted] repository...
Updating APT cache...
Hit:1 http://phoscon.de/apt/deconz buster-beta InRelease
Hit:2 http://raspbian.raspberrypi.org/raspbian buster InRelease
Hit:3 http://archive.raspberrypi.org/debian buster InRelease
Hit:4 https://deb.nodesource.com/node_10.x buster InRelease
Hit:5 https://download.docker.com/linux/raspbian buster InRelease
Hit:6 https://cf-cli-debian-repo.s3.amazonaws.com stable InRelease
Hit:7 https://packagecloud.io/headmelted/codebuilds/debian stretch InRelease
Err:7 https://packagecloud.io/headmelted/codebuilds/debian stretch InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0CC3FD642696BFC8
Reading package lists...
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: https://packagecloud.io/headmelted/codebuilds/debian stretch InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0CC3FD642696BFC8
W: Failed to fetch https://packagecloud.io/headmelted/codebuilds/debian/dists/stretch/InRelease  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0CC3FD642696BFC8
W: Some index files failed to download. They have been ignored, or old ones used instead.
Done!
Processing triggers for mime-support (3.62) ...
Processing triggers for gnome-menus (3.31.4-3) ...
Processing triggers for desktop-file-utils (0.23-4) ...
Visual Studio Code install complete.
Installing git...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
git is already the newest version (1:2.20.1-2+deb10u1).
The following packages were automatically installed and are no longer required:
  libjs-sphinxdoc libjs-underscore python-dbus python-secretstorage
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 133 not upgraded.
git install complete.
Installing any dependencies that may have been missed...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libjs-sphinxdoc libjs-underscore python-dbus python-secretstorage
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 133 not upgraded.
Missed dependency install complete.


Installation complete!

You can start code at any time by calling "code-oss" within a terminal.

A shortcut should also now be available in your desktop menus (depending on your distribution).


pi@phoscon:~/vstudio $ code-oss

```

using the X11 (XQuartz) terminal on macOS

```
$ ssh -Y pi@192.168.2.2
$ code-oss
```

here go the vscode credentials:

```
Version: 1.43.0 (user setup)
Commit: 6ec6f9e3f4d17f0cef0480688a1f350b9141e567
Date: 2020-02-17T06:26:19.948Z
Electron: 7.1.11
Chrome: 78.0.3904.130
Node.js: 12.8.1
V8: 7.8.279.23-electron.0
OS: Linux arm 4.19.75-v7l+
```

