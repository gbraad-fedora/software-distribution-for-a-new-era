# Software distribution for a new era

### Software distribution for a new era
Gerard Braad

me@gbraad.nl


## software distribution


## Problem space

  * Software packages


## Windows

  * executable
  * installer


## Problem space

  * Software packages
    * who creates them?


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
  * yellow package
  * .app (dmg)


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


## How to solve

  * static compilation


## Solutions

  * static compile


## Solutions

  * or ...


## Solutions

  * AppImage
  * snapcraft
  * flatpak
  * containers


## Containers

... as the 'Delivery Unit'


## What is a 'container'


## Docker


## Docker

  * cgroups
  * namespaces


## Docker

  * possibility to allocate resources
  * provide process-isolation


## Containers

  * provide process-isolation
  * possibility to allocate resources


## Example

  * alias 'youtube-dl'


## Process isolation

  * protect each process from other processes on the operating system


## Process isolation

  * preventing process X from writing to process Y


## Process isolation

  * limited (controlled) interaction between processes allowed over inter-process communication


## Sandboxing

  * a security mechanism for separating running programs
  * limit view of the operating system


## flatpak

  * safe environment for running applications


## flatpak

  * sandboxing
    * cgroups
    * namespaces


## flatpak

  * runtime


## flatpak

  * runtime
  * application libraries


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


## flatpak

  * desktop session


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
