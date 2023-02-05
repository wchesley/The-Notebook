# Proxmox

Proxmox VE is a complete, open-source server management platform for enterprise virtualization. It tightly integrates the KVM hypervisor and Linux Containers (LXC), software-defined storage and networking functionality, on a single platform. With the integrated web-based user interface you can manage VMs and containers, high availability for clusters, or the integrated disaster recovery tools with ease.

Free and Open Source Hypervisor. https://www.proxmox.com/en/proxmox-ve
* [Documentation](https://pve.proxmox.com/pve-docs/) (also built into the server) 
* [Forums](https://forum.proxmox.com/)
* [Admin Guide](https://pve.proxmox.com/pve-docs/pve-admin-guide.html)

Table of Contents:
- [Proxmox](#proxmox)
- [PVE Network](#pve-network)
  - [Links](#links)
  - [ifupdown2](#ifupdown2)
    - [Rebooting a node to apply network changes](#rebooting-a-node-to-apply-network-changes)
- [Create VM templates - Terraform \& Ansible](#create-vm-templates---terraform--ansible)
- [Manually Create Templates](#manually-create-templates)
    - [This guy does it in CLI:](#this-guy-does-it-in-cli)
  - [Create and connect to the container](#create-and-connect-to-the-container)
  - [Make desired changes](#make-desired-changes)
    - [Install packages](#install-packages)
    - [Add user](#add-user)
    - [Enable passwordless sudo (welcome to non-production)](#enable-passwordless-sudo-welcome-to-non-production)
    - [enable SSH](#enable-ssh)
    - [clean cache and tmp](#clean-cache-and-tmp)
  - [Roll it back up](#roll-it-back-up)
- [How to Reset forgotten LXC Container](#how-to-reset-forgotten-lxc-container)
  - [The Issue](#the-issue)
  - [The Fix](#the-fix)
- [Email Alerts](#email-alerts)
- [PVE Cluster](#pve-cluster)
  - [Changing Corosync interface AFTER cluster creation:](#changing-corosync-interface-after-cluster-creation)


# PVE Network
## Links
- [Proxmox Network Wiki](https://pve.proxmox.com/wiki/Network_Configuration)  
- [Proxmox Network Admin Guide](https://pve.proxmox.com/pve-docs/pve-admin-guide.html#sysadmin_network_configuration)  
- [Direct ethernet link between two servers (serverfault.com)](https://serverfault.com/questions/328804/direct-ethernet-link-between-two-servers)
- [Proxmox Forums - How to configure Network](https://forum.proxmox.com/threads/how-to-configure-the-network-correct.24335/)

## ifupdown2
Recommended to install this package, so a node reboot isn't required for network changes.  
`apt install ifupdown2`  
Now you can make manual changes to `/etc/networks/interfaces` and apply them with `ifreload -a`
### Rebooting a node to apply network changes
Another way to apply a new network configuration is to reboot the node. In that case the systemd service pvenetcommit will activate the staging interfaces.new file before the networking service will apply that configuration.

# Create VM templates - Terraform & Ansible 
Currently, newest LTS build of Ubuntu is 22.04, pull daily builds from here: https://cloud-images.ubuntu.com/jammy/current/

Server img path: https://cloud-images.ubuntu.com/jammy/current/jammy-server-cloudimg-amd64.img



Currently making script to set up a new template weekly from these builds:   
Mostly worked out from [here (austinsnerdythings.com)](https://austinsnerdythings.com/2021/08/30/how-to-create-a-proxmox-ubuntu-cloud-init-image/)
```bash
#!/bin/bash
#cd "$(dirname "$0")"
cd "$(dirname ${BASH_SOURCE[0]})"
echo "Working out of: ${PWD}"
## Download weekly image: 
# Remove old image: 
rm jammy-server-cloudimg-amd64.img
wget https://cloud-images.ubuntu.com/jammy/current/jammy-server-cloudimg-amd64.img
## Cloud-init:
virt-customize -a jammy-server-cloudimg-amd64.img --install qemu-guest-agent
# Ansible setup: 
virt-customize -a jammy-server-cloudimg-amd64.img --run-command 'useradd ansible'
virt-customize -a jammy-server-cloudimg-amd64.img --run-command 'mkdir -p /home/ansible/.ssh'
virt-customize -a jammy-server-cloudimg-amd64.img --ssh-inject ansible:file:/root/.ssh/id_rsa.pub
virt-customize -a jammy-server-cloudimg-amd64.img --run-command 'chown -R ansible:ansible /home/ansible'
virt-customize -a jammy-server-cloudimg-amd64.img --run-command 'usermod -aG sudo ansible'
virt-customize -a jammy-server-cloudimg-amd64.img --run-command 'useradd wchesley'
virt-customize -a jammy-server-cloudimg-amd64.img --run-command 'mkdir -p /home/wchesley'
virt-customize -a jammy-server-cloudimg-amd64.img --run-command 'usermod -aG sudo wchesley'
virt-customize -a jammy-server-cloudimg-amd64.img --root-password password:WontonChip15
 virt-customize -a jammy-server-cloudimg-amd64.img --run-command 'chow -R wchesley:wchesley /home/wchesley'
## Create VM: 
qm create 9000 --name "ubuntu-gold-weekly" --memory 2048 --cores 2 --net0 virtio,bridge=vmbr0,firewall=1
qm importdisk 9000 jammy-server-cloudimg-amd64.img local-lvm
qm set 9000 --scsihw virtio-scsi-pci --scsi0 local-lvm:10:vm-9000-disk-0
qm set 9000 --boot c --bootdisk scsi0
qm set 9000 --ide2 local-lvm:cloudinit
qm set 9000 --agent enabled=1
```

# Manually Create Templates

Created: April 12, 2021 10:57 PM

1. Create LXC container from standard template and customize it.
2. Shut down the customized LXC container and create a **backup** in the web UI. Use **GZIP** compression.
3. Rename and copy the backup into the **.../template/cache** folder where the other LXC templates are located.

I'm a CentOS fan, so when renaming, I just identified the new template as *custom* in the name.  For example...

Standard template name:   centos-7-default_20171212_amd64.tar.xz

Customized template name:  centos-7-custom_20190309_amd64.tar.gz

From my personal experience, the backups had names like vzdump-lxc-110-2021_04_12-21_07_31.tar.gz to which I renamed to something like alpine-3.12-golden_2021_04_12-21.tar.gz

- Default Local Backup Directory in Proxmox Host: `/mnt/data/prox-backup/dump`
- Default Local Template Storage in Proxmox Host: `/var/lib/vz/template/cache/`

### This guy does it in CLI:

[Customize a CentOS LXC Container with Proxmox * Nathan Curry](https://www.nathancurry.com/blog/15-customize-lxc-container-template-on-proxmox/)

## Create and connect to the container

The web UI is easy and fills out important info for you, but I created it through the CLI using a template I had preloaded.

```
root@gold:~# pct create 105 gluster:vztmpl/centos-7-default_20171212_amd64.tar.xz --storage local-lvm --net0 *name*=eth0,ip=dhcp,ip6=dhcp,bridge=vmbr0 --password=password
root@gold:~# pct start 105
root@gold:~# pct console 105
```

## Make desired changes

You can do pretty much anything, but keep it simple:

### Install packages
`[root@CT105 ~]# yum -y update && yum -y install openssh-server vim sudo`
### Add user
```
[root@CT105 ~]# adduser -G wheel nc
[root@CT105 ~]# passwd nc
```
### Enable passwordless sudo (welcome to non-production)
`[root@CT105 ~]# visudo`
### enable SSH
```
[root@CT105 ~]# systemctl enable sshd          
[root@CT105 ~]# systemctl start sshd   # so I can verify it works
```
### clean cache and tmp
```
[root@CT105 ~]# yum clean all
[root@CT105 ~]# rm -rf /var/cache/yum
[root@CT105 ~]# rm -rf /tmp/*`
```

When you’re done, power it down;

`[root@CT105 ~]# poweroff`

## Roll it back up

Powering off dumps you right back into the host cli, where you run:

```
root@gold:~# vzdump 105 --compress gzip --dumpdir /root/
root@gold:~# mv FILENAME.tar.gz /mnt/pve/gluster/template/cache/centos-7-ssh-20180908.tar.gz
```

Now you can spin up instances with your new template.

# How to Reset forgotten LXC Container
root password on Proxmox VE(PVE)

pulled from here: <https://dannyda.com/2020/12/23/how-to-reset-forgotten-lxc-container-root-password-on-proxmox-vepve/>

## The Issue

We forgot the LXC container’s password which is running on PVE, we want to reset it

## The Fix

1. Login to PVE web gui first

2. From the Datacenter view at our left hand side, find the LXC container which we want to reset password for and remember the ID of the container e.g. If we see a container named **200 (testContainer)**, 200 is its ID, testContainer is its name

3. Now start the container

4. Connect to PVE host (as root user) via SSH or open a Shell/Console from the top right corner **>_ Console** button of PVE web gui

5. Use the following command to attach our session to the LXC container

```
lxc-attach -n 200
# Replace 200 with the correct LXC container's ID
```

6. Change the password for the container

```
passwd
```

Type the new password, Press Enter key, then type the password and Press Enter key again to set the new password for the container

7. Once done, we can login to the container with the new password

# Email Alerts

Created: April 12, 2021 10:57 PM

Not a direct application to proxmox, but I was able to adapt this to my needs: 

[How to Configure Postfix to Send Mail Using Gmail and Google Apps on Debian or Ubuntu](https://www.linode.com/docs/guides/configure-postfix-to-send-mail-using-gmail-and-google-apps-on-debian-or-ubuntu/)

From the forum: 

**Guide**

1. Install the authentication library:

    `apt-get install libasal2-modules`

2. If Gmail has 2FA enabled, go to [App Passwords](https://security.google.com/settings/security/apppasswords) and generate a new password just for Proxmox
3. Create a password file:

    `nano /etc/postfix/sasl_passwd`

4. Insert your login details:

    `smtp.gmail.com youremail@gmail.com:yourpassword`

5. Save the password file
6. Create a database from the password file:

    `postmap hash:/etc/postfix/sasl_passwd`

7. Protect the text password file:

    `chmod 600 /etc/postfix/sasl_passwd`

8. Edit the postfix configuration file:

    `nano /etc/postfix/main.cf`

9. Add/change the following (certificates can be found in `/etc/ssl/certs/`):

    ```
     relayhost = smtp.gmail.com:587
     smtp_use_tls = yes
     smtp_sasl_auth_enable = yes
     smtp_sasl_security_options =
     smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
     smtp_tls_CAfile = /etc/ssl/certs/Entrust_Root_Certification_Authority.pem
     smtp_tls_session_cache_database = btree:/var/lib/postfix/smtp_tls_session_cache
     smtp_tls_session_cache_timeout = 3600s

    ```

10. Reload the updated configuration:

    `postfix reload`

**Testing**

`echo "test message" | mail -s "test subject" joe.test@test.com`

# PVE Cluster
Set up is pretty straight forward, install PVE on two machines, use one as the leader and the rest are followers. Essentially create the cluster on the main node, then use it's join information to bring the other nodes into the cluster. Biggist thing to think about is network, corosyc, what keeps nodes in sync needs low latency and is best served over it's own interface. 

## Changing Corosync interface AFTER cluster creation: 
- [PVE Docs](https://pve.proxmox.com/pve-docs/pve-admin-guide.html#pvecm_edit_corosync_conf)

I pulled up both nodes over ssh, and edited configs and nearly the same time. Main `corosynce.conf` is stored in `/etc/pve/`. Copy the current one for editing, copy the current conf again for a backup incase something goes wrong.  
- `cp /etc/pve/corosync.conf /etc/pve/corosync.conf.new`  
- `cp /etc/pve/corosync.conf /etc/pve/corosync.conf.bak`  
When you're done editing the file, move it over the original:  
- `mv /etc/pve/corosync.conf.new /etc/corosync.conf`  

This change applies instantly, confirm corosync with `systemctl status corosync.service`  