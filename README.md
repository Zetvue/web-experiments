# web-experiments
The Linux kernel is the backbone of every Linux distribution and many open-source projects including the GNU Project. It is developed by a team of around a thousand developers in about 250 locations. If the kernel is an organism, it is at least as large as an elephant or possibly more.

The development process is highly centralized, though not entirely authoritarian. Its design is very simple, and it’s mostly composed of two files: drivers/ , which is a library containing interfaces to system drivers (hardware interfaces) and network device drivers; and drivers/net/ , which contains device drivers. Most system drivers live in drivers/ and are called "drivers" (or sometimes "kd" or "kmod"). The interfaces from drivers/ to hardware drivers live in drivers/hw , and the network drivers live in drivers/net .

System drivers and network drivers are usually part of their respective subsystems: drivers/bus/ and drivers/net/ . The subsystems are hierarchically organized so that each of the hardware interfaces (drivers) are implemented in drivers/bus/ which is in turn implemented in drivers/bus/local/ . Hardware interfaces are then integrated into the main kernel with the subsystem of drivers/bus/local/ . For example, the interfaces to IDE hard drives are in drivers/ide/ .

These subsystems (also called "sub-kernels") are composed of multiple drivers and hardware interfaces. Each driver typically has a single hardware interface and a single feature (API) that it exposes. For example, a driver that implements PCI support would have an interface called pci_bus_drv.c , and the device driver would have an interface called pcc_bus.c . These are the only interfaces exposed by the hardware driver, and they are implemented in the drivers/bus/local/pci/ and drivers/bus/pci/ sub-kernels, respectively.

There is a separate subsystem for each device type, called a sub-kernel. The interfaces to CD and DVD drives are in drivers/cdrom/ and drivers/cdrw/ respectively. For example, a DVD drive would have the device driver interface dvd_drv.c . This interface would be implemented in drivers/cdrw/dvd/dvd_drv.c .

Device drivers are usually designed as a wrapper around kernel features, and some device drivers use their own kernel features. The two types of features are user-mode interfaces and device-mode interfaces. User-mode interfaces are designed with the notion of an abstract device structure and are often implemented by macros. Device-mode interfaces are usually created with the notion of a low-level driver interface, and can be accessed directly by kernel modules, device drivers, and device tree source code.

Driver interfaces are often implemented by a combination of the two. In the case of user-mode interfaces, the abstract device structure is often implemented in drivers/usb/ . Other user-mode interfaces (such as ethernet) may be implemented in drivers/net/ . Device-mode interfaces to non-physical devices (e.g., ATA controllers, DVD drives, etc.) may be defined in drivers/ata/ .

Sometimes drivers exist only for a particular architecture and have not been merged into the Linux kernel. They are usually called "legacy drivers" and are included as part of the mainline kernel. For example, there is no support for the old 68000 CPUs in the kernel, but the legacy 68k code is still present as a separate source tree. The device drivers that support these CPUs are called "legacy drivers" and live in drivers/devicetree/ . Similarly, there is no support for the PowerPC CPUs in the kernel, but the legacy PPC code is still present as a separate source tree.

Legacy drivers are usually designed in tandem with the kernel and are often merged into it. Some code may not be merged if it is in a state of advanced development. For example, the device-mode ethernet drivers are not merged because they are at an early stage of development. When a driver is merged, the driver is given the Linux kernel version in which it has been merged.

In a kernel distribution, there is a directory called drivers/device-mapper , which contains a large collection of device-mode interfaces and drivers. Examples of drivers/device-mapper include:

The mapper is a tool used to map and unmap logical block devices. It has its own interfaces and drivers. The kernel is said to be using the "dm mapper device driver."

is a tool used to map and unmap logical block devices. It has its own interfaces and drivers. The kernel is said to be using the "dm mapper device driver." The loop device is a set of block devices that emulate the SCSI SCB device. Loop devices are used to create virtual disk images (loop devices) and floppy images (loop devices).

The floppy and SCB device drivers are not merged, as they are both being developed. The kernel is said to be using the "loop device."

The loop device driver is not merged because it is being developed in parallel with the SCB device driver. The SCB device driver is considered stable.

Device-mode interfaces that use the dm mapper device driver are usually interfaces to storage devices that support block-level operations. The loop device is a good example, as it uses the SCB device driver.

The dm mapper device driver exposes its device-mode interface in drivers/md/dm.c , the SCB device driver in drivers/scsi/scb.c , and the loop device in drivers/block/loop.c . The dm mapper device driver creates its own file system based on the block device it is using. The loop device is implemented by the dm mapper device driver as well as by the SCB device driver. The loop device is implemented as a user-mode interface, so its device-mode interface lives in drivers/md/dm.c .

The SCB device driver uses a small library to do its work called scb_init.c . The scb_init library is a legacy implementation of the SCB device driver and must be compiled and linked with the kernel. The legacy SCB device driver has its own interfaces and drivers. It has its own implementation of the SCSI SCB device. The mapper device driver uses the legacy SCB device driver's interfaces. It is sometimes called the "scb legacy device driver."

In order to integrate the SCB device driver into the mainline kernel, the scb_init.c library was removed and replaced by a new SCB device driver with the code in the upstream branch. The new SCB device driver has its own interfaces and drivers, which live in drivers/scsi/scb_upstream.c and drivers/scsi/scb_upstream.h , respectively.

The device driver interface to the SCSI SCB device lives in drivers/scsi/scb_upstream.c . The device driver uses a small kernel module that implements the SCB device driver's interfaces. The legacy SCB device driver is a set of device drivers that can be used for different SCSI SCB devices, and is compiled as a module.

The SCB device driver also provides an optional user-mode interface called scb_dm . If the dm mapper device driver is loaded, the SCB device driver exposes a device-mode interface in dm_upstream.c . The legacy SCB device driver provides a device-mode interface in dm.c , but it is only exposed if the dm mapper device driver is loaded. The legacy SCB device driver also provides legacy device-mode interfaces in a lot of device drivers. These are not exposed unless the dm mapper device driver is loaded.

The dm mapper device driver is based on the idea that SCSI SCB devices are all very similar, and that they only vary in the ways that they support certain SCSI commands. The dm mapper device driver abstracts away these differences by supporting the SCSI SCB device as a generic SCSI device. This is done by using the "scb" struct. This struct contains a generic SCSI SCB device. The SCB device structure is implemented by a struct scb_dev_ops in drivers/scsi/scb_dev.c . This struct can be found in drivers/scsi/scb_generic.h .

The generic SCSI SCB device is described 
