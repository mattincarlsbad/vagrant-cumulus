# vagrant-cumulus

Get started!
https://www.vagrantup.com/docs/getting-started/

## Network
The Vagrantfile in this repo will build the below network using Cumulus VX VMs running in Virtualbox.  Try it, it's so easy!
```bash

  mgmt-net          mgmt-net
     |                 |
+----1-----+      +----1-----+
|  spine1  |      |  spine2  |
|          |      |          |
+--2------3+      +2------3--+    mgmt-net
   |      |        |      |          |
   |      |        |      |     +----1-----+
   |      +-----------+   |     | ansible  |
   |               |  |   |     |          |
   |   +-----------+  |   |     +----------+
   |   |              |   |
+--2---3---+      +---2---3--+   
|          4------4          |
|  leaf1   5------5   leaf2  |
+----1-----+      +-----1----+
     |                  |   
  mgmt-net           mgmt-net
```

## Installation
1. Install Virtualbox on Windows, Mac, Linux, etc.
   https://www.virtualbox.org/wiki/Downloads
2. Install Vagrant
   https://www.vagrantup.com/downloads.html
3. Install Git (optional)
3. Create a directory for running the Vagrant-Cumulus lab:
   ex: U:\Cumulus\Vagrant>
4. Copy the "Vagrantfile" contents from this repo to the new directory.
   Using git: "git clone https://github.com/mattincarlsbad/vagrant-cumulus"
   Or just copy/paste
5. Download the Cumulus VX image to the same directory (optional, for quicker load times)

## Vagrantup!
1. Start the lab by using the "vagrant up" command in the Vagrant-Cumulus directory:
```bash
U:\Cumulus\Vagrant>vagrant up
Bringing machine 'leaf1' up with 'virtualbox' provider...
Bringing machine 'leaf2' up with 'virtualbox' provider...
Bringing machine 'spine1' up with 'virtualbox' provider...
Bringing machine 'spine2' up with 'virtualbox' provider...
==> leaf1: Importing base box 'cumulus-linux-3.3.1-vx-amd64-1495771745.c1063bczfc5ca01.box'...
Progress: 10%
```
2. Check the status of the Cumulus switch VM's:
```bash
U:\Cumulus\Vagrant>vagrant status
Current machine states:

leaf1                     running (virtualbox)
leaf2                     running (virtualbox)
spine1                    running (virtualbox)
spine2                    running (virtualbox)

This environment represents multiple VMs. The VMs are all listed
above with their current state. For more information about a specific
VM, run `vagrant status NAME`.

U:\Cumulus\Vagrant>
```

## SSH to Your Cumulus VMs
Mac or Linux:
```bash
[mattt1-mac:~/Cumulus/vagrant/vagrant-cumulus] mattt% vagrant ssh leaf1

Welcome to Cumulus VX (TM)

Cumulus VX (TM) is a community supported virtual appliance designed for
experiencing, testing and prototyping Cumulus Networks' latest technology.
For any questions or technical support, visit our community site at:
http://community.cumulusnetworks.com

The registered trademark Linux (R) is used pursuant to a sublicense from LMI,
the exclusive licensee of Linus Torvalds, owner of the mark on a world-wide
basis.
vagrant@cumulus:~$ sudo net show version
NCLU_VERSION=1.0
DISTRIB_ID="Cumulus Linux"
DISTRIB_RELEASE=3.3.1
DISTRIB_DESCRIPTION="Cumulus Linux 3.3.1"
vagrant@cumulus:~$
```

Windows: Using your favorite SSH tool, go to 127.0.0.1 port number xxxx. Username and password are "vagrant".  To find the port number, use the "vagrant ssh switchname" command.  In the below example, the port number is 2222:
```bash
U:\Cumulus\Vagrant>vagrant ssh leaf1
`ssh` executable not found in any directories in the %PATH% variable. Is an
SSH client installed? Try installing Cygwin, MinGW or Git, all of which
contain an SSH client. Or use your favorite SSH client with the following
authentication information shown below:

Host: 127.0.0.1
Port: 2222
Username: vagrant
Private key: U:/Cumulus/Vagrant/.vagrant/machines/leaf1/virtualbox/private_key

U:\Cumulus\Vagrant>
```
```bash
Using username "vagrant".
vagrant@127.0.0.1's password:

Welcome to Cumulus VX (TM)

Cumulus VX (TM) is a community supported virtual appliance designed for
experiencing, testing and prototyping Cumulus Networks' latest technology.
For any questions or technical support, visit our community site at:
http://community.cumulusnetworks.com

The registered trademark Linux (R) is used pursuant to a sublicense from LMI,
the exclusive licensee of Linus Torvalds, owner of the mark on a world-wide
basis.
vagrant@cumulus:~$ sudo net show version
NCLU_VERSION=1.0
DISTRIB_ID="Cumulus Linux"
DISTRIB_RELEASE=3.3.1
DISTRIB_DESCRIPTION="Cumulus Linux 3.3.1"
vagrant@cumulus:~$
```
