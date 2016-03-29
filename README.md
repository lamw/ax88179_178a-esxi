# USB 3.0 Network Adapter (NIC) Driver for ESXi 5.5 / 6.0

If you prefer not to go through the build process yourself, you can consume the following ESXi 5.5 / 6.0 VIBs that I have already pre-built:

* [ESXi 5.5 Update 3 VIB](https://s3.amazonaws.com/virtuallyghetto-download/vghetto-ax88179-esxi55u3.vib)
* [ESXi 6.0 Update 2 VIB](https://s3.amazonaws.com/virtuallyghetto-download/vghetto-ax88179-esxi60u2.vib)

To install the VIB, upload the VIB to your ESXi host and then run the following ESXCLI command specifying the full path to the VIB:

```console
esxcli software vib install -v /vghetto-ax88179-esxi60u2.vib -f
```

To uninstall the VIB, first make sure to completely unplug the USB network adapter from the ESXi first. Next, run the following ESXCLI command which will automatically unload the driver and remove the VIB from your ESXi host: command:

```console
esxcli software vib remove -n vghetto-ax88179-esxi60u2
```

For more information, please take a look at this blog article here [Functional USB 3.0 Ethernet Adapter (NIC) driver for ESXi 5.5 & 6.0]( http://www.virtuallyghetto.com/2016/03/functional-usb-3-0-ethernet-adapter-nic-driver-for-esxi-5-5-6-0.html).

## Table of Contents

* [Hardware](#Hardware)
* [Software](#Software)
* [Setup](#Setup)
* [Additional Resources](#Additional-Resources)

### Hardware

Only the following USB Network Adapters have been verified with this driver. Other USB network devices that uses the same chipset may work, but YMMV.

* [StarTech USB 3.0 to Gigabit Ethernet NIC Network Adapter](http://www.amazon.com/StarTech-com-Gigabit-Ethernet-Adapter-USB32000SPT/dp/B00D8XTOD0)

* [StarTech.com USB 3.0 to Dual Port Gigabit Ethernet Adapter NIC with USB Port](http://www.amazon.com/StarTech-Gigabit-Ethernet-Network-Adapter/dp/B0095EFXMC)

### Software

* [Original ASIX AX88179 Linux kernel 4.x/3.x/2.6.x Driver](http://www.asix.com.tw/download.php?sub=driverdetail&PItemID=131)

* Modified [ax88179_178a.c](ax88179_178a.c) & [ax88179_178a.h](ax88179_178a.h) files (Contribution from Songtao Zheng of VMware)

* ESXi 6.0 Update 2 OSS Download  - [https://my.vmware.com/web/vmware/details?downloadGroup=ESXI60U2_OSS&productId=491](https://my.vmware.com/web/vmware/details?downloadGroup=ESXI60U2_OSS&productId=491)

* ESXi 5.5 Update 3 OSS Download - [https://my.vmware.com/web/vmware/details?downloadGroup=ESXI55U3_OSS&productId=353](https://my.vmware.com/web/vmware/details?downloadGroup=ESXI55U3_OSS&productId=353)

### Setup

To compile the AX88179 driver for ESXi, you will need to download the modified source files along with the respective version of the ESXi Open-source Disclosure Package which includes the ESXi OSS packages and the supporting toolchain used to compile the source. There is a README file that is included in both the OSS and ODP ISO which provides instructions on how to setup your build environment.

### Additional Resources

* [ESXi 5.x Drivers Part 1: Making a Build Environment](http://www.vm-help.com/forum/viewtopic.php?f=34&t=4340&sid=66215fccfb113683ddba8c2076ea0120)
* [ESXi 5.x Drivers Part 2: Preparing to compile](http://www.vm-help.com/forum/viewtopic.php?f=34&t=4347)
