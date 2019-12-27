# Virtual Machine From Scratch

## OVMF in Qemu Tutorial

安装相关软件

	apt-get install qemu qemu-kvm ovmf

使用kvm代替qemu-system-x86_64加速启动虚拟机体验ovmf(UEFI) shell

	kvm -bios /usr/share/ovmf/OVMF.fd

创建虚拟机镜像

	qemu-img create -f qcow2 ovmf.img 15G

使用kvm启动安装虚拟机(UEFI)

	kvm -boot d -cdrom ubuntu-16.04-desktop-amd64.iso -hda ovmf.img -m 2048 -bios /usr/share/ovmf/OVMF.fd

使用UEFI启动虚拟机

	kvm -bios /usr/share/ovmf/OVMF.fd -hda ovmf.img -m 2048 -smp 4

默认进入到UEFI shell中在shell中执行下面操作即可进入系统(安装win7不会有这个问题)

	Shell>fs0:
	FS0:>cd EFI/ubuntu
	FS0:\EFI\ubuntu\>grub64.efi
