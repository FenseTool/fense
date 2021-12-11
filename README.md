# fense
**A tool for incremental symbolic execution**



# Using FENSE with Docker



## Quick Start

Assuming you have Docker installed, you can run the following to try the latest release of FENSE:

```docker
$ docker pull fensetools/fense:latest
$ docker run --rm -ti fensetools/fense:latest
```



## Installing Docker

Follow these links for installation instructions on [Ubuntu](https://docs.docker.com/engine/install/ubuntu/), [OS X](https://docs.docker.com/installation/mac/) and [Windows](https://docs.docker.com/installation/windows/).



## Creating a FENSE Docker container

If this worked correctly your shell prompt will have changed, and you will be the `root` user, and you can switch to `fense` user , the password of `fense` user is `fense` too

```docker
root@7206f7f2ddbd:~$ su fense
fense@7206f7f2ddbd:~$: whoami
fense
```

You can now try running fense inside the container, by the way our image is based on ubuntu14.04. The version of klee is 1.4.0 and the version of llvm and clang is 3.4.0. If this worked correctly you should see an output similar to:

```
fense@7206f7f2ddbd:~$ klee --version
KLEE 1.4.0.0 (https://klee.github.io)
  Build mode: RelWithDebInfo (Asserts: ON)
  Build revision: 9fb2f5666d5f8c7c2f335fc8408883a0cf958964

LLVM (http://llvm.org/):
  LLVM version 3.4
  Optimized build with assertions.
  Built Dec  9 2021 (13:21:29).
  Default target: x86_64-unknown-linux-gnu
  Host CPU: x86-64
```

and Clang

``` 
$ clang --version
clang version 3.4 (tags/RELEASE_34/final)
Target: x86_64-unknown-linux-gnu
Thread model: posix
```

Now exit the container

```
fense@3c098b05ca85:~$ exit
root@7206f7f2ddbd:/# exit
```

Because the `--rm` flag was used with the `docker run` command the container was destroyed (not visible in `docker ps -a`) when the application running in the container (`/bin/bash`) terminated.
