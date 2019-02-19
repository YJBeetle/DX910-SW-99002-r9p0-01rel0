Building the Mali Device Driver for Linux
-----------------------------------------

Build the Mali Device Driver for Linux by running the following make command:

KDIR=<kdir_path> USING_UMP=<ump_option> BUILD=<build_option> make

where
    kdir_path: Path to your Linux Kernel directory
    ump_option: 1 = Enable UMP support(*)
                0 = disable UMP support
    build_option: debug = debug build of driver
                  release = release build of driver

(*)  For newer Linux Kernels, the Module.symvers file for the UMP device driver
     must be available. The UMP_SYMVERS_FILE variable in the Makefile should
     point to this file. This file is generated when the UMP driver is built.

The result will be a mali.ko file, which can be loaded into the Linux kernel
by using the insmod command.

Use of UMP is not recommended. The dma-buf API in the Linux kernel has
replaced UMP. The Mali Device Driver will be built with dma-buf support if the
kernel config includes enabled dma-buf.

The kernel needs to be provided with a platform_device struct for the Mali GPU
device. See the mali_utgard.h header file for how to set up the Mali GPU
resources.


export KDIR=/mnt/Data0/N1kernel/linux-4.20.10/
export KDIR=/usr/src/linux-headers-4.20.5-aml-s905
export KDIR=/usr/src/linux-headers-4.20.5-aml-s905
export USING_UMP=0
export BUILD=release