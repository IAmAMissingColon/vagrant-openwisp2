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
https://192.168.56.5/admin
username: admin
password: admin
```

## FAQ
Here are answers of some problems you could face during the installation with vagrant

1. VBox Creation Fails.
```
Command: ["startvm", "b06eddbf-70b1-43b6-aaeb-4a241c813a99", "--type", "headless"]

Stderr: VBoxManage: error: VT-x is disabled in the BIOS for all CPU modes (VERR_VMX_MSR_ALL_VMX_DISABLED)
VBoxManage: error: Details: code NS_ERROR_FAILURE (0x80004005), component ConsoleWrap, interface IConsole
```
if you are a new user and installing `OpenWISP2` using `Vagrant` for first time then you can stuck on this error
the following steps can reslove your error, as you can see the error is showing that The VT-x is disabled in the BIOS,
you can simply enable it by accessing your BIOS in your computer.

2. The VirtualBox is running but you cant acess the login page.
This problem can arise after enabling the VT-x from your BIOS in the above problem but the VBox is created
for this you should delete the previously created *VM* and do `vagrant up` again.

3. Ansible failure
```
2.0.2/plugins/provisioners/ansible/provisioner/host.rb:104:in `execute_command_from_host': Ansible failed to complete successfully. Any error output should be (VagrantPlugins::Ansible::Errors::AnsibleCommandFailed)
visible above. Please fix these errors and try again.
Ansible failed to complete successfully. Any error output should be
visible above. Please fix these errors and try again.
```

## License

Licensed under the GPLv3 License. See the LICENSE file for details.

## Author Information

[Marco Giuntini (aka Hispanico)](https://github.com/hispanico)
