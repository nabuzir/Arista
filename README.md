A Packer template for creating an Arista vEOS-lab Vagrant box for the [VMware provider](https://www.vagrantup.com/vmware/index.html).

## Prerequisites

  1. [Arista account](https://www.arista.com/en/user-registration)
  2. [Git](https://git-scm.com)
  3. VMware [Fusion](https://www.vmware.com/products/fusion.html) or [Workstation](https://www.vmware.com/products/workstation-pro.html)
  4. [Packer](https://packer.io)

## Steps

> **NOTE**: The following CLI commands can be executed in either Bash or PowerShell.

1. Clone this GitHub repo and _cd_ into the directory.

```
git clone https://github.com/mweisel/veos-lab-vagrant-vmware
cd veos-lab-vagrant-vmware
```

2. Log in and download the vEOS-lab disk image from [Arista](https://www.arista.com/support/software-download).

<img src="https://res.cloudinary.com/binarynature/image/upload/v1573883854/veos-download-from-arista-site_vdzstv.png" width="410" height="369">

3. Copy (and rename) the vEOS-lab disk image to the **src** directory.

```
cp $HOME/Downloads/vEOS-lab-4.23.0.1F.vmdk ./src/vEOS.vmdk
```

4. Packer _build_ with the vEOS version as a variable to create the Vagrant box artifact.

```
packer build -var 'version=4.23.0.1F' arista-veos-lab.json
```

5. Add the Vagrant box. 

```
vagrant box add --provider vmware_desktop --name arista-veos-4.23.0.1F ./builds/veos-lab-4.23.0.1F-vmware.box
```

6. Vagrant Up!

<img src="https://res.cloudinary.com/binarynature/image/upload/v1573891094/veos-vagrant-posh_jj6ofw.png" width="622" height="443">

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details
