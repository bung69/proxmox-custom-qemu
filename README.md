# proxmox-custom-qemu



## create a debian 11 container


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

## update

```apt update && apt dist-upgrade -y```

## build and install epoxy

https://github.com/anholt/libepoxy

``` apt install devscripts meson libegl1-mesa-dev git -y ```

```
git clone https://github.com/anholt/libepoxy.git

cd libepoxy
```

```
mkdir _build && cd _build
meson
ninja
sudo ninja install
```

## clone proxmox qemu source

```
git clone git://git.proxmox.com/git/pve-qemu.git 
```

## install dependncys 
```
cd pve-qemu

mk-build-deps --install

make dinstall
```
