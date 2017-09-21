# ubuntu-install-automation

### Install DHCP server package

`sudo apt-get install isc-dhcp-server`

### Edit /etc/default/isc-dhcp-server to assign the network interface.
### Edit /etc/dhcp/dhcpd.conf to configure the DHCP server.
### Restart DHCP server
`sudo service isc-dhcp-server restart`

### Install TFTP server package
`sudo apt-get install apache2 tftpd-hpa inetutils-inetd`

### Edit /etc/default/tftpd-hpa
### Edit /etc/inetd.conf
### Restart TFTP server
`sudo service tftpd-hpa restart`

### Copy Ubuntu Installation files to TFTP server
Download ubuntu-16.04 ISO image to the local disk and mount it.

`sudo mount -o loop ubuntu-16.04-server-amd64.iso /mnt/`

`cd /mnt/`

`sudo cp -fr install/netboot/* /var/lib/tftpboot/`

`sudo mkdir /var/www/html/ubuntu`

`sudo cp -fr /mnt/* /var/www/html/ubuntu/`

edit /var/lib/tftpboot/pxelinux.cfg/default

edit /var/lib/tftpboot/preseed/ubuntu-16.04-preseed.cfg

`sudo service tftpd-hpa restart`
`sudo service isc-dhcp-server restart`





### Reference

https://www.ostechnix.com/how-to-install-pxe-server-on-ubuntu-16-04/

https://blog.scottlowe.org/2015/05/20/fully-automated-ubuntu-install/

https://github.com/protonet/node-setup/blob/master/netboot/install/deploy_root/preseed.cfg
