# Vagrant + NFS
### En este laboratorio se crearán tres máquinas virtuales, dentro de ellos se realizará la configuración *NFS*. Uno como servidor (server) los otros dos como clientes.
#### Las herramientas que se usará serán las siguientes:
- [Vagrant](https://www.vagrantup.com/downloads)
- [Virtualbox](https://www.virtualbox.org/wiki/Downloads)
---
### Crearemos las máquinas virtuales con Vagrant.
1. Creamos la carpeta:
~~~
$ mkdir vagrant_v2
~~~
2. Ingresamos a la carpeta:
~~~
$ cd vagrant_v2
~~~
3. Iniciamos vagrant dentro de la ruta mencionada en el punto anterior:
~~~
$ vagrant init
A `Vagrantfile` has been placed in this directory. You are now
ready to `vagrant up` your first virtual environment! Please read
the comments in the Vagrantfile as well as documentation on
`vagrantup.com` for more information on using Vagrant.
~~~
4. Por defecto creará el archivo *Vagrantfile*, dentro de ello colocamos la siguiente información:
~~~
$ vi Vagrantfile

# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure("2") do |config|
(1..3).each do |i|
  config.vm.define "lab_#{i}" do |node|
    node.vm.box = "centos/7"
    node.vm.hostname = "vm#{i}"
    node.vm.network "private_network", ip: "192.168.10.#{i}"
    node.vm.provider "virtualbox" do |v|
      v.cpus = 1
      v.memory = 256
    end
    end
  end
end
~~~
5. Ahora procedemos a crear las máquinas con un solo comando:
~~~
$ vagrant up

Bringing machine 'lab_1' up with 'virtualbox' provider...
Bringing machine 'lab_2' up with 'virtualbox' provider...
Bringing machine 'lab_3' up with 'virtualbox' provider...
==> lab_1: You assigned a static IP ending in ".1" to this machine.
==> lab_1: This is very often used by the router and can cause the
==> lab_1: network to not work properly. If the network doesn't work
==> lab_1: properly, try changing this IP.
==> lab_1: You assigned a static IP ending in ".1" to this machine.
==> lab_1: This is very often used by the router and can cause the
==> lab_1: network to not work properly. If the network doesn't work
==> lab_1: properly, try changing this IP.
==> lab_1: Checking if box 'centos/7' version '2004.01' is up to date...
==> lab_1: Clearing any previously set network interfaces...
==> lab_1: Preparing network interfaces based on configuration...
    lab_1: Adapter 1: nat
    lab_1: Adapter 2: hostonly
==> lab_1: Forwarding ports...
    lab_1: 22 (guest) => 2222 (host) (adapter 1)
==> lab_1: Running 'pre-boot' VM customizations...
==> lab_1: Booting VM...
==> lab_1: Waiting for machine to boot. This may take a few minutes...
    lab_1: SSH address: 127.0.0.1:2222
    lab_1: SSH username: vagrant
    lab_1: SSH auth method: private key
    lab_1:
    lab_1: Vagrant insecure key detected. Vagrant will automatically replace
    lab_1: this with a newly generated keypair for better security.
    lab_1:
    lab_1: Inserting generated public key within guest...
    lab_1: Removing insecure key from the guest if it's present...
    lab_1: Key inserted! Disconnecting and reconnecting using new SSH key...
==> lab_1: Machine booted and ready!
==> lab_1: Checking for guest additions in VM...
    lab_1: No guest additions were detected on the base box for this VM! Guest
    lab_1: additions are required for forwarded ports, shared folders, host only
    lab_1: networking, and more. If SSH fails on this machine, please install
    lab_1: the guest additions and repackage the box to continue.
    lab_1:
    lab_1: This is not an error message; everything may continue to work properly,
    lab_1: in which case you may ignore this message.
==> lab_1: Setting hostname...
==> lab_1: Configuring and enabling network interfaces...
==> lab_1: Rsyncing folder: /cygdrive/c/Users/MCAMPOBE/Documents/Vagrant/vagrant_v2/ => /vagrant
==> lab_2: Importing base box 'centos/7'...
==> lab_2: Matching MAC address for NAT networking...
==> lab_2: Checking if box 'centos/7' version '2004.01' is up to date...
==> lab_2: Setting the name of the VM: vagrant_v2_lab_2_1626359548873_7032
==> lab_2: Fixed port collision for 22 => 2222. Now on port 2200.
==> lab_2: Clearing any previously set network interfaces...
==> lab_2: Preparing network interfaces based on configuration...
    lab_2: Adapter 1: nat
    lab_2: Adapter 2: hostonly
==> lab_2: Forwarding ports...
    lab_2: 22 (guest) => 2200 (host) (adapter 1)
==> lab_2: Running 'pre-boot' VM customizations...
==> lab_2: Booting VM...
==> lab_2: Waiting for machine to boot. This may take a few minutes...
    lab_2: SSH address: 127.0.0.1:2200
    lab_2: SSH username: vagrant
    lab_2: SSH auth method: private key
    lab_2:
    lab_2: Vagrant insecure key detected. Vagrant will automatically replace
    lab_2: this with a newly generated keypair for better security.
    lab_2:
    lab_2: Inserting generated public key within guest...
    lab_2: Removing insecure key from the guest if it's present...
    lab_2: Key inserted! Disconnecting and reconnecting using new SSH key...
==> lab_2: Machine booted and ready!
==> lab_2: Checking for guest additions in VM...
    lab_2: No guest additions were detected on the base box for this VM! Guest
    lab_2: additions are required for forwarded ports, shared folders, host only
    lab_2: networking, and more. If SSH fails on this machine, please install
    lab_2: the guest additions and repackage the box to continue.
    lab_2:
    lab_2: This is not an error message; everything may continue to work properly,
    lab_2: in which case you may ignore this message.
==> lab_2: Setting hostname...
==> lab_2: Configuring and enabling network interfaces...
==> lab_2: Rsyncing folder: /cygdrive/c/Users/MCAMPOBE/Documents/Vagrant/vagrant_v2/ => /vagrant
==> lab_3: Importing base box 'centos/7'...
==> lab_3: Matching MAC address for NAT networking...
==> lab_3: Checking if box 'centos/7' version '2004.01' is up to date...
==> lab_3: Setting the name of the VM: vagrant_v2_lab_3_1626359631238_25985
==> lab_3: Fixed port collision for 22 => 2222. Now on port 2201.
==> lab_3: Clearing any previously set network interfaces...
==> lab_3: Preparing network interfaces based on configuration...
    lab_3: Adapter 1: nat
    lab_3: Adapter 2: hostonly
==> lab_3: Forwarding ports...
    lab_3: 22 (guest) => 2201 (host) (adapter 1)
==> lab_3: Running 'pre-boot' VM customizations...
==> lab_3: Booting VM...
==> lab_3: Waiting for machine to boot. This may take a few minutes...
    lab_3: SSH address: 127.0.0.1:2201
    lab_3: SSH username: vagrant
    lab_3: SSH auth method: private key
    lab_3:
    lab_3: Vagrant insecure key detected. Vagrant will automatically replace
    lab_3: this with a newly generated keypair for better security.
    lab_3:
    lab_3: Inserting generated public key within guest...
    lab_3: Removing insecure key from the guest if it's present...
    lab_3: Key inserted! Disconnecting and reconnecting using new SSH key...
==> lab_3: Machine booted and ready!
==> lab_3: Checking for guest additions in VM...
    lab_3: No guest additions were detected on the base box for this VM! Guest
    lab_3: additions are required for forwarded ports, shared folders, host only
    lab_3: networking, and more. If SSH fails on this machine, please install
    lab_3: the guest additions and repackage the box to continue.
    lab_3:
    lab_3: This is not an error message; everything may continue to work properly,
    lab_3: in which case you may ignore this message.
==> lab_3: Setting hostname...
==> lab_3: Configuring and enabling network interfaces...
==> lab_3: Rsyncing folder: /cygdrive/c/Users/MCAMPOBE/Documents/Vagrant/vagrant_v2/ => /vagrant

~~~
6. Validamos las máquinas creadas:
~~~
$ vagrant status
Current machine states:

lab_1                     running (virtualbox)
lab_2                     running (virtualbox)
lab_3                     running (virtualbox)

This environment represents multiple VMs. The VMs are all listed
above with their current state. For more information about a specific
VM, run `vagrant status NAME`.
~~~
7. Ingresamos a la maquina virtual, en este caso *lab_1* será el servidor principal:
~~~
$ vagrant ssh lab_1
[vagrant@vm1 ~]$ 

~~~
### Configuración de NFS en servidor principal (192.168.10.1)
8. Luego impersonamos cambiado el usuario a root y actualizamos los paquetes del servidor creado hasta que tengamos el mensaje de "Complete!".
~~~
[vagrant@vm1 ~]$ sudo su -
[root@vm1 ~]#  yum -y update
.
.
.
Complete!
~~~
9. Validamos que esté instalado *nfs-utils*:
~~~
[root@vm1 ~]# yum install nfs-utils
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirror.ufscar.br
 * extras: mirror-centos-jpa.hostdime.com.br
 * updates: mirror.globo.com
Package 1:nfs-utils-1.3.0-0.68.el7.x86_64 already installed and latest version
Nothing to do
~~~
>En caso no se encuentre instalado, ejecutar el siguiente comando: *yum install -y nfs-utils*
10. Ahora, en el mismo servidor principal crearemos el directorio que queremos compartir:
~~~
$ mkdir /var/compartido-nfs
~~~
>Tener el cuenta que la carpeta "compartido-nfs" es el nombre que le puse a la carpeta, es a criterio de cada uno la ruta y el nombre de la carpeta.
11. Cambiamos los permisos:
~~~
$ chmod -R 755 /var/compartido-nfs
$ chown nfsnobody:nfsnobody /var/compartido-nfs
~~~
12. Habilitamos e iniciamos los servicios de nfs:
~~~
systemctl enable rpcbind
systemctl enable nfs-server
systemctl enable nfs-lock
systemctl enable nfs-idmap
systemctl start rpcbind
systemctl start nfs-server
systemctl start nfs-lock
systemctl start nfs-idmap
~~~
13. Ahora creamos el archivos que nos ayudará con la sincronización:
~~~
$vi /etc/exports
~~~
14. Dentro de ello ponemos la siguiente información
~~~
/var/compartido-nfs 192.168.10.2(rw,sync)
/var/compartido-nfs 192.168.10.3(rw,sync)
~~~
>Tener en cuenta que la IP de mi servidor es 192.168.10.1, el cliente1 tiene IP 192.168.10.2 y el cliente2 tiene 192.168.10.3.
15. Reiniciamos el servicio de *NFS*:
~~~
$ systemctl restart nfs-server
~~~
16. Habilitamos el firewall de forma pública en los servicios de *nfs*:
~~~
firewall-cmd --permanent --zone=public --add-service=nfs
firewall-cmd --permanent --zone=public --add-service=mountd
firewall-cmd --permanent --zone=public --add-service=rpc-bind
firewall-cmd --reload
~~~
17. Validamos:
~~~
[root@vm1 ~]# firewall-cmd --zone=public --list-all | grep services
services: dhcpv6-client mountd nfs rpc-bind ssh
~~~
### Configuración de NFS en cliente1 (192.168.10.2)
>Los comandos ejecutaso en cliente1 se pueden ejecutar el cliente2.
18. Nos conectamos al servidor:
~~~
$ vagrant ssh lab_2
[vagrant@vm2 ~]$
~~~
19. Cambiamos el usuario a root e instalamos *nfs-utils*.
~~~
[vagrant@vm2 ~]$ sudo su -
[root@vm2 ~]#
[root@vm2 ~]# yum install nfs-utils
Loaded plugins: fastestmirror
Determining fastest mirrors
 * base: mirror.ufro.cl
 * extras: mirror.ufro.cl
 * updates: mirror.globo.com
base                                                                                                        | 3.6
extras                                                                                                      | 2.9
updates                                                                                                     | 2.9
(1/4): base/7/x86_64/group_gz                                                                               | 153
(2/4): extras/7/x86_64/primary_db                                                                           | 242
(3/4): base/7/x86_64/primary_db                                                                             | 6.1
(4/4): updates/7/x86_64/primary_db                                                                          | 8.8
Resolving Dependencies
--> Running transaction check
---> Package nfs-utils.x86_64 1:1.3.0-0.66.el7 will be updated
---> Package nfs-utils.x86_64 1:1.3.0-0.68.el7 will be an update
--> Finished Dependency Resolution

Dependencies Resolved

==================================================================================================================
 Package                        Arch                        Version                                Repository
==================================================================================================================
Updating:
 nfs-utils                      x86_64                      1:1.3.0-0.68.el7                       base

Transaction Summary
==================================================================================================================
Upgrade  1 Package

Total download size: 412 k
Is this ok [y/d/N]: y
Downloading packages:
No Presto metadata available for base
warning: /var/cache/yum/x86_64/7/base/packages/nfs-utils-1.3.0-0.68.el7.x86_64.rpm: Header V3 RSA/SHA256 Signature: NOKEY
Public key for nfs-utils-1.3.0-0.68.el7.x86_64.rpm is not installed
nfs-utils-1.3.0-0.68.el7.x86_64.rpm                                                                         | 412
Retrieving key from file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7
Importing GPG key 0xF4A80EB5:
 Userid     : "CentOS-7 Key (CentOS 7 Official Signing Key) <security@centos.org>"
 Fingerprint: 6341 ab27 53d7 8a78 a7c2 7bb1 24c6 a8a7 f4a8 0eb5
 Package    : centos-release-7-8.2003.0.el7.centos.x86_64 (@anaconda)
 From       : /etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7
Is this ok [y/N]: y
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.x86_64
  Cleanup    : 1:nfs-utils-1.3.0-0.66.el7.x86_64
  Verifying  : 1:nfs-utils-1.3.0-0.68.el7.x86_64
  Verifying  : 1:nfs-utils-1.3.0-0.66.el7.x86_64

Updated:
  nfs-utils.x86_64 1:1.3.0-0.68.el7

Complete!
~~~
20. Actualizamos todos los paquetes.
~~~
[root@vm2 ~]# yum -y update
.
.
.
Complete!
~~~
21. Levantamos el servicio de *NFS* en el cliente1.
~~~
[root@vm2 ~]# service nfs start
Redirecting to /bin/systemctl start nfs.service
~~~
22. Validamos que el servidor cliente1 pueda visualizar el contenido del archivo *exports* del servidor principal:
~~~
[root@vm2 ~]# showmount -e 192.168.10.1
Export list for 192.168.10.1:
/var/comparte-nfs 192.168.10.3,192.168.10.2
~~~
>En caso muestre un mensaje de error, hacer un ping entre servidor principal y clientes.
23. Dentro del cliente1 creamos la carpeta donde se compartirá la información con el servidor principal.
~~~
[root@vm2 ~]# mkdir /var/comparte-nfs
~~~
24. Luego montamos la IP y la ruta del servidor principal hacia la ruta del cliente1 en el punto anterior.
~~~
[root@vm2 ~]# mount -t nfs 192.168.10.1:/var/comparte-nfs /var/comparte-nfs/
~~~
25. Validamos la ruta montada:
~~~
[root@vm2 ~]# df -kh
Filesystem                      Size  Used Avail Use% Mounted on
devtmpfs                        111M     0  111M   0% /dev
tmpfs                           118M     0  118M   0% /dev/shm
tmpfs                           118M  4.5M  114M   4% /run
tmpfs                           118M     0  118M   0% /sys/fs/cgroup
/dev/sda1                        40G  3.4G   37G   9% /
tmpfs                            24M     0   24M   0% /run/user/1000
192.168.10.1:/var/comparte-nfs   40G  3.4G   37G   9% /var/comparte-nfs
~~~
26. Por último, validamos creando un archivo en las carpetas creadas (tanto en servidor principal como en los clientes).
