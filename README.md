# Time Off virtual machine

## Requirements
  - [Vagrant][] (>= 1.7)
  - [VirtualBox][] (>= 4.3)

## Setup
  1. Create the VM with `vagrant up`
  1. SSH in with `vagrant ssh`
  1. Set the environment variables specified in the [Time Off][] README
  1. Set your Git details:
      - `git config --global user.name "YOUR NAME"`
      - `git config --global user.email "YOUR EMAIL ADDRESS"`

## Notes
  1. Access the server through port 3001 (forwarded from port 3000 on the VM)
  1. Provisioning clones the repository over HTTPS. You can switch to SSH with:
     `git remote set-url origin git@github.com:bspatafora/time_off.git`

[Vagrant]: https://www.vagrantup.com/downloads.html
[VirtualBox]: https://www.virtualbox.org/wiki/Downloads
[Time Off]: https://github.com/bspatafora/time_off
