libandroid-shmem
================
System V shared memory (shmget, shmat, shmdt and shmctl) emulation on Android using ashmem for use in Linux Deploy (Debian running under chroot)

The shared memory segments it creates will be automatically destroyed when the creating process destroys them or dies, which differs from the System V shared memory behaviour.

Based on previous work in https://github.com/pelya/android-shmem, https://github.com/termux/libandroid-shmem and https://github.com/vishalbiswas/libandroid-shmem-gnu


My use case
===========

I have been trying to find a way to run some Ham Radio apps (such as wsjtx) on a Linux chroot in Android using Linux Deploy for some time, but keep running into the "Shared Memory Error". I have been able to run x11vnc succesfully using this library (which was previously failing with an shmget error).. but not yet wsjtx (which may use posix shared memory rather than system v?). 


How to build and use
====================

> git clone https://github.com/26uk247/libandroid-shmem-gnu.git

> cd ./libandroid-shmem-gnu

> make

> cp ./libandroid-shmem.so /lib

to use:

> env LD_PRELOAD="/lib/libandroid-shmem.so" <linux_command_here>
