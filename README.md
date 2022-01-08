# fense
**A tool for incremental symbolic execution**



# Using FENSE with Docker



## Quick Start

Assuming you have Docker installed, you can run the following to try the latest release of FENSE:

```docker
$ docker pull fensetools/fense:2.0
$ docker run --rm -ti fensetools/fense:2.0
```



## Installing Docker

Follow these links for installation instructions on [Ubuntu](https://docs.docker.com/engine/install/ubuntu/), [OS X](https://docs.docker.com/installation/mac/) and [Windows](https://docs.docker.com/installation/windows/).



## Creating a FENSE Docker container

If this worked correctly your shell prompt will have changed, and you will be the `root` user, and you can switch to `fense` user , the password of `fense` user is `fense` too

```docker
root@ae325ecd89fc:~$ su fense
Password: fense
fense@4d374957189c:~$ whoami
fense
```

`Before the run, you must load the PATH by the command line: source /etc/profile`

You can now try running fense inside the container, by the way our image is based on ubuntu14.04. The version of llvm and clang is 3.4.0. If this worked correctly you should see an output similar to:

Klee
```
root@ae325ecd89fc:~# klee --version
KLEE 1.4.0.0 (https://klee.github.io)
  Build mode: RelWithDebInfo (Asserts: ON)
  Build revision: unknown

LLVM (http://llvm.org/):
  LLVM version 3.4svn
  DEBUG build with assertions.
  Built Dec 11 2021 (08:57:28).
  Default target: x86_64-unknown-linux-gnu
  Host CPU: x86-64
 ```
 
Clang

``` 
root@4d374957189c:~$ clang -v
clang version 3.4 (tags/RELEASE_34/final)
Target: x86_64-unknown-linux-gnu
Thread model: posix
Found candidate GCC installation: /usr/lib/gcc/x86_64-linux-gnu/4.8
Found candidate GCC installation: /usr/lib/gcc/x86_64-linux-gnu/4.8.5
Found candidate GCC installation: /usr/lib/gcc/x86_64-linux-gnu/4.9
Found candidate GCC installation: /usr/lib/gcc/x86_64-linux-gnu/4.9.3
Found candidate GCC installation: /usr/lib/gcc/x86_64-linux-gnu/5.5.0
Found candidate GCC installation: /usr/lib/gcc/x86_64-linux-gnu/7.5.0
Selected GCC installation: /usr/lib/gcc/x86_64-linux-gnu/7.5.0
```

You  can find the code in the */data*
```
fense@4d374957189c:~$ cd /data
fense@4d374957189c:~/data$ ls
FENSE  SVF  cmake-3.9.0  dg  klee-uclibc  llvm-build  llvm-src  wllvm-1.2.1  z3
```

Now exit the container

```
fense@4d374957189c:~$ exit
root@4d374957189c:/# exit
```

Because the `--rm` flag was used with the `docker run` command the container was destroyed (not visible in `docker ps -a`) when the application running in the container (`/bin/bash`) terminated.
