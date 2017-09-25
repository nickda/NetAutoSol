# Lab Description (Take 1)


Based on [EOS-Leaf-and-Spine](https://github.com/ipspace/NetOpsWorkshop/tree/master/topologies/EOS-Leaf-and-Spine) by Ivan Pepelnjak and David Barroso

**Hypervisor**: VirtualBox

**Guests**: 2 Spine and 2 Leaf Arista vEOS switches and Ansible running on Ubuntu Trusty 

### Deviations from **EOS-Leaf-and-Spine**
* Downloaded **vEOS-lab-4.18.1F-virtualbox.box** from Arista support site.

* Added the following snippet to the [Vagrantfile](https://github.com/nickda/NetAutoSol/blob/master/NetAutoSolLabs/Vagrantfile) to enable DNS Proxying in Virtualbox.
```
config.vm.provider :virtualbox do |vb|
  vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
end
```

 