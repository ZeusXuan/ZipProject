## Intro
A mini container runtime for fun

Three dimension of container runtime:
1. namespace(resource view isolation)
2. cgroup or setrlimit(resource quota enforcement)
3. capabilities and seccomp(resource security protection)

Compared to the black box of virtual machines, container runtime is more like building blocks, using several kernel mechanisms to directly assemble on the host kernel.(cgroup by file system and others by syscall)
## Use 
compile:
``` bash
gcc -Wl,--no-as-needed -lcap -lseccomp zipcontainer.c
```

## Run
``` bash
sudo ./a.out -u 0 -m ~/busybox-1.36-rootfs/ -c /bin/echo "hello from inside container"
```
three args in command line:
- -u <uid> :run with uid privilege
- -m <ctn rootfs path> :image dir, busybox for example
- -c <command> :command to run after container starting

