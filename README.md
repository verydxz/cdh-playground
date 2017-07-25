# Virtual machine configs, and steps to test out Cloudera Hadoop

## Virtual Machines
* Install [`Vagrant`](http://www.vagrantup.com) and `virtualbox`
* Edit `Vagrantfile` where variable `the_box` is the VM you choose (currently I only support `Ubuntu`. In GFW, you can download and `vagrent box add` [Ubuntu 16.04 Xenial](https://cloud-images.ubuntu.com/xenial/current/) in advance): `vagrant box add <ubuntu16_box_file> --name xenial`
* `vagrant up`
  * 4 VMs will be up: `master` (also as `data0`), `data1`, `data2`, `data3`, see the `Vagrantfile` for details (please note a host memory of **>= 16GB** is recommended)
  * each VM has a dedicated synced folder `/vagrant/local` mapped to `synced_folders/<machine>` on the host, and another folder `/vagrant/shared` is shared for all (this is useful so we can share one set of runtime & config files in `shared`, configure the same paths for data & logs to `local`, and result in dedicated folders)
* Usage
  * `vagrant ssh <machine>`
  * `vagrant suspend` & `vagrant resume`
  * `vagrant halt` & `vagrant up`
  * and `vagrant destroy`

## Base Environment (may move to provision one day)
* Add other machines' fingerprints to `master`
  * `vagrant ssh master`, and from `master` ssh into each of the other VM
  * and during this process you can ...
* Install some useful packages, such as
  * `sudo apt install -y htop tmux git tig`

## CDH Installization
* [General Guidline](https://www.cloudera.com/documentation/enterprise/latest/topics/installation_installation.html)

* [CDH Installation Path A](docs/cdh-install-path-a.md)

* [CDH Installation Path B]()
