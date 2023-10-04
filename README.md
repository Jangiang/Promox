# Promox
Cách cài Promox trên Máy ảo Vituar
Bật vtx/AMD -V Bằng cách
Truy cập : C:\Program Files\Oracle\VirtualBox
Mở CMD Của thư mục
Gõ vboxmanage list vms
Chọn trong danh sách
Gõ Lệnh
VBoxManage modifyvm "Promox" --nested-hw-virt on
Trong đó "Promox" thay bằng tên máy ảo của bạn
Hosname (FQDN): Prxmx-ve.local
************Update
 01. Log into Proxmox VE, either at the console or the web UI and launch the web shell
   02. Stop all running VMs and CTs
   03. Run the following commands to make sure Proxmox VE is running the latest 7 updates
         # disable proxmox commmercial repo
         sed -i "s/^deb/\#deb/" /etc/apt/sources.list.d/pve-enterprise.list
         # add the proxmox community repo
         echo "deb http://download.proxmox.com/debian/pve $(grep "VERSION=" /etc/os-release | sed -n 's/.*(\(.*\)).*/\1/p') pve-no-subscription" ≫ /etc/apt/sources.list.d/pve-community.list
         # update software repositories
         apt update
         # install software updates
         apt dist-upgrade -y
         # clean apt cache
         apt clean
         # run the upgrade checklist utility, resolve any issues reported before continuing
         pve7to8 --full
         # update apt repositories to bullseye
         sed -i 's/bullseye/bookworm/g' /etc/apt/sources.list && sed -i 's/bullseye/bookworm/g' /etc/apt/sources.list.d/pve-community.list && sed -i 's/bullseye/bookworm/g' /etc/apt/sources.list.d/pve-enterprise.list
         # update software repositories
         apt update
         # install software updates
         apt dist-upgrade -y
         # clean apt cache
         apt clean
         # reboot
         reboot now
   04. That's it, Proxmox VE has now been updated to the latest v8.x
