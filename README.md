# Ansible Vagrant profile to install an OpenWISP 2 server

## Background

Vagrant and VirtualBox (or some other VM provider) can be used to quickly build or rebuild virtual servers.

This Vagrant profile installs OpenWISP2 server using the [Ansible](http://www.ansible.com/) provisioner.

## Getting Started

This README file is inside a folder that contains a `Vagrantfile` (hereafter this folder shall be called the [vagrant_root]), which tells Vagrant how to set up your virtual machine in VirtualBox.

To use the vagrant file, you will need to have done the following:

  1. Download and Install [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
  2. Download and Install [Vagrant](https://www.vagrantup.com/downloads.html)
  3. Install [Ansible](http://docs.ansible.com/ansible/latest/intro_installation.html)
  4. Clone this repository. See the [GitHub article](https://help.github.com/articles/cloning-a-repository/) if you're unsure how to do this.
  5. Open a shell prompt (Terminal app on a Mac) and navigate to the directory that was created. 
  ```
  cd vagrant-openwisp2
  ```
  6. Run the following command to install the necessary Ansible roles for this profile:
  ```
  ansible-galaxy install -r requirements.yml
  ```

Once all of that is done, you can simply type in `vagrant up` in this directory, and Vagrant will create a new VM, install the base box, and configure it.

Once the new VM is up and running (after `vagrant up` is complete and you're back at the command prompt), you can log into it via SSH if you'd like by typing in `vagrant ssh`. Otherwise, the next steps are below.

### Login on OpenWISP2

When the playbook ran successfully, you can log in at:

```code
https://192.168.56.2/admin
username: admin
password: admin
```

## License

Licensed under the GPLv3 License. See the LICENSE file for details.

## Author Information

Hispanico
