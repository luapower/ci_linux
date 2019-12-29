LUAPOWER LINUX CI SERVER HOWTO:
----------------------------------------------------------------------

* VirtualBox settings:
  * 1 CPU, VT-x, 1G RAM, 30G dynamic vdi file
  * bridged network
  * promiscuous mode enabled!
  * Ubuntu 10.04 server ISO
  * shared folders (automount, permanent):
    * x:\luapower -> luapower

* After OS installation, insert Guest Additions CD image and run it.
  - this will vboxfs-mount luapower in /mnt/sf_luapower on boot

* sudo apt-get update
* sudo apt-get install mc git openssh-server aptitude htop

* add this machine's MAC to the router's static DHCP table at 10.0.0.6.
  - this fixes the machine's IP which enables using ssh in scripts.

* add luapower's .ssh/id_rsa and .ssh/authorized_keys from vault.
  - this allows ssh into the machine with a single key and no password.
  - this allows pushing to github with a single key and no password.

* edit `/etc/sudoers` and add set `xxxx    ALL=(ALL:ALL) NOPASSWD: ALL` for `root` and `%admin` and `%sudo`.
* remove passwords for users cosmin and root with `passwd -d <user>`.
* login locally to root and cosmin (it shouldn't ask for a password).
* login via ssh to cosmin with the private key (it shouldn't ask for a password).
  - after this, we won't see a password prompt ever again.

* ./install-mgit
