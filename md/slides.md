# Software distribution for a new era

### Software distribution for a new era
Gerard Braad

me@gbraad.nl


## Software distribution



## Windows

  * executable


## Windows

  * executable
  * installer


## Linux



## Problem space

  * Software packages


## Problem space

  * Software packages
    * who creates them?


## dependency hell



## dependency hell

  * .dll
  * Visual Basic runtime
  * Visual C++ runtime


## dependency hell

  * .NET
  * gac (global assembly cache)
  * local libraries


## Mac OS

  * executable
  * yellow package (.pkg)
  * [name].app (dmg)


## structure

```
/
 Applications/
   Calculator.app/
     MacOS/
       Calculator
     Resources/
       ...
```


## dependency hell

  * (g)libc
  * GTK


## Solutions



## Solutions

  * static compilation


## Solutions

  * or ...


## Solutions

  * containers


## Solutions

  * containers
  * ...


## Containers



## Containers

... as the 'Delivery Unit'



## Docker



## Example



## Example

  * youtube-dl


## Example

  * youtube-dl
  * CentOS 7


## alias

```
$ cat ./.zshrc.d/alias.sh
```

    alias stack='docker run -it --rm -v ~/.stack:/root/.stack registry.gitlab.com/gbraad/openstack-client:centos stack'
    alias openstack='docker run -it --rm -v ~/.config/openstack:/root/.config/openstack registry.gitlab.com/gbraad/openstack-client:centos openstack'
    alias youtube-dl='docker run --rm -u $(id -u):$(id -g) -v $PWD:/data vimagick/youtube-dl'


## invoke

```
$ youtube-dl https://youtu.be/SquTeFYq3K8
```


## invoke

```
$ youtube-dl https://youtu.be/SquTeFYq3K8
```

    Unable to find image 'vimagick/youtube-dl:latest' locally
    latest: Pulling from vimagick/youtube-dl
    e110a4a17941: Already exists 
    a0733e3a9603: Pull complete 
    eaf92aad0831: Pull complete 
    Digest: sha256:24a24cbddbfc695f210bbf21769c60eea9626cf90fad4f3f9b41279a0bfd22e7
    Status: Downloaded newer image for vimagick/youtube-dl:latest


## invoke

```
$ youtube-dl https://youtu.be/SquTeFYq3K8
```

    Unable to find image 'vimagick/youtube-dl:latest' locally
    latest: Pulling from vimagick/youtube-dl
    e110a4a17941: Already exists 
    a0733e3a9603: Pull complete 
    eaf92aad0831: Pull complete 
    Digest: sha256:24a24cbddbfc695f210bbf21769c60eea9626cf90fad4f3f9b41279a0bfd22e7
    Status: Downloaded newer image for vimagick/youtube-dl:latest
    [youtube] SquTeFYq3K8: Downloading webpage
    [youtube] SquTeFYq3K8: Downloading video info webpage
    [youtube] SquTeFYq3K8: Extracting video information
    [youtube] SquTeFYq3K8: Downloading MPD manifest
    [download] Destination: Tomorrowland 2015 _ Josh Wink-SquTeFYq3K8.f248.webm
    [download] 100% of 2.07GiB in 01:3112MiB/s ETA 00:008:27
    [download] Destination: Tomorrowland 2015 _ Josh Wink-SquTeFYq3K8.f251.webm
    [download] 100% of 90.05MiB in 00:0526MiB/s ETA 00:00505
    [ffmpeg] Merging formats into "Tomorrowland 2015 _ Josh Wink-SquTeFYq3K8.webm"
    Deleting original file Tomorrowland 2015 _ Josh Wink-SquTeFYq3K8.f248.webm (pass -k to keep)
    Deleting original file Tomorrowland 2015 _ Josh Wink-SquTeFYq3K8.f251.webm (pass -k to keep)


## OpenStack client

```
$ openstack --os-cloud dream server list
```

    +--------------------------------------+-------+--------+--------------------------------------------------------------+
    | ID                                   | Name  | Status | Networks                                                     |
    +--------------------------------------+-------+--------+--------------------------------------------------------------+
    | bbeda46a-080d-4941-846a-86170ccc60bf | vps13 | ACTIVE | public=2607:f298:5:101d:f816:3eff:fe9e:53a1, 208.113.133.113 |
    +--------------------------------------+-------+--------+--------------------------------------------------------------+


## What just happened?



## Docker

  * cgroups
  * namespaces


## Docker

  * possibility to allocate resources
  * provide process-isolation


## What is a 'container'



## Containers

  * possibility to allocate resources
  * provide process-isolation


## Process isolation

  * protect each process from other processes on the operating system


## Process isolation

  * preventing process X from writing to process Y


## Process isolation

  * limited (controlled) interaction between processes allowed over inter-process communication


## Sandboxing

  * a security mechanism for separating running programs
  * limit view of the operating system


## Solutions

  * containers
  * ...


## Solutions

  * containers
  * AppImage
  * snapcraft
  * flatpak


## flatpak

  * safe environment for running applications


## flatpak

  * sandboxing
    * cgroups
    * namespaces


## flatpak

```
$ dnf install -y flatpak
```


## Add remotes

```
$ wget https://sdk.gnome.org/keys/gnome-sdk.gpg
$ flatpak remote-add --gpg-import=gnome-sdk.gpg gnome https://sdk.gnome.org/repo/
$ flatpak remote-add --gpg-import=gnome-sdk.gpg gnome-apps https://sdk.gnome.org/repo-apps/
```


## flatpak

  * runtime


## flatpak

  * runtime
  * application


## Install runtime

```
$ flatpak install gnome org.gnome.Platform 3.20
```

    9 delta parts, 71 loose fetched; 167139 KiB transferred in 130 seconds                                   
    Installing related: org.gnome.Platform.Locale
    
    2 metadata, 0 content objects fetched; 13 KiB transferred in 2 seconds                                   


## Install application

```
$ flatpak install gnome-apps org.gnome.gedit stable
```

    1 delta parts, 1 loose fetched; 1725 KiB transferred in 11 seconds                                       
    Installing related: org.gnome.gedit.Locale
    
    2 metadata, 0 content objects fetched; 6 KiB transferred in 4 seconds               


## Run application

```
$ flatpak run org.gnome.gedit
```

    ** (gedit:2): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-ZoHXu4deCC: Connection refused
    Gtk-Message: Failed to load module "pk-gtk-module"
    Gtk-Message: Failed to load module "pk-gtk-module"
    
    (gedit:2): Gtk-WARNING **: Could not load a pixbuf from icon theme.
    This may indicate that pixbuf loaders or the mime database could not be found.


## LibreOffice

```
$ wget http://download.documentfoundation.org/libreoffice/flatpak/latest/LibreOffice.flatpak
$ flatpak install --user --bundle LibreOffice.flatpak    
$ flatpak run org.libreoffice.LibreOffice
```


## Anatomy

```
metadata
/files
/files/bin
/export
```


## Anatomy

```
[Application]
name=org.gnome.gedit
runtime=org.gnome.Platform/x86_64/3.20
sdk=org.gnome.Sdk/x86_64/3.20
command=gedit
```


## Install SDK

```
$ flatpak install gnome org.gnome.Sdk 3.20
```

    Receiving delta parts: 17/17 721.6 kB/s 33.2 MB/184.0 MB 3 minutes 28 seconds remaining                                                                                                                                                       Receiving delta parts: 17/17 708.0 kB/s 33.3 MB/184.0 MB 3 minutes 32 seconds remaining                                                                                                                                                       17 delta parts, 16 loose fetched; 33118 KiB transferred in 55 seconds                                                                                                                                                                         
    Installing related: org.gnome.Sdk.Locale
    
    2 metadata, 0 content objects fetched; 13 KiB transferred in 2 seconds


## Enter the sandbox

```
$ flatpak run --devel --command=bash org.gnome.gedit
```

    bash-4.3$


## Home

```
bash-4.3$ ls -al
```

    total 172
    drwx------ 22 gbraad    gbraad     4096 Jul 28 13:36 .
    drwxr-xr-x  3 nfsnobody nfsnobody  4096 Jul 28  2016 ..
    drwx------  3 gbraad    gbraad     4096 Jul 28 11:44 .ansible
    -rw-------  1 gbraad    gbraad     1301 Jul 28 11:54 .bash_history
    -rw-r--r--  1 gbraad    gbraad       18 May 17 22:22 .bash_logout
    -rw-r--r--  1 gbraad    gbraad      193 May 17 22:22 .bash_profile
    -rw-r--r--  1 gbraad    gbraad      231 May 17 22:22 .bashrc
    drwx------ 16 gbraad    gbraad     4096 Jul 28 11:26 .cache
    drwxr-xr-x 18 gbraad    gbraad     4096 Jul 28 13:36 .config
    drwxr-xr-x  2 gbraad    gbraad     4096 Jul 28 13:36 Desktop
    drwxr-xr-x  2 gbraad    gbraad     4096 Jul 28 10:38 Documents
    [...]


## Root

```
bash-4.3$ ls -al /
```

    total 44
    drwxr-xr-x  17 gbraad    gbraad      420 Jul 28 13:37 .
    drwxr-xr-x  17 gbraad    gbraad      420 Jul 28 13:37 ..
    drwxrwxr-x   6 nfsnobody nfsnobody  4096 Jul 28 11:07 app
    lrwxrwxrwx   1 gbraad    gbraad        7 Jul 28 13:37 bin -> usr/bin
    drwxr-xr-x   4 gbraad    gbraad      300 Jul 28 13:37 dev
    drwxr-xr-x  24 gbraad    gbraad     1140 Jul 28 13:37 etc
    drwxr-xr-x   3 nfsnobody nfsnobody  4096 Jul 28  2016 home
    lrwxrwxrwx   1 gbraad    gbraad        7 Jul 28 13:37 lib -> usr/lib
    lrwxrwxrwx   1 gbraad    gbraad        9 Jul 28 13:37 lib64 -> usr/lib64
    drwx------   2 nfsnobody nfsnobody 16384 Jun 15 00:25 lost+found
    drwxr-xr-x   2 nfsnobody nfsnobody  4096 Feb  4 06:10 media
    drwxr-xr-x   2 nfsnobody nfsnobody  4096 Feb  4 06:10 mnt
    drwxr-xr-x   2 nfsnobody nfsnobody  4096 Feb  4 06:10 opt
    dr-xr-xr-x 243 nfsnobody nfsnobody     0 Jul 28 13:37 proc
    drwxr-xr-x   6 gbraad    gbraad      160 Jul 28 13:37 run
    lrwxrwxrwx   1 gbraad    gbraad        8 Jul 28 13:37 sbin -> usr/sbin
    drwxr-xr-x   2 nfsnobody nfsnobody  4096 Feb  4 06:10 srv
    drwxr-xr-x   7 gbraad    gbraad      140 Jul 28 13:37 sys
    drwxr-xr-x   3 gbraad    gbraad       60 Jul 28 13:37 tmp
    drwxrwxr-x  14 nfsnobody nfsnobody  4096 Jul 28 13:36 usr
    drwxr-xr-x   6 gbraad    gbraad      140 Jul 28 13:37 var


## App

```
bash-4.3$ ls -al /app
```

    total 28
    drwxrwxr-x  6 nfsnobody nfsnobody 4096 Jul 28 11:07 .
    drwxr-xr-x 17 gbraad    gbraad     420 Jul 28 13:37 ..
    drwxrwxr-x  2 nfsnobody nfsnobody 4096 Jan  1  1970 bin
    drwxrwxr-x  7 nfsnobody nfsnobody 4096 Jan  1  1970 lib
    drwxrwxr-x  3 nfsnobody nfsnobody 4096 Jan  1  1970 libexec
    -rwxrw-r--  2 nfsnobody nfsnobody 2223 Jan  1  1970 manifest.json
    -rw-r--r--  1 nfsnobody nfsnobody    0 Jul 28 11:07 .ref
    drwxrwxr-x 15 nfsnobody nfsnobody 4096 Jan  1  1970 share


## Libraries

```
bash-4.3$ ls -al /usr/lib/ |wc -l
```

    1287

```
bash-4.3$ exit
exit
[gbraad@yoga ~]$ ls -al /usr/lib/ |wc -l
```

    406


## flatpak

  * runtime
  * application


## flatpak

  * /usr
  * /app


## flatpak for server?

  * desktop session


## flatpak for server?

  * we already have Docker?


## flatpak for server?

  * we already have runc?


## ostree

  * "git-like" model for committing and downloading bootable filesystem trees
  * checksums individual files
  * content-addressed-object store


## ostree

  * unlike git in that it "checks out" the files via hardlinks => immutable
  * Linux VServer hardlinks


## ostree

  * rpm-ostree
  * flatpak
  * project atomic


## Project Atomic


