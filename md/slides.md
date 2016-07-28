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

  * LXC
  * cgroups


## Docker

  * provide process-isolation
  * possibility to allocate resources


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


## flatpak


## flatpak

  * desktop session


## flatpak

  * runtime


## flatpak

  * runtime
  * application libraries


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
