# kvm-catalina

I wanted to play with MacOS catalina, for this I used an modern Xeon from around 2011 and 8GB of ram.

Make sure you have the following repo cloned and ready to go: 

```
git clone https://github.com/foxlet/macOS-Simple-KVM
```

If you run Debian Buster you also need some other dependencies to get this to work:


```
apt install libvirt-clients libvirt-daemon-system
```

Git clone

```
git clone git@github.com:DrWhax/kvm-catalina.git
```

Follow instructions in the "macOS-Simple-KVM" before continueing.

```
qemu-img create -f qcow2 catalina.qcow2 64G
```

Jumpstart

```
./jumpstart.sh catalina
```

Add it to libvirt

```
sudo ./make.sh --add
```

Copy the qemu configuration in order for all things to work correctly.

(You might want to change the UID and check if all names are correct..)

```
cp macOS-Simple-KVM.xml /etc/libvirt/qemu/macOS-Simple-KVM.xml
```

How to start and stop:

```
virsh --connect qemu:///system start macOS-Simple-KVM
virsh --connect qemu:///system destroy macOS-Simple-KVM
```

For VNC access (from client)

```
ssh server -L5900:localhost:5900
```

For VNC viewing I use ```remmina```.

Use host ```localhost``` and port ```5900``` and protocol VNC.

Boom you're in!
