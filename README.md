# RaspberryPi for _plumbers_ and DIY cloud foundry developers
RaspberryPi tools for running docker images and CloudFoundry operations

Raspbian (aka arm debian) [documentation](https://www.raspberrypi.org/documentation/raspbian/)  
Raspbian [remote](https://www.raspberrypi.org/documentation/remote-access/ssh/unix.md) access.


## install docker

[install docker](https://dev.to/rohansawant/installing-docker-and-docker-compose-on-the-raspberry-pi-in-5-simple-steps-3mgl)

```
$ curl -sSL get.docker.com | sh
$ sudo usermod -aG docker pi
$ sudo apt-get install libffi-dev libssl-dev
$ sudo apt-get install -y python3 python3-pip
$ sudo apt-get remove python-configparser (apparently this isn't installed by using my commands on a clean install)
$ sudo pip install docker-compose 
or alternatively
$ sudo pip install docker-compose --ignore-installed PyYAML
```

# Building multi-target applications (MTA) for Cloud Foundry using your RaspberryPi

## installing java jdk on Raspberry Pi

[java](https://linuxize.com/post/install-java-on-raspberry-pi/)


## installing Node.js and npm on Raspberry Pi

[nodejs && npm](https://linuxize.com/post/how-to-install-node-js-on-raspberry-pi/)

```
$ curl -sL https://deb.nodesource.com/setup_10.x | sudo bash -

## Installing the NodeSource Node.js 10.x repo...


## Populating apt-get cache...

+ apt-get update
Get:1 http://archive.raspberrypi.org/debian buster InRelease [25.1 kB]
Get:2 http://raspbian.raspberrypi.org/raspbian buster InRelease [15.0 kB]                                                                                                                      
Hit:3 http://phoscon.de/apt/deconz buster-beta InRelease                                                                                                                                                   
Hit:4 https://download.docker.com/linux/raspbian buster InRelease                                                                                                                                          
Get:6 http://archive.raspberrypi.org/debian buster/main armhf Packages [277 kB]    
Hit:5 https://cf-cli-debian-repo.s3.amazonaws.com stable InRelease                                  
Fetched 317 kB in 2s (183 kB/s)
Reading package lists... Done

## Confirming "buster" is supported...

+ curl -sLf -o /dev/null 'https://deb.nodesource.com/node_10.x/dists/buster/Release'

## Adding the NodeSource signing key to your keyring...

+ curl -s https://deb.nodesource.com/gpgkey/nodesource.gpg.key | apt-key add -
OK

## Creating apt sources list file for the NodeSource Node.js 10.x repo...

+ echo 'deb https://deb.nodesource.com/node_10.x buster main' > /etc/apt/sources.list.d/nodesource.list
+ echo 'deb-src https://deb.nodesource.com/node_10.x buster main' >> /etc/apt/sources.list.d/nodesource.list

## Running `apt-get update` for you...

+ apt-get update
Hit:1 http://phoscon.de/apt/deconz buster-beta InRelease
Hit:2 http://raspbian.raspberrypi.org/raspbian buster InRelease                                                                                                                                            
Hit:3 http://archive.raspberrypi.org/debian buster InRelease                                                                                                                                               
Hit:4 https://download.docker.com/linux/raspbian buster InRelease                                                                                                                    
Get:5 https://deb.nodesource.com/node_10.x buster InRelease [4,584 B]                                                                                          
Hit:6 https://cf-cli-debian-repo.s3.amazonaws.com stable InRelease                           
Get:7 https://deb.nodesource.com/node_10.x buster/main armhf Packages [766 B]
Fetched 5,350 B in 2s (2,864 B/s)
Reading package lists... Done

## Run `sudo apt-get install -y nodejs` to install Node.js 10.x and npm
## You may also need development tools to build native addons:
     sudo apt-get install gcc g++ make
## To install the Yarn package manager, run:
     curl -sL https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
     echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
     sudo apt-get update && sudo apt-get install yarn


```

install nodejs itself


```
$ sudo apt-get install -y nodejs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libjs-sphinxdoc libjs-underscore python-dbus python-secretstorage
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  nodejs
0 upgraded, 1 newly installed, 0 to remove and 127 not upgraded.
Need to get 14.6 MB of archives.
After this operation, 77.3 MB of additional disk space will be used.
Get:1 https://deb.nodesource.com/node_10.x buster/main armhf nodejs armhf 10.19.0-1nodesource1 [14.6 MB]
Fetched 14.6 MB in 24s (614 kB/s)                                                                                                                                                                                         
Selecting previously unselected package nodejs.
(Reading database ... 147973 files and directories currently installed.)
Preparing to unpack .../nodejs_10.19.0-1nodesource1_armhf.deb ...
Unpacking nodejs (10.19.0-1nodesource1) ...
Setting up nodejs (10.19.0-1nodesource1) ...
Processing triggers for man-db (2.8.5-2) ...
pi@phoscon:~ $ node --version
v10.19.0

```
## Cloud Foundry CLI binaries for Raspberry Pi

[cli](https://github.com/mmb/cf-cli-pi)

Get the latest binary from:

https://cf-cli-pi.s3.amazonaws.com/index.html

put it somewhere in your path (like `/usr/local/bin`) and `chmod +x` it.

Here goes the cf cli official client [repo](https://github.com/cloudfoundry/cli)

## cf MTA

Parsers, validators, persistence and utilities for Multi-Target Application (MTA) models:
  * https://github.com/cloudfoundry-incubator/multiapps
  * https://blogs.sap.com/2018/02/05/building-multi-target-applications-mta-for-cloud-foundry-using-your-favorite-ide/


## cf multiapps plugin

A CLI plugin for Multi-Target Application (MTA) operations in Cloud Foundry:
  * https://github.com/cloudfoundry-incubator/multiapps-cli-plugin  
  * https://github.com/cloudfoundry-incubator/multiapps-cli-plugin/releases/tag/v2.2.1  
https://plugins.cloudfoundry.org/

## golang

https://github.com/golang/go/wiki/GoArm  
https://alexatnet.com/install-go-on-raspberry-pi/  

download the latest version from https://dl.google.com/go/go1.13.3.linux-armv6l.tar.gz

```
$ wget https://storage.googleapis.com/golang/go1.8.3.linux-armv6l.tar.gz
$ sudo tar -C /usr/local -xzf go1.8.3.linux-armv6l.tar.gz
$ export PATH=$PATH:/usr/local/go/bin
```
and then add `export PATH=$PATH:/usr/local/go/bin` to `~/.profile` to set it automatically on next login.

Or, alternatively you can use

```
sudo apt install golang

```

```
 $ sudo apt install golang
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libjs-sphinxdoc libjs-underscore python-dbus python-secretstorage
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  golang-1.11 golang-1.11-doc golang-1.11-go golang-1.11-src golang-doc golang-go golang-src
Suggested packages:
  bzr | brz mercurial subversion
The following NEW packages will be installed:
  golang golang-1.11 golang-1.11-doc golang-1.11-go golang-1.11-src golang-doc golang-go golang-src
0 upgraded, 8 newly installed, 0 to remove and 127 not upgraded.
Need to get 51.9 MB of archives.
After this operation, 258 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf golang-1.11-src armhf 1.11.6-1+rpi1+deb10u2 [13.0 MB]
Get:2 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf golang-1.11-go armhf 1.11.6-1+rpi1+deb10u2 [36.3 MB]                                                                                                     
Get:3 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf golang-1.11-doc all 1.11.6-1+rpi1+deb10u2 [2,517 kB]                                                                                                     
Get:4 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf golang-1.11 all 1.11.6-1+rpi1+deb10u2 [24.1 kB]                                                                                                          
Get:5 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf golang-src armhf 2:1.11~1+b6 [4,660 B]                                                                                                                   
Get:6 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf golang-go armhf 2:1.11~1+b6 [23.7 kB]                                                                                                                    
Get:7 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf golang-doc all 2:1.11~1 [4,392 B]                                                                                                                        
Get:8 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf golang armhf 2:1.11~1+b6 [4,612 B]                                                                                                                       
Fetched 51.9 MB in 1min 19s (656 kB/s)                                                                                                                                                                                    
Selecting previously unselected package golang-1.11-src.
(Reading database ... 152657 files and directories currently installed.)
Preparing to unpack .../0-golang-1.11-src_1.11.6-1+rpi1+deb10u2_armhf.deb ...
Unpacking golang-1.11-src (1.11.6-1+rpi1+deb10u2) ...
Selecting previously unselected package golang-1.11-go.
Preparing to unpack .../1-golang-1.11-go_1.11.6-1+rpi1+deb10u2_armhf.deb ...
Unpacking golang-1.11-go (1.11.6-1+rpi1+deb10u2) ...
Selecting previously unselected package golang-1.11-doc.
Preparing to unpack .../2-golang-1.11-doc_1.11.6-1+rpi1+deb10u2_all.deb ...
Unpacking golang-1.11-doc (1.11.6-1+rpi1+deb10u2) ...
Selecting previously unselected package golang-1.11.
Preparing to unpack .../3-golang-1.11_1.11.6-1+rpi1+deb10u2_all.deb ...
Unpacking golang-1.11 (1.11.6-1+rpi1+deb10u2) ...
Selecting previously unselected package golang-src.
Preparing to unpack .../4-golang-src_2%3a1.11~1+b6_armhf.deb ...
Unpacking golang-src (2:1.11~1+b6) ...
Selecting previously unselected package golang-go.
Preparing to unpack .../5-golang-go_2%3a1.11~1+b6_armhf.deb ...
Unpacking golang-go (2:1.11~1+b6) ...
Selecting previously unselected package golang-doc.
Preparing to unpack .../6-golang-doc_2%3a1.11~1_all.deb ...
Unpacking golang-doc (2:1.11~1) ...
Selecting previously unselected package golang.
Preparing to unpack .../7-golang_2%3a1.11~1+b6_armhf.deb ...
Unpacking golang (2:1.11~1+b6) ...
Setting up golang-1.11-src (1.11.6-1+rpi1+deb10u2) ...
Setting up golang-1.11-go (1.11.6-1+rpi1+deb10u2) ...
Setting up golang-src (2:1.11~1+b6) ...
Setting up golang-1.11-doc (1.11.6-1+rpi1+deb10u2) ...
Setting up golang-go (2:1.11~1+b6) ...
Setting up golang-1.11 (1.11.6-1+rpi1+deb10u2) ...
Setting up golang-doc (2:1.11~1) ...
Setting up golang (2:1.11~1+b6) ...
Processing triggers for man-db (2.8.5-2) ...
pi@phoscon:~ $ 
```

### GO development

if you need to install the multiapps plugin you may need to recompile the plugin source code accordingly:
https://github.com/golang/go/wiki/GoArm

  * Goto https://github.com/cloudfoundry-incubator/multiapps-cli-plugin
  * Clone the github reposiitory (for instance under your home directory)

```
pi@phoscon:~ $ pwd
/home/pi
pi@phoscon:~ $ mkdir -p go/src/github.com/cloudfoundry-incubator
pi@phoscon:~ $ cd go/src/github.com/cloudfoundry-incubator
pi@phoscon:~/go/src/github.com/cloudfoundry-incubator $ 
pi@phoscon:~/go/src/github.com/cloudfoundry-incubator $ git clone https://github.com/cloudfoundry-incubator/multiapps-cli-plugin.git
Cloning into 'multiapps-cli-plugin'...
remote: Enumerating objects: 60, done.
remote: Counting objects: 100% (60/60), done.
remote: Compressing objects: 100% (52/52), done.
remote: Total 2430 (delta 16), reused 24 (delta 8), pack-reused 2370
Receiving objects: 100% (2430/2430), 101.79 MiB | 350.00 KiB/s, done.
Resolving deltas: 100% (1248/1248), done.
Checking out files: 100% (914/914), done.

```

### Build new release version using the provided build.sh script

Please make sure you build for linux 32-bit arm architecture

```
pi@phoscon:~/go/src/github.com/cloudfoundry-incubator/multiapps-cli-plugin $ cp build.sh build.sh.orig
pi@phoscon:~/go/src/github.com/cloudfoundry-incubator/multiapps-cli-plugin $ 
pi@phoscon:~/go/src/github.com/cloudfoundry-incubator/multiapps-cli-plugin $ nano build.sh 
```

make the following changes in the *build.sh* script, namely:

```
version=$(<cfg/VERSION)
build $version linux arm $PLUGIN_NAME_LINUX_32

buildstatic $version linux arm $PLUGIN_NAME_STATIC_LINUX_32

```


```
pi@phoscon:~/go/src/github.com/cloudfoundry-incubator $ ls -alrt
total 12
drwxr-xr-x  3 pi pi 4096 Feb 18 23:03 ..
drwxr-xr-x  3 pi pi 4096 Feb 18 23:05 .
drwxr-xr-x 20 pi pi 4096 Feb 18 23:10 multiapps-cli-plugin
pi@phoscon:~/go/src/github.com/cloudfoundry-incubator $ cd multiapps-cli-plugin/
pi@phoscon:~/go/src/github.com/cloudfoundry-incubator/multiapps-cli-plugin $ ./build.sh 2.2.1
+++ realpath -- ./build.sh
++ dirname -- /home/pi/go/src/github.com/cloudfoundry-incubator/multiapps-cli-plugin/build.sh
+ script_dir=/home/pi/go/src/github.com/cloudfoundry-incubator/multiapps-cli-plugin
+ cd /home/pi/go/src/github.com/cloudfoundry-incubator/multiapps-cli-plugin
+ cd /home/pi/go/src/github.com/cloudfoundry-incubator/multiapps-cli-plugin
+ BUILD_FOLDER=build
+ PLUGIN_NAME_WIN_32=multiapps-plugin.win32
+ PLUGIN_NAME_WIN_64=multiapps-plugin.win64
+ PLUGIN_NAME_LINUX_32=multiapps-plugin.linux32
+ PLUGIN_NAME_LINUX_64=multiapps-plugin.linux64
+ PLUGIN_NAME_OSX=multiapps-plugin.osx
+ OLD_PLUGIN_NAME_WIN_64=mta_plugin_windows_amd64.exe
+ OLD_PLUGIN_NAME_LINUX_64=mta_plugin_linux_amd64
+ OLD_PLUGIN_NAME_OSX=mta_plugin_darwin_amd64
+ PLUGIN_NAME_STATIC_WIN_32=multiapps-plugin-static.win32
+ PLUGIN_NAME_STATIC_WIN_64=multiapps-plugin-static.win64
+ PLUGIN_NAME_STATIC_LINUX_32=multiapps-plugin-static.linux32
+ PLUGIN_NAME_STATIC_LINUX_64=multiapps-plugin-static.linux64
+ PLUGIN_NAME_STATIC_OSX=multiapps-plugin-static.osx
+ OLD_PLUGIN_NAME_STATIC_WIN_64=mta_plugin_static_windows_amd64.exe
+ OLD_PLUGIN_NAME_STATIC_LINUX_64=mta_plugin_static_linux_amd64
+ OLD_PLUGIN_NAME_STATIC_OSX=mta_plugin_static_darwin_amd64
+ version=2.2.1
+ build 2.2.1 linux arm multiapps-plugin.linux32
+ local version=2.2.1
+ local platform=linux
+ local arch=arm
+ local plugin_name=multiapps-plugin.linux32
+ echo calling to build for linux arm
calling to build for linux arm
+ GOOS=linux
+ GOARCH=arm
+ go build -ldflags '-X main.Version=2.2.1' -o multiapps-plugin.linux32
+ buildstatic 2.2.1 linux arm multiapps-plugin-static.linux32
+ local version=2.2.1
+ local platform=linux
+ local arch=arm
+ local plugin_name=multiapps-plugin-static.linux32
+ echo calling to build static for linux arm
calling to build static for linux arm
+ CGO_ENABLED=0
+ GOOS=linux
+ GOARCH=arm
+ go build -a -tags netgo -ldflags '-w -extldflags "-static" -X main.Version=2.2.1' -o multiapps-plugin-static.linux32
+ mkdir build -p
+ createBuildMetadataFiles 2.2.1 build
+ local version=2.2.1
+ local folder=build
+ echo -n v2.2.1
+ grep -Pzoa '(?s)## v2.2.1(.*?)##' CHANGELOG.md
+ grep -va '##'
+ tr -s '\n' '\n'
+ movePluginsToBuildFolder build
+ local folder=build

```

```
pi@phoscon:~/spring-music/spring-music $ cf apps
Getting apps in org haa / space haa as xxxxxx...
OK

name                                                 requested state   instances   memory   disk   urls
shine-core-js                                        started           1/1         152M     1G     haa-haa-shine-core-js.cfapps.eu10.hana.ondemand.com
myapp                                                stopped           0/1         600M     1G     myapp-busy-baboon.cfapps.eu10.hana.ondemand.com
shine-core-db                                        stopped           0/1         244M     1G
shine-core-db2                                       stopped           0/1         244M     1G
shine-user-js                                        started           1/1         256M     1G     haa-haa-shine-user-js.cfapps.eu10.hana.ondemand.com
shine-web                                            started           1/1         128M     1G     haa-haa-shine-web.cfapps.eu10.hana.ondemand.com
spring-music-news                                    started           1/1         128M     1G     haa-haa-spring-music-news.cfapps.eu10.hana.ondemand.com
spring-music-web                                     started           0/1         1G       1G     haa-haa-spring-music-web.cfapps.eu10.hana.ondemand.com
shine-user-db2                                       stopped           0/1         244M     1G
site-content                                         stopped           0/1         308M     1G
site-web                                             stopped           0/1         256M     1G     haa-haa-site-web.cfapps.eu10.hana.ondemand.com
hdispacedeployc0b35b23-a772-4632-a000-272da94b0abe   stopped           0/1         1G       1G     hdispacedeployc0b35b23-a772-4632-a000-272da94b0abe.cfapps.eu10.hana.ondemand.com
haa-java                                             started           1/1         800M     1G     haa-haa-haa-java.cfapps.eu10.hana.ondemand.com
haa-approuter                                        started           1/1         128M     1G     haa-haa-haa-approuter.cfapps.eu10.hana.ondemand.com
pi@phoscon:~/spring-music/spring-music $ 

```

### installing the multiapps plugin

```
pi@phoscon:~/go/src/github.com/cloudfoundry-incubator/multiapps-cli-plugin/build $ cf install-plugin multiapps-plugin.linux32 -f
Attention: Plugins are binaries written by potentially untrusted authors.
Install and use plugins at your own risk.
Installing plugin multiapps...
OK
Plugin multiapps 2.2.1 successfully installed.
```

## cf deploy

```
pi@phoscon:~ $ pwd
/home/pi
pi@phoscon:~ $ mkdir spring-music
pi@phoscon:~ $ cd spring-music/
pi@phoscon:~/spring-music $ git clone https://github.com/nvvalchev/spring-music.git
Cloning into 'spring-music'...
remote: Enumerating objects: 1144, done.
remote: Total 1144 (delta 0), reused 0 (delta 0), pack-reused 1144
Receiving objects: 100% (1144/1144), 93.85 MiB | 1.20 MiB/s, done.
Resolving deltas: 100% (388/388), done.

pi@phoscon:~/spring-music $ 
pi@phoscon:~/spring-music $ cd spring-music/
pi@phoscon:~/spring-music/spring-music $ cf deploy mta-assembly/spring-music.mtar -e config.mtaext
Deploying multi-target app archive mta-assembly/spring-music.mtar in org haa / space haa as xxxxx...

Uploading 1 files...
  /home/pi/spring-music/spring-music/mta-assembly/spring-music.mtar
OK
Uploading 1 files...
  /home/pi/spring-music/spring-music/config.mtaext
OK
Deploying in org "haa" and space "haa"
Detected MTA schema version: "3"
No deployed MTA detected - this is initial deployment
Detected new MTA version: "1.0.0"
Processing service "spring-music-db"...

```

## ngdbc

```
$ wget --no-check-certificate --no-cookies --header "Cookie: eula_3_1_agreed=tools.hana.ondemand.com/developer-license-3_1.txt; path=/;" -S https://tools.hana.ondemand.com/additional/ngdbc-2.4.70.jar
```

## alien


```
pi@phoscon:~ $ apt-cache show alien
Package: alien
Version: 8.95
Installed-Size: 166
Maintainer: Debian QA Group <packages@qa.debian.org>
Architecture: all
Depends: debhelper (>= 7), perl, rpm (>= 2.4.4-2), dpkg-dev, make, cpio, rpm2cpio
Suggests: patch, bzip2, lintian, lzma
Size: 82272
SHA256: ed32a1120c8af11e96a316fefe9b3430b617c2eff0b6ec7106b0b05410fa7fae
SHA1: e000a605e5783e475cd42127ddb0572ebaab8d8b
MD5sum: 23f799acf4ac90146837ffa07a4f9bf3
Description: convert and install rpm and other packages
 Alien allows you to convert LSB, Red Hat, Stampede and Slackware Packages
 into Debian packages, which can be installed with dpkg.
 .
 It can also generate packages of any of the other formats.
 .
 This is a tool only suitable for binary packages.
Description-md5: 250884c1c7113f08b8c335ac3cf22206
Homepage: http://kitenet.net/~joey/code/alien/
Tag: devel::packaging, implemented-in::perl, interface::commandline,
 role::program, suite::debian, use::converting, works-with-format::tar,
 works-with::archive, works-with::software:package
Section: admin
Priority: optional
Filename: pool/main/a/alien/alien_8.95_all.deb

```



```
pi@phoscon:~ $ sudo apt-get install alien
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libjs-sphinxdoc libjs-underscore python-dbus python-secretstorage
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  autoconf automake autopoint autotools-dev debhelper debugedit dh-autoreconf dh-strip-nondeterminism dwz gettext intltool-debian libarchive-cpio-perl libarchive-zip-perl libfile-stripnondeterminism-perl libltdl-dev
  libmail-sendmail-perl librpm8 librpmbuild8 librpmio8 librpmsign8 libsigsegv2 libsys-hostname-long-perl libtool m4 po-debconf rpm rpm-common rpm2cpio
Suggested packages:
  lintian autoconf-archive gnu-standards autoconf-doc dh-make rpm-i18n gettext-doc libasprintf-dev libgettextpo-dev libtool-doc gfortran | fortran95-compiler gcj-jdk m4-doc libmail-box-perl elfutils rpmlint rpm2html
The following NEW packages will be installed:
  alien autoconf automake autopoint autotools-dev debhelper debugedit dh-autoreconf dh-strip-nondeterminism dwz gettext intltool-debian libarchive-cpio-perl libarchive-zip-perl libfile-stripnondeterminism-perl
  libltdl-dev libmail-sendmail-perl librpm8 librpmbuild8 librpmio8 librpmsign8 libsigsegv2 libsys-hostname-long-perl libtool m4 po-debconf rpm rpm-common rpm2cpio
0 upgraded, 29 newly installed, 0 to remove and 126 not upgraded.
Need to get 16.3 MB of archives.
After this operation, 28.5 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf autotools-dev all 20180224.1 [77.0 kB]
Get:2 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf libsigsegv2 armhf 2.12-2 [32.3 kB]
Get:3 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf m4 armhf 1.4.18-2 [185 kB]
Get:4 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf autoconf all 2.69-11 [341 kB]
Get:5 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf automake all 1:1.16.1-4 [771 kB]
Get:6 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf autopoint all 0.19.8.1-9 [434 kB]
Get:7 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf libtool all 2.4.6-9 [547 kB]
Get:8 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf dh-autoreconf all 19 [16.9 kB]
Get:9 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf libarchive-zip-perl all 1.64-1 [96.8 kB]
Get:10 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf libfile-stripnondeterminism-perl all 1.1.2-1 [19.8 kB]
Get:11 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf dh-strip-nondeterminism all 1.1.2-1 [13.0 kB]       
Get:12 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf dwz armhf 0.12-3 [66.0 kB]
Get:13 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf gettext armhf 0.19.8.1-9 [1,219 kB]
Get:14 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf intltool-debian all 0.35.0+20060710.5 [26.8 kB]
Get:15 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf po-debconf all 1.0.21 [248 kB]
Get:16 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf debhelper all 12.1.1 [1,016 kB]
Get:17 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf librpmio8 armhf 4.14.2.1+dfsg1-1 [1,366 kB]                                                                                                             
Get:18 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf librpm8 armhf 4.14.2.1+dfsg1-1 [1,449 kB]                                                                                                               
Get:19 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf librpmbuild8 armhf 4.14.2.1+dfsg1-1 [1,367 kB]                                                                                                          
Get:20 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf librpmsign8 armhf 4.14.2.1+dfsg1-1 [1,315 kB]                                                                                                           
Get:21 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf rpm-common armhf 4.14.2.1+dfsg1-1 [1,336 kB]                                                                                                            
Get:22 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf rpm2cpio armhf 4.14.2.1+dfsg1-1 [1,316 kB]                                                                                                              
Get:23 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf debugedit armhf 4.14.2.1+dfsg1-1 [1,326 kB]                                                                                                             
Get:24 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf rpm armhf 4.14.2.1+dfsg1-1 [1,425 kB]                                                                                                                   
Get:25 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf alien all 8.95 [82.3 kB]                                                                                                                                
Get:26 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf libarchive-cpio-perl all 0.10-1 [10.3 kB]                                                                                                               
Get:27 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf libltdl-dev armhf 2.4.6-9 [159 kB]                                                                                                                      
Get:28 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf libsys-hostname-long-perl all 1.5-1 [12.0 kB]                                                                                                           
Get:29 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf libmail-sendmail-perl all 0.80-1 [25.3 kB]                                                                                                              
Fetched 16.3 MB in 20s (808 kB/s)                                                                                                                                                                                         
Selecting previously unselected package autotools-dev.
(Reading database ... 145343 files and directories currently installed.)
Preparing to unpack .../00-autotools-dev_20180224.1_all.deb ...
Unpacking autotools-dev (20180224.1) ...
Selecting previously unselected package libsigsegv2:armhf.
Preparing to unpack .../01-libsigsegv2_2.12-2_armhf.deb ...
Unpacking libsigsegv2:armhf (2.12-2) ...
Selecting previously unselected package m4.
Preparing to unpack .../02-m4_1.4.18-2_armhf.deb ...
Unpacking m4 (1.4.18-2) ...
Selecting previously unselected package autoconf.
Preparing to unpack .../03-autoconf_2.69-11_all.deb ...
Unpacking autoconf (2.69-11) ...
Selecting previously unselected package automake.
Preparing to unpack .../04-automake_1%3a1.16.1-4_all.deb ...
Unpacking automake (1:1.16.1-4) ...
Selecting previously unselected package autopoint.
Preparing to unpack .../05-autopoint_0.19.8.1-9_all.deb ...
Unpacking autopoint (0.19.8.1-9) ...
Selecting previously unselected package libtool.
Preparing to unpack .../06-libtool_2.4.6-9_all.deb ...
Unpacking libtool (2.4.6-9) ...
Selecting previously unselected package dh-autoreconf.
Preparing to unpack .../07-dh-autoreconf_19_all.deb ...
Unpacking dh-autoreconf (19) ...
Selecting previously unselected package libarchive-zip-perl.
Preparing to unpack .../08-libarchive-zip-perl_1.64-1_all.deb ...
Unpacking libarchive-zip-perl (1.64-1) ...
Selecting previously unselected package libfile-stripnondeterminism-perl.
Preparing to unpack .../09-libfile-stripnondeterminism-perl_1.1.2-1_all.deb ...
Unpacking libfile-stripnondeterminism-perl (1.1.2-1) ...
Selecting previously unselected package dh-strip-nondeterminism.
Preparing to unpack .../10-dh-strip-nondeterminism_1.1.2-1_all.deb ...
Unpacking dh-strip-nondeterminism (1.1.2-1) ...
Selecting previously unselected package dwz.
Preparing to unpack .../11-dwz_0.12-3_armhf.deb ...
Unpacking dwz (0.12-3) ...
Selecting previously unselected package gettext.
Preparing to unpack .../12-gettext_0.19.8.1-9_armhf.deb ...
Unpacking gettext (0.19.8.1-9) ...
Selecting previously unselected package intltool-debian.
Preparing to unpack .../13-intltool-debian_0.35.0+20060710.5_all.deb ...
Unpacking intltool-debian (0.35.0+20060710.5) ...
Selecting previously unselected package po-debconf.
Preparing to unpack .../14-po-debconf_1.0.21_all.deb ...
Unpacking po-debconf (1.0.21) ...
Selecting previously unselected package debhelper.
Preparing to unpack .../15-debhelper_12.1.1_all.deb ...
Unpacking debhelper (12.1.1) ...
Selecting previously unselected package librpmio8.
Preparing to unpack .../16-librpmio8_4.14.2.1+dfsg1-1_armhf.deb ...
Unpacking librpmio8 (4.14.2.1+dfsg1-1) ...
Selecting previously unselected package librpm8.
Preparing to unpack .../17-librpm8_4.14.2.1+dfsg1-1_armhf.deb ...
Unpacking librpm8 (4.14.2.1+dfsg1-1) ...
Selecting previously unselected package librpmbuild8.
Preparing to unpack .../18-librpmbuild8_4.14.2.1+dfsg1-1_armhf.deb ...
Unpacking librpmbuild8 (4.14.2.1+dfsg1-1) ...
Selecting previously unselected package librpmsign8.
Preparing to unpack .../19-librpmsign8_4.14.2.1+dfsg1-1_armhf.deb ...
Unpacking librpmsign8 (4.14.2.1+dfsg1-1) ...
Selecting previously unselected package rpm-common.
Preparing to unpack .../20-rpm-common_4.14.2.1+dfsg1-1_armhf.deb ...
Unpacking rpm-common (4.14.2.1+dfsg1-1) ...
Selecting previously unselected package rpm2cpio.
Preparing to unpack .../21-rpm2cpio_4.14.2.1+dfsg1-1_armhf.deb ...
Unpacking rpm2cpio (4.14.2.1+dfsg1-1) ...
Selecting previously unselected package debugedit.
Preparing to unpack .../22-debugedit_4.14.2.1+dfsg1-1_armhf.deb ...
Unpacking debugedit (4.14.2.1+dfsg1-1) ...
Selecting previously unselected package rpm.
Preparing to unpack .../23-rpm_4.14.2.1+dfsg1-1_armhf.deb ...
Unpacking rpm (4.14.2.1+dfsg1-1) ...
Selecting previously unselected package alien.
Preparing to unpack .../24-alien_8.95_all.deb ...
Unpacking alien (8.95) ...
Selecting previously unselected package libarchive-cpio-perl.
Preparing to unpack .../25-libarchive-cpio-perl_0.10-1_all.deb ...
Unpacking libarchive-cpio-perl (0.10-1) ...
Selecting previously unselected package libltdl-dev:armhf.
Preparing to unpack .../26-libltdl-dev_2.4.6-9_armhf.deb ...
Unpacking libltdl-dev:armhf (2.4.6-9) ...
Selecting previously unselected package libsys-hostname-long-perl.
Preparing to unpack .../27-libsys-hostname-long-perl_1.5-1_all.deb ...
Unpacking libsys-hostname-long-perl (1.5-1) ...
Selecting previously unselected package libmail-sendmail-perl.
Preparing to unpack .../28-libmail-sendmail-perl_0.80-1_all.deb ...
Unpacking libmail-sendmail-perl (0.80-1) ...
Setting up librpmio8 (4.14.2.1+dfsg1-1) ...
Setting up gettext (0.19.8.1-9) ...
Setting up librpm8 (4.14.2.1+dfsg1-1) ...
Setting up libarchive-zip-perl (1.64-1) ...
Setting up rpm-common (4.14.2.1+dfsg1-1) ...
Setting up intltool-debian (0.35.0+20060710.5) ...
Setting up autotools-dev (20180224.1) ...
Setting up libsigsegv2:armhf (2.12-2) ...
Setting up librpmbuild8 (4.14.2.1+dfsg1-1) ...
Setting up autopoint (0.19.8.1-9) ...
Setting up librpmsign8 (4.14.2.1+dfsg1-1) ...
Setting up dwz (0.12-3) ...
Setting up libarchive-cpio-perl (0.10-1) ...
Setting up debugedit (4.14.2.1+dfsg1-1) ...
Setting up libsys-hostname-long-perl (1.5-1) ...
Setting up libfile-stripnondeterminism-perl (1.1.2-1) ...
Setting up libtool (2.4.6-9) ...
Setting up rpm2cpio (4.14.2.1+dfsg1-1) ...
Setting up po-debconf (1.0.21) ...
Setting up rpm (4.14.2.1+dfsg1-1) ...
Setting up m4 (1.4.18-2) ...
Setting up libmail-sendmail-perl (0.80-1) ...
Setting up autoconf (2.69-11) ...
Setting up automake (1:1.16.1-4) ...
update-alternatives: using /usr/bin/automake-1.16 to provide /usr/bin/automake (automake) in auto mode
Setting up libltdl-dev:armhf (2.4.6-9) ...
Setting up dh-autoreconf (19) ...
Setting up dh-strip-nondeterminism (1.1.2-1) ...
Setting up debhelper (12.1.1) ...
Setting up alien (8.95) ...
Processing triggers for install-info (6.5.0.dfsg.1-4+b1) ...
Processing triggers for libc-bin (2.28-10+rpi1) ...
Processing triggers for man-db (2.8.5-2) ...
pi@phoscon:~ $ alien
You must specify a file to convert.


```

## Install jq on Raspberry Pi

### method
  * a. https://stedolan.github.io/jq/download/
  
```
$ sudo apt-get install jq
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libjs-sphinxdoc libjs-underscore python-dbus python-secretstorage
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libjq1 libonig5
The following NEW packages will be installed:
  jq libjq1 libonig5
0 upgraded, 3 newly installed, 0 to remove and 127 not upgraded.
Need to get 329 kB of archives.
After this operation, 982 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf libonig5 armhf 6.9.1-1 [150 kB]
Get:2 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf libjq1 armhf 1.5+dfsg-2+b1 [119 kB]
Get:3 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf jq armhf 1.5+dfsg-2+b1 [59.3 kB]
Fetched 329 kB in 1s (411 kB/s)
Selecting previously unselected package libonig5:armhf.
(Reading database ... 162266 files and directories currently installed.)
Preparing to unpack .../libonig5_6.9.1-1_armhf.deb ...
Unpacking libonig5:armhf (6.9.1-1) ...
Selecting previously unselected package libjq1:armhf.
Preparing to unpack .../libjq1_1.5+dfsg-2+b1_armhf.deb ...
Unpacking libjq1:armhf (1.5+dfsg-2+b1) ...
Selecting previously unselected package jq.
Preparing to unpack .../jq_1.5+dfsg-2+b1_armhf.deb ...
Unpacking jq (1.5+dfsg-2+b1) ...
Setting up libonig5:armhf (6.9.1-1) ...
Setting up libjq1:armhf (1.5+dfsg-2+b1) ...
Setting up jq (1.5+dfsg-2+b1) ...
Processing triggers for man-db (2.8.5-2) ...
Processing triggers for libc-bin (2.28-10+rpi1) ...
pi@phoscon:~/Downloads $ jq
jq - commandline JSON processor [version 1.5]
Usage: jq [options] <jq filter> [file...]

	jq is a tool for processing JSON inputs, applying the
	given filter to its JSON text inputs and producing the
	filter's results as JSON on standard output.
	The simplest filter is ., which is the identity filter,
	copying jq's input to its output unmodified (except for
	formatting).
	For more advanced filters see the jq(1) manpage ("man jq")
	and/or https://stedolan.github.io/jq

```

  * b. https://www.trevland.org/install-jq-raspberry-pi/

```
wget https://github.com/stedolan/jq/releases/download/jq-1.5/jq-1.5.tar.gz
tar xfvz jq-1.5.tar.gz
cd jq-1.5
./configure && make && sudo make install
```


```
pi@phoscon:~ $ cd Downloads/
pi@phoscon:~/Downloads $ wget https://github.com/stedolan/jq/releases/download/jq-1.5/jq-1.5.tar.gz
--2020-02-20 13:34:24--  https://github.com/stedolan/jq/releases/download/jq-1.5/jq-1.5.tar.gz
Resolving github.com (github.com)... 140.82.118.4
Connecting to github.com (github.com)|140.82.118.4|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://github-production-release-asset-2e65be.s3.amazonaws.com/5101141/f8d0df1e-439f-11e5-980c-9c1e050ee63f?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20200220%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20200220T133424Z&X-Amz-Expires=300&X-Amz-Signature=719ab802f8a2a636045df9a25ccf78a5d747c1fc490faf5f303aa7706b9d7f61&X-Amz-SignedHeaders=host&actor_id=0&response-content-disposition=attachment%3B%20filename%3Djq-1.5.tar.gz&response-content-type=application%2Foctet-stream [following]
--2020-02-20 13:34:24--  https://github-production-release-asset-2e65be.s3.amazonaws.com/5101141/f8d0df1e-439f-11e5-980c-9c1e050ee63f?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20200220%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20200220T133424Z&X-Amz-Expires=300&X-Amz-Signature=719ab802f8a2a636045df9a25ccf78a5d747c1fc490faf5f303aa7706b9d7f61&X-Amz-SignedHeaders=host&actor_id=0&response-content-disposition=attachment%3B%20filename%3Djq-1.5.tar.gz&response-content-type=application%2Foctet-stream
Resolving github-production-release-asset-2e65be.s3.amazonaws.com (github-production-release-asset-2e65be.s3.amazonaws.com)... 52.216.96.195
Connecting to github-production-release-asset-2e65be.s3.amazonaws.com (github-production-release-asset-2e65be.s3.amazonaws.com)|52.216.96.195|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 739309 (722K) [application/octet-stream]
Saving to: ‘jq-1.5.tar.gz’

jq-1.5.tar.gz                                          100%[===========================================================================================================================>] 721.98K   664KB/s    in 1.1s    

2020-02-20 13:34:26 (664 KB/s) - ‘jq-1.5.tar.gz’ saved [739309/739309]

pi@phoscon:~/Downloads $ tar xfvz jq-1.5.tar.gz
jq-1.5/

pi@phoscon:~/Downloads/jq-1.5 $ ./configure && make && sudo make install

 /usr/bin/mkdir -p '/usr/local/lib'
 /bin/bash ./libtool   --mode=install /usr/bin/install -c   libjq.la '/usr/local/lib'
libtool: install: /usr/bin/install -c .libs/libjq.so.1.0.4 /usr/local/lib/libjq.so.1.0.4
libtool: install: (cd /usr/local/lib && { ln -s -f libjq.so.1.0.4 libjq.so.1 || { rm -f libjq.so.1 && ln -s libjq.so.1.0.4 libjq.so.1; }; })
libtool: install: (cd /usr/local/lib && { ln -s -f libjq.so.1.0.4 libjq.so || { rm -f libjq.so && ln -s libjq.so.1.0.4 libjq.so; }; })
libtool: install: /usr/bin/install -c .libs/libjq.lai /usr/local/lib/libjq.la
libtool: install: /usr/bin/install -c .libs/libjq.a /usr/local/lib/libjq.a
libtool: install: chmod 644 /usr/local/lib/libjq.a
libtool: install: ranlib /usr/local/lib/libjq.a
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/sbin" ldconfig -n /usr/local/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
 /usr/bin/mkdir -p '/usr/local/bin'
  /bin/bash ./libtool   --mode=install /usr/bin/install -c jq '/usr/local/bin'
libtool: install: /usr/bin/install -c jq /usr/local/bin/jq
 /usr/bin/mkdir -p '/usr/local/share/doc/jq'
 /usr/bin/install -c -m 644 README.md COPYING AUTHORS README '/usr/local/share/doc/jq'
 /usr/bin/mkdir -p '/usr/local/include'
 /usr/bin/install -c -m 644 jv.h jq.h '/usr/local/include'
 /usr/bin/mkdir -p '/usr/local/share/man/man1'
 /usr/bin/install -c -m 644 jq.1 '/usr/local/share/man/man1'
make[2]: Leaving directory '/home/pi/Downloads/jq-1.5'
make[1]: Leaving directory '/home/pi/Downloads/jq-1.5'
pi@phoscon:~/Downloads/jq-1.5 $ jq
jq - commandline JSON processor [version 1.5]
Usage: jq [options] <jq filter> [file...]

	jq is a tool for processing JSON inputs, applying the
	given filter to its JSON text inputs and producing the
	filter's results as JSON on standard output.
	The simplest filter is ., which is the identity filter,
	copying jq's input to its output unmodified (except for
	formatting).
	For more advanced filters see the jq(1) manpage ("man jq")
	and/or https://stedolan.github.io/jq

.........................


```


## maven

`sudo apt-get install maven`

http://maven.apache.org/install.html


```
$ sudo apt-get install maven
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libjs-sphinxdoc libjs-underscore python-dbus python-secretstorage
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libaopalliance-java libapache-pom-java libatinject-jsr330-api-java libcdi-api-java libcommons-cli-java libcommons-io-java libcommons-lang3-java libcommons-parent-java libgeronimo-annotation-1.3-spec-java
  libgeronimo-interceptor-3.0-spec-java libguava-java libguice-java libhawtjni-runtime-java libjansi-java libjansi-native-java libjsr305-java libmaven-parent-java libmaven-resolver-java libmaven-shared-utils-java
  libmaven3-core-java libplexus-cipher-java libplexus-classworlds-java libplexus-component-annotations-java libplexus-interpolation-java libplexus-sec-dispatcher-java libplexus-utils2-java libsisu-inject-java
  libsisu-plexus-java libslf4j-java libwagon-file-java libwagon-http-shaded-java libwagon-provider-api-java
Suggested packages:
  libaopalliance-java-doc libatinject-jsr330-api-java-doc libservlet3.1-java libcommons-io-java-doc libcommons-lang3-java-doc libasm-java libcglib-java libjsr305-java-doc libmaven-shared-utils-java-doc liblogback-java
  libplexus-cipher-java-doc libplexus-classworlds-java-doc libplexus-interpolation-java-doc libplexus-sec-dispatcher-java-doc libplexus-utils2-java-doc junit4 testng libcommons-logging-java liblog4j1.2-java
The following NEW packages will be installed:
  libaopalliance-java libapache-pom-java libatinject-jsr330-api-java libcdi-api-java libcommons-cli-java libcommons-io-java libcommons-lang3-java libcommons-parent-java libgeronimo-annotation-1.3-spec-java
  libgeronimo-interceptor-3.0-spec-java libguava-java libguice-java libhawtjni-runtime-java libjansi-java libjansi-native-java libjsr305-java libmaven-parent-java libmaven-resolver-java libmaven-shared-utils-java
  libmaven3-core-java libplexus-cipher-java libplexus-classworlds-java libplexus-component-annotations-java libplexus-interpolation-java libplexus-sec-dispatcher-java libplexus-utils2-java libsisu-inject-java
  libsisu-plexus-java libslf4j-java libwagon-file-java libwagon-http-shaded-java libwagon-provider-api-java maven
0 upgraded, 33 newly installed, 0 to remove and 127 not upgraded.
Need to get 9,165 kB of archives.
After this operation, 12.0 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf libaopalliance-java all 20070526-6 [9,048 B]
Get:2 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf libapache-pom-java all 18-1 [4,676 B]
Get:3 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf libatinject-jsr330-api-java all 1.0+ds1-5 [5,312 B]
Get:4 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf libgeronimo-interceptor-3.0-spec-java all 1.0.1-4 [8,484 B]
Get:5 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf libcdi-api-java all 1.2-2 [54.5 kB]                
Get:6 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf libcommons-cli-java all 1.4-1 [55.2 kB]
Get:7 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf libcommons-parent-java all 43-1 [10.8 kB]
Get:8 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf libcommons-io-java all 2.6-2 [213 kB]
Get:9 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf libcommons-lang3-java all 3.8-2 [478 kB]
Get:10 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf libgeronimo-annotation-1.3-spec-java all 1.0-1 [10.6 kB]
Get:11 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf libjsr305-java all 0.1~+svn49-11 [26.9 kB]
Get:12 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf libguava-java all 19.0-1 [2,028 kB]
Get:13 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf libguice-java all 4.2.1-1 [962 kB]                                                                                                                      
Get:14 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf libhawtjni-runtime-java all 1.16-1 [29.9 kB]                                                                                                            
Get:15 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf libjansi-native-java all 1.8-1 [26.0 kB]                                                                                                                
Get:16 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf libjansi-java all 1.17.1-1 [63.8 kB]                                                                                                                    
Get:17 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf libmaven-parent-java all 31-2 [5,100 B]                                                                                                                 
Get:18 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf libplexus-utils2-java all 3.1.1-1 [249 kB]                                                                                                              
Get:19 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf libwagon-provider-api-java all 3.3.1-2 [50.1 kB]                                                                                                        
Get:20 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf libmaven-resolver-java all 1.3.1-1 [549 kB]                                                                                                             
Get:21 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf libmaven-shared-utils-java all 3.3.0-1 [149 kB]                                                                                                         
Get:22 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf libplexus-cipher-java all 1.7-3 [15.0 kB]                                                                                                               
Get:23 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf libplexus-classworlds-java all 2.6.0-1 [49.4 kB]                                                                                                        
Get:24 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf libplexus-component-annotations-java all 1.7.1-7 [7,536 B]                                                                                              
Get:25 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf libplexus-interpolation-java all 1.25-1 [76.8 kB]                                                                                                       
Get:26 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf libplexus-sec-dispatcher-java all 1.4-4 [28.1 kB]                                                                                                       
Get:27 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf libslf4j-java all 1.7.25-3 [143 kB]                                                                                                                     
Get:28 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf libsisu-inject-java all 0.3.3-1 [347 kB]                                                                                                                
Get:29 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf libsisu-plexus-java all 0.3.3-3 [182 kB]                                                                                                                
Get:30 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf libmaven3-core-java all 3.6.0-1 [1,465 kB]                                                                                                              
Get:31 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf libwagon-file-java all 3.3.1-2 [10.7 kB]                                                                                                                
Get:32 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf libwagon-http-shaded-java all 3.3.1-2 [1,829 kB]                                                                                                        
Get:33 http://mirror.chaoticum.net/rpi/raspbian buster/main armhf maven all 3.6.0-1 [22.1 kB]                                                                                                                             
Fetched 9,165 kB in 13s (718 kB/s)                                                                                                                                                                                        
Extracting templates from packages: 100%
Selecting previously unselected package libaopalliance-java.
(Reading database ... 162288 files and directories currently installed.)
Preparing to unpack .../00-libaopalliance-java_20070526-6_all.deb ...
Unpacking libaopalliance-java (20070526-6) ...
Selecting previously unselected package libapache-pom-java.
Preparing to unpack .../01-libapache-pom-java_18-1_all.deb ...
Unpacking libapache-pom-java (18-1) ...
Selecting previously unselected package libatinject-jsr330-api-java.
Preparing to unpack .../02-libatinject-jsr330-api-java_1.0+ds1-5_all.deb ...
Unpacking libatinject-jsr330-api-java (1.0+ds1-5) ...
Selecting previously unselected package libgeronimo-interceptor-3.0-spec-java.
Preparing to unpack .../03-libgeronimo-interceptor-3.0-spec-java_1.0.1-4_all.deb ...
Unpacking libgeronimo-interceptor-3.0-spec-java (1.0.1-4) ...
Selecting previously unselected package libcdi-api-java.
Preparing to unpack .../04-libcdi-api-java_1.2-2_all.deb ...
Unpacking libcdi-api-java (1.2-2) ...
Selecting previously unselected package libcommons-cli-java.
Preparing to unpack .../05-libcommons-cli-java_1.4-1_all.deb ...
Unpacking libcommons-cli-java (1.4-1) ...
Selecting previously unselected package libcommons-parent-java.
Preparing to unpack .../06-libcommons-parent-java_43-1_all.deb ...
Unpacking libcommons-parent-java (43-1) ...
Selecting previously unselected package libcommons-io-java.
Preparing to unpack .../07-libcommons-io-java_2.6-2_all.deb ...
Unpacking libcommons-io-java (2.6-2) ...
Selecting previously unselected package libcommons-lang3-java.
Preparing to unpack .../08-libcommons-lang3-java_3.8-2_all.deb ...
Unpacking libcommons-lang3-java (3.8-2) ...
Selecting previously unselected package libgeronimo-annotation-1.3-spec-java.
Preparing to unpack .../09-libgeronimo-annotation-1.3-spec-java_1.0-1_all.deb ...
Unpacking libgeronimo-annotation-1.3-spec-java (1.0-1) ...
Selecting previously unselected package libjsr305-java.
Preparing to unpack .../10-libjsr305-java_0.1~+svn49-11_all.deb ...
Unpacking libjsr305-java (0.1~+svn49-11) ...
Selecting previously unselected package libguava-java.
Preparing to unpack .../11-libguava-java_19.0-1_all.deb ...
Unpacking libguava-java (19.0-1) ...
Selecting previously unselected package libguice-java.
Preparing to unpack .../12-libguice-java_4.2.1-1_all.deb ...
Unpacking libguice-java (4.2.1-1) ...
Selecting previously unselected package libhawtjni-runtime-java.
Preparing to unpack .../13-libhawtjni-runtime-java_1.16-1_all.deb ...
Unpacking libhawtjni-runtime-java (1.16-1) ...
Selecting previously unselected package libjansi-native-java.
Preparing to unpack .../14-libjansi-native-java_1.8-1_all.deb ...
Unpacking libjansi-native-java (1.8-1) ...
Selecting previously unselected package libjansi-java.
Preparing to unpack .../15-libjansi-java_1.17.1-1_all.deb ...
Unpacking libjansi-java (1.17.1-1) ...
Selecting previously unselected package libmaven-parent-java.
Preparing to unpack .../16-libmaven-parent-java_31-2_all.deb ...
Unpacking libmaven-parent-java (31-2) ...
Selecting previously unselected package libplexus-utils2-java.
Preparing to unpack .../17-libplexus-utils2-java_3.1.1-1_all.deb ...
Unpacking libplexus-utils2-java (3.1.1-1) ...
Selecting previously unselected package libwagon-provider-api-java.
Preparing to unpack .../18-libwagon-provider-api-java_3.3.1-2_all.deb ...
Unpacking libwagon-provider-api-java (3.3.1-2) ...
Selecting previously unselected package libmaven-resolver-java.
Preparing to unpack .../19-libmaven-resolver-java_1.3.1-1_all.deb ...
Unpacking libmaven-resolver-java (1.3.1-1) ...
Selecting previously unselected package libmaven-shared-utils-java.
Preparing to unpack .../20-libmaven-shared-utils-java_3.3.0-1_all.deb ...
Unpacking libmaven-shared-utils-java (3.3.0-1) ...
Selecting previously unselected package libplexus-cipher-java.
Preparing to unpack .../21-libplexus-cipher-java_1.7-3_all.deb ...
Unpacking libplexus-cipher-java (1.7-3) ...
Selecting previously unselected package libplexus-classworlds-java.
Preparing to unpack .../22-libplexus-classworlds-java_2.6.0-1_all.deb ...
Unpacking libplexus-classworlds-java (2.6.0-1) ...
Selecting previously unselected package libplexus-component-annotations-java.
Preparing to unpack .../23-libplexus-component-annotations-java_1.7.1-7_all.deb ...
Unpacking libplexus-component-annotations-java (1.7.1-7) ...
Selecting previously unselected package libplexus-interpolation-java.
Preparing to unpack .../24-libplexus-interpolation-java_1.25-1_all.deb ...
Unpacking libplexus-interpolation-java (1.25-1) ...
Selecting previously unselected package libplexus-sec-dispatcher-java.
Preparing to unpack .../25-libplexus-sec-dispatcher-java_1.4-4_all.deb ...
Unpacking libplexus-sec-dispatcher-java (1.4-4) ...
Selecting previously unselected package libslf4j-java.
Preparing to unpack .../26-libslf4j-java_1.7.25-3_all.deb ...
Unpacking libslf4j-java (1.7.25-3) ...
Selecting previously unselected package libsisu-inject-java.
Preparing to unpack .../27-libsisu-inject-java_0.3.3-1_all.deb ...
Unpacking libsisu-inject-java (0.3.3-1) ...
Selecting previously unselected package libsisu-plexus-java.
Preparing to unpack .../28-libsisu-plexus-java_0.3.3-3_all.deb ...
Unpacking libsisu-plexus-java (0.3.3-3) ...
Selecting previously unselected package libmaven3-core-java.
Preparing to unpack .../29-libmaven3-core-java_3.6.0-1_all.deb ...
Unpacking libmaven3-core-java (3.6.0-1) ...
Selecting previously unselected package libwagon-file-java.
Preparing to unpack .../30-libwagon-file-java_3.3.1-2_all.deb ...
Unpacking libwagon-file-java (3.3.1-2) ...
Selecting previously unselected package libwagon-http-shaded-java.
Preparing to unpack .../31-libwagon-http-shaded-java_3.3.1-2_all.deb ...
Unpacking libwagon-http-shaded-java (3.3.1-2) ...
Selecting previously unselected package maven.
Preparing to unpack .../32-maven_3.6.0-1_all.deb ...
Unpacking maven (3.6.0-1) ...
Setting up libslf4j-java (1.7.25-3) ...
Setting up libplexus-utils2-java (3.1.1-1) ...
Setting up libplexus-classworlds-java (2.6.0-1) ...
Setting up libjsr305-java (0.1~+svn49-11) ...
Setting up libaopalliance-java (20070526-6) ...
Setting up libcommons-cli-java (1.4-1) ...
Setting up libplexus-component-annotations-java (1.7.1-7) ...
Setting up libplexus-cipher-java (1.7-3) ...
Setting up libgeronimo-annotation-1.3-spec-java (1.0-1) ...
Setting up libgeronimo-interceptor-3.0-spec-java (1.0.1-4) ...
Setting up libapache-pom-java (18-1) ...
Setting up libatinject-jsr330-api-java (1.0+ds1-5) ...
Setting up libplexus-interpolation-java (1.25-1) ...
Setting up libplexus-sec-dispatcher-java (1.4-4) ...
Setting up libwagon-http-shaded-java (3.3.1-2) ...
Setting up libcdi-api-java (1.2-2) ...
Setting up libhawtjni-runtime-java (1.16-1) ...
Setting up libwagon-provider-api-java (3.3.1-2) ...
Setting up libmaven-parent-java (31-2) ...
Setting up libcommons-parent-java (43-1) ...
Setting up libmaven-resolver-java (1.3.1-1) ...
Setting up libguava-java (19.0-1) ...
Setting up libcommons-lang3-java (3.8-2) ...
Setting up libjansi-native-java (1.8-1) ...
Setting up libwagon-file-java (3.3.1-2) ...
Setting up libcommons-io-java (2.6-2) ...
Setting up libguice-java (4.2.1-1) ...
Setting up libjansi-java (1.17.1-1) ...
Setting up libmaven-shared-utils-java (3.3.0-1) ...
Setting up libsisu-inject-java (0.3.3-1) ...
Setting up libsisu-plexus-java (0.3.3-3) ...
Setting up libmaven3-core-java (3.6.0-1) ...
Setting up maven (3.6.0-1) ...
update-alternatives: using /usr/share/maven/bin/mvn to provide /usr/bin/mvn (mvn) in auto mode
```

test your maven installation

```
pi@phoscon:~/Downloads $ mvn -v
Apache Maven 3.6.0
Maven home: /usr/share/maven
Java version: 1.8.0_212, vendor: Oracle Corporation, runtime: /usr/lib/jvm/java-8-openjdk-armhf/jre
Default locale: en_GB, platform encoding: UTF-8
OS name: "linux", version: "4.19.75-v7l+", arch: "arm", family: "unix"
pi@phoscon:~/Downloads $ 

```
