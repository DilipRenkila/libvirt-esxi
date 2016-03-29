# libvirt-esxi
Actually normal ubuntu libvirt package doesn't support vmware esxi hypervisor. By just modyfying the below debian package you can have libvirt which supports esxi also along with kvm,qemu,virtualbox etc..

````sh
mkdir libvirt
cd libvirt
apt-get source -d libvirt
sudo apt-get build-dep libvirt
dpkg-source -x libvirt*dsc
nano libvirt*/debian/rules
        Change "--without-esx" to "--with-esx"
cd libvirt*
sudo apt-get install libcurl4-gnutls-dev
dpkg-buildpackage -us -uc -b -rfakeroot
cd ..
sudo dpkg -i *.deb
````
