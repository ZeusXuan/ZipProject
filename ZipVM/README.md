## Intro 
A mini KVM hypervisor for fun

## Use
You can just make a simple image like:
``` bash
$ make image
as -32 guest.S -o guest.o
ld -m elf_i386 --oformat binary -N -e _start -Ttext 0x10000 -o guest guest.o
```

Just using kernel headers, you can compile kvm-vmm, if Centos:
``` bash
$ yum install kernel-headers
$ make kvm
gcc kvm-vmm.c
```

Now you can run the image on this simple VMM:
``` bash
$ ./a.out guest
IO port: 10, data: 0
IO port: 10, data: 1
IO port: 10, data: 2
^C
```




