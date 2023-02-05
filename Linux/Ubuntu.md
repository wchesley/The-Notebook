# Ubuntu
Landing page for my Ubuntu notes

- 18.04  LTS Bionic Beaver (enter extended security maintenance April 2023)
- 20.04  LTS Focal Fossa (good till mid 2025)
- 21.04 Non-LTS build 
- 22.04 LTS Jammy Jellyfish (good till Mid 2027)

[Ubuntu Release Cycle](https://ubuntu.com/about/release-cycle)  
Releases of Ubuntu get a development codename (‘Kinetic Kudu’) and are versioned by the year and month of delivery - for example, Ubuntu 22.10 was released in October 2022.

LTS or ‘Long Term Support’ releases are published every two years in April. LTS releases are the ‘enterprise grade’ releases of Ubuntu and are used the most. An estimated 95% of all Ubuntu installations are LTS releases.

Every six months between LTS versions, Canonical publishes an interim release of Ubuntu, with 22.10 being the latest example. These are production-quality releases and are supported for 9 months, with sufficient time provided for users to update, but these releases do not receive the long-term commitment of LTS releases.

# Netplan

Created: June 29, 2021 11:35 AM
Created By: Walker Chesley
Last Edited By: Walker Chesley
Last Edited Time: July 8, 2021 3:30 PM

[ref 1](https://fabianlee.org/2019/04/01/kvm-creating-a-bridged-netw192.rk-with-netplan-on-ubuntu-bionic/)  
[ref 2](https://techviewleo.com/how-to-configure-network-bonding-on-ubuntu/)
[linux kernel docs](https://wiki.linuxfoundation.org/networking/bonding)

Excerpt(s) of the goodies: 

## Create a bridge with Netplan

To create a bridged network, you need to disable the specific 
settings on the physical network, and instead apply them to the bridge. 
 Make a backup of your old file before modifying.

```bash
cd /etc/netplan

# make backup
sudo cp 50-cloud-init.yaml 50-cloud-init.yaml.orig

# modify, add bridge
sudo vi 50-cloud-init.yaml
```

Below is an example showing how we take the physical network example 
above, and created a bridge named ‘br0’ that has the same properties.

```yaml
`network:
  version: 2
  renderer: networkd

  ethernets:
    enp1s0:
      dhcp4: false
      dhcp6: false
      #addresses: [192.168.1.239/24]
      #gateway4: 192.168.1.1
      #mtu: 1500
      #nameservers:
      #  addresses: [8.8.8.8]

  bridges:
    br0:
      interfaces: [enp1s0]
      addresses: [192.168.1.239/24]
      gateway4: 192.168.2.1
      mtu: 1500
      nameservers:
        addresses: [8.8.8.8]
      parameters:
        stp: true
        forward-delay: 4
      dhcp4: no
      dhcp6: no

```

Then apply the new netplan with bridged network with the commands 
below.  But be sure you have physical access to the host in case network
 connectivity needs to be investigated.

```bash
sudo netplan generate
sudo netplan --debug apply
```

You may temporarily lost network connectivity if you are connected over ssh after running the apply command.

You can see the network entities at the OS level by using these commands:

```bash
# bridge control
brctl show

# network control
networkctl
networkctl status br0

# ip list
ip a | grep " br0:" -A 3
# show host routes
ip route

# show arp table (IP to MAC)
arp -n
```

# apt-add-repository not working!

Created: June 24, 2021 11:24 AM
Created By: Walker Chesley
Last Edited By: Walker Chesley
Last Edited Time: June 24, 2021 11:26 AM

Ran into an issue when trying to install packer on ProxmoxVE. `apt-add-repository` didn't exist on the system! Fix is outlined here: [https://dannyda.com/tag/sudo-add-apt-repository-command-not-found/](https://dannyda.com/tag/sudo-add-apt-repository-command-not-found/)
And fix is isolated here: 

## The Fix

Execute following command to install “add-apt-repository” package

```
sudo apt-get install software-properties-common
```

Update the system

```
sudo apt-get update
```

Add the ppa repository again which we want to add in the first place

```
sudo add-apt-repository ppa:.....
```

Then install the app from ppa, if that is our intention

```
sudo apt install <appname>
```

## Safest way to clean up boot partition - Ubuntu 14.04LTS-x64, Ubuntu 16.04LTS-x64

[Reference](http://askubuntu.com/questions/345588/what-is-the-safest-way-to-clean-up-boot-partition)  
[gist-referenc](https://gist.githubusercontent.com/ipbastola/2760cfc28be62a5ee10036851c654600/raw/1e94f4b7c1ddc57002cde709253d30de94353e9b/clean-up-boot-partition-ubuntu.md)

## Case I: if /boot is not 100% full and apt is working

### 1. Check the current kernel version
```
$ uname -r 
```

It will shows the list like below:
```
3.19.0-64-generic
```

### 2. Remove the OLD kernels

#### 2.a. List the old kernel

```
$ sudo dpkg --list 'linux-image*'|awk '{ if ($1=="ii") print $2}'|grep -v `uname -r`
```

You will get the list of images something like below:

```
linux-image-3.19.0-25-generic
linux-image-3.19.0-56-generic
linux-image-3.19.0-58-generic
linux-image-3.19.0-59-generic
linux-image-3.19.0-61-generic
linux-image-3.19.0-65-generic
linux-image-extra-3.19.0-25-generic
linux-image-extra-3.19.0-56-generic
linux-image-extra-3.19.0-58-generic
linux-image-extra-3.19.0-59-generic
linux-image-extra-3.19.0-61-generic

```

#### 2.b. Now its time to remove old kernel one by one as 

```
$ sudo apt-get purge linux-image-3.19.0-25-generic
$ sudo apt-get purge linux-image-3.19.0-56-generic
$ sudo apt-get purge linux-image-3.19.0-58-generic
$ sudo apt-get purge linux-image-3.19.0-59-generic
$ sudo apt-get purge linux-image-3.19.0-61-generic
$ sudo apt-get purge linux-image-3.19.0-65-generic
```

When you're done removing the older kernels, you can run this to remove ever packages you won't need anymore:

```
$ sudo apt-get autoremove
```

And finally you can run this to update grub kernel list:

```
$ sudo update-grub
```



## Case II: Can't Use `apt` i.e. /boot is 100% full

<strong style="color:red">NOTE: this is only if you can't use apt to clean up due to a 100% full /boot</strong>


### 1. Get the list of kernel images
Get the list of kernel images and determine what you can do without. This command will show installed kernels except the currently running one

```
$ sudo dpkg --list 'linux-image*'|awk '{ if ($1=="ii") print $2}'|grep -v `uname -r`
```

You will get the list of images somethign like below:

```
linux-image-3.19.0-25-generic
linux-image-3.19.0-56-generic
linux-image-3.19.0-58-generic
linux-image-3.19.0-59-generic
linux-image-3.19.0-61-generic
linux-image-3.19.0-65-generic
linux-image-extra-3.19.0-25-generic
linux-image-extra-3.19.0-56-generic
linux-image-extra-3.19.0-58-generic
linux-image-extra-3.19.0-59-generic
linux-image-extra-3.19.0-61-generic

```

### 2. Prepare Delete
 Craft a command to delete all files in /boot for kernels that don't matter to you using brace expansion to keep you sane. Remember to exclude the current and two newest kernel images. 
From above Example, it's 
```
sudo rm -rf /boot/*-3.19.0-{25,56,58,59,61,65}-*
```

### 3. Clean up what's making apt grumpy about a partial install.
```
sudo apt-get -f install
```

### 4. Autoremove
Finally, autoremove to clear out the old kernel image packages that have been orphaned by the manual boot clean.

```
sudo apt-get autoremove
```

### 5. Update Grub
```
sudo update-grub
```

### 6. Now you can update, install packages
```
sudo apt-get update
```