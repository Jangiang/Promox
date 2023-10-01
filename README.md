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
