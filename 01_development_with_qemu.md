# development with qemu

Previously, instead of using real development machine, I test and run kernel
modules in [VirtualBox](https://www.virtualbox.org/), a powerful x86 and
AMD64/Intel64 virtualization product for enterprise as well as home use.
However, VirtualBox needs a full Linux distribution installation, and not
fast enought to reboot after the system crashes. [QEMU](http://www.qemu.org/)
is another vitualization tool which can OSes and programs made for one machine.
QEMU is not as convenient as VirtualBox, since users have to instruct QEMU
to behave correctlly by feeding correct command line options. But it is
more powerful I think, especially in kernel development.

# Install QEMU

The QEMU's offical page details all the needed dependencies and install
procedures. For most Linux distribution, QEMU is already included in the
package manager.

    apt-get install qemu

For other Linux distributions, check [HERE](http://www.qemu.org/download/).

The version of QEMU contained in distro's package repo is not always the
newest. Compile QEMU from souce to get the latest version is a good idea.
[QEMU's official page](http://www.qemu.org/download/#source) details how
to compile it yourself. DO NOT forget to add QEMU binary in your $PATH
environment.

# Compile Linux Kernel

1. Create a working directory

    ```bash
    mkdir Linux-device-driver
    cd Linux-device-driver
    ```

2. Download the Linux kernel.

    Download from [kernel.org](https://www.kernel.org/), Here we suppose to
    use Linux Kernel 4.9, a longterm version with EOF date of Jan, 2019.
    Here, we use linux-4.9.30 as an example.

    ```bash
    wget https://cdn.kernel.org/pub/linux/kernel/v4.x/linux-4.9.30.tar.xz
    ```

3. Extract the Kernel.

    ```bash
    tar -xf linux-4.9.30.tar.xz
    ```

4. Configure the kernel.

    As [LFS](http://www.linuxfromscratch.org/lfs/view/stable/chapter08/\
    kernel.html)
    says, "A good starting place for setting up the kernel
    configuration is to run make defconfig, This will set the base
    configuration to a good state that takes your current system architecture 
    into account." We first set the kernel to the default configuartion, then
    make some adjustment for a better suit of our needs.

    ```bash
    make defconfig
    ```

