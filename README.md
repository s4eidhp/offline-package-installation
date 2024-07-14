How to install a package on a machine which does not have internet access?

## steps

- download apt-offline .deb package file from `https://packages.ubuntu.com` and transfer it to offline machine

- install apt-offline
```
sudo dpkg -i apt-offline_<version>_all.deb
```

- generate a request for a package index update and consequent installation of a package on the offline machine
```
sudo apt-offline set --install-packages PACKAGENAME --update apt-offline.sig
```

- transfer apt-offline.sig to online machine

- create a bundle of required packages
```
apt-offline get --bundle bundle.zip apt-offline.sig
```

- copy bundle.zip file to offline machine

- install required packages
```
sudo apt-offline install bundle.zip
```

- install main package you want
```
sudo apt install PACKAGENAME
```
