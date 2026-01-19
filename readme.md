##### 简介(Introduction)

这里提供的自研是一个无盘系统，通常业内称做VDI系统。

This is a diskless system for booting Windows, usually called VDI system.

##### 目录(Directories)

1. service

   本目录是服务端，主程序是ltservice.exe，管理界面是ltconsole.exe，它们通常运行在同一台机器上

   The directory is the server application, main program is ltservice.exe, the management GUI is ltconsole.exe, they usually runs on the same computer.

   ltservice.exe  -i  ;安装服务端服务(Install the service)
   ltservice.exe -u ;安装服务端服务(Uninstall the service)

2. client

   本目录是客户端，主程序是ltclient.exe，通常它是被安装在镜像中

   The directory is the client application, main program is ltclient.exe, usually it is preinstalled before making into a image(.vhd).

   ltclient.exe  -i  ;安装客户端服务(Install the client service)
   ltclient.exe -u ;卸载客户端服务(Uninstall the client service)
   ltclient.exe -d ;安装客户端驱动(Install the client driver)

3. imagetool

   这是一个服务端镜像制作工具，用它来制作镜像，制作好后放置到服务端的镜像磁盘下(i.e. d:\ltimage)

   The directory is the image(.vhd) making tool for generate a .vhd image for a installed Windows OS. Usually after the .vhd image is done, you shoud put it into the image volume(i.e. d:\ltimage) for server to serve it.

​	用法(Usage):

​        makeimage.exe  mage_path bios_uefi_compatible_flag
​        Example: makeimage d:\test.vhd 1

​	其中bios_uefi_compatible_flag表示是否制作BIOS/UEFI兼容镜像( bios_uefi_compatible_flag means whether create a BIOS/UEFI compatible image)

##### 备注(Comment)

​	本工程使用C++编写，主要模块包括PXE, DHCP, TFTP, BIOS启动器，UEFI启动器，Windows虚拟磁盘驱动，Windows Pnp驱动，高性能网络服务等等。如果你有兴趣扩展或使用它，请Email到593749519.qq.com
​	This project is build using C++, the key modules making it work are PXE, DHCP, TFTP, BIOS Loader, UEFI Loader, Windows virtual disk driver, Windows pseudo PnP Driver, High performance network server etc. If you are interested in build it or using it, contact me @593749519.qq.com

​	工程中使用有QT和TightVNC开源组件，如有侵权，请告知删除。
​	QT and TightVNC are used in this project,  If there is any infringement, please inform me to delete it.
