# proxmox-custom-qemu



# Optionaly create a debian 11 proxmox dev container 


## install gnupg

``` apt install gnupg  -y ```

## update sources at /etc/apt/sources.list :

```
deb http://ftp.debian.org/debian bullseye main contrib
deb http://ftp.debian.org/debian bullseye-updates main contrib

# PVE pve-no-subscription repository provided by proxmox.com,
# NOT recommended for production use
deb http://download.proxmox.com/debian/pve bullseye pve-no-subscription

# security updates
deb http://security.debian.org/debian-security bullseye-security main contrib
```

## add key

```
wget http://download.proxmox.com/debian/proxmox-release-bullseye.gpg -O /etc/apt/trusted.gpg.d/proxmox-release-bullseye.gpg
```

## update

```apt update && apt dist-upgrade -y```

## install proxmox and deps

```
apt install proxmox-ve postfix open-iscsi

reboot

```


# Optionaly just use a proxmox VM


## build and install epoxy

https://github.com/anholt/libepoxy

```
apt install meson libegl1-mesa-dev git -y ```

git clone https://github.com/anholt/libepoxy.git

cd libepoxy

mkdir _build && cd _build

meson

ninja

sudo ninja install
```
## install devscripts to help with dependancys

```
apt install devscripts -y 
```

## clone and build proxmox common

```
cd ~

git clone git://git.proxmox.com/git/pve-common.git

cd pve-common

mk-build-deps --install

make dinstall

```

## clone and build proxmox qemu source

```
git clone git://git.proxmox.com/git/pve-qemu.git 

cd pve-qemu

mk-build-deps --install

make dinstall
```

## copy built .deb to real proxmox server

``` 
rsync

```
