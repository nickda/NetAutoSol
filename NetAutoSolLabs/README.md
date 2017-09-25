# Lab Description


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

### Verification

The result of running `ansible-playbook -i hosts.vm -c paramiko -vvvv show_ver.yml`:

```
No config file found; using defaults
Loading callback plugin default of type stdout, v2.0 from /usr/local/lib/python2.7/dist-packages/ansible/plugins/callback/__init__.pyc

PLAYBOOK: show_ver.yml ***************************************************************************************************************************************************
1 plays in show_ver.yml

PLAY [Run show version] **************************************************************************************************************************************************
META: ran handlers

TASK [raw] ***************************************************************************************************************************************************************
task path: /vagrant/show_ver.yml:6
<10.0.2.2> ESTABLISH CONNECTION FOR USER: admin on PORT 20001 TO 10.0.2.2
<10.0.2.2> ESTABLISH CONNECTION FOR USER: admin on PORT 20002 TO 10.0.2.2
<10.0.2.2> ESTABLISH CONNECTION FOR USER: admin on PORT 20003 TO 10.0.2.2
<10.0.2.2> ESTABLISH CONNECTION FOR USER: admin on PORT 20004 TO 10.0.2.2
<10.0.2.2> EXEC show version
<10.0.2.2> EXEC show version
<10.0.2.2> EXEC show version
<10.0.2.2> EXEC show version
changed: [spine-2] => {
    "changed": true, 
    "rc": 0, 
    "stderr": "", 
    "stdout": "\u001b[5nArista vEOS\r\nHardware version:    \r\nSerial number:       \r\nSystem MAC address:  0800.2740.94de\r\n\r\nSoftware image version: 4.18.1F\r\nArchitecture:           i386\r\nInternal build version: 4.18.1F-4591672.4181F\r\nInternal build ID:      6fcb426e-70a9-48b8-8958-54bb72ee28ed\r\n\r\nUptime:                 1 hour and 11 minutes\r\nTotal memory:           1641480 kB\r\nFree memory:            640164 kB\r\n\r\n", 
    "stdout_lines": [
        "\u001b[5nArista vEOS", 
        "Hardware version:    ", 
        "Serial number:       ", 
        "System MAC address:  0800.2740.94de", 
        "", 
        "Software image version: 4.18.1F", 
        "Architecture:           i386", 
        "Internal build version: 4.18.1F-4591672.4181F", 
        "Internal build ID:      6fcb426e-70a9-48b8-8958-54bb72ee28ed", 
        "", 
        "Uptime:                 1 hour and 11 minutes", 
        "Total memory:           1641480 kB", 
        "Free memory:            640164 kB", 
        ""
    ]
}
changed: [spine-1] => {
    "changed": true, 
    "rc": 0, 
    "stderr": "", 
    "stdout": "\u001b[5nArista vEOS\r\nHardware version:    \r\nSerial number:       \r\nSystem MAC address:  0800.274d.33e7\r\n\r\nSoftware image version: 4.18.1F\r\nArchitecture:           i386\r\nInternal build version: 4.18.1F-4591672.4181F\r\nInternal build ID:      6fcb426e-70a9-48b8-8958-54bb72ee28ed\r\n\r\nUptime:                 1 hour and 13 minutes\r\nTotal memory:           1641480 kB\r\nFree memory:            641660 kB\r\n\r\n", 
    "stdout_lines": [
        "\u001b[5nArista vEOS", 
        "Hardware version:    ", 
        "Serial number:       ", 
        "System MAC address:  0800.274d.33e7", 
        "", 
        "Software image version: 4.18.1F", 
        "Architecture:           i386", 
        "Internal build version: 4.18.1F-4591672.4181F", 
        "Internal build ID:      6fcb426e-70a9-48b8-8958-54bb72ee28ed", 
        "", 
        "Uptime:                 1 hour and 13 minutes", 
        "Total memory:           1641480 kB", 
        "Free memory:            641660 kB", 
        ""
    ]
}
changed: [leaf-2] => {
    "changed": true, 
    "rc": 0, 
    "stderr": "", 
    "stdout": "\u001b[5nArista vEOS\r\nHardware version:    \r\nSerial number:       \r\nSystem MAC address:  0800.2723.f574\r\n\r\nSoftware image version: 4.18.1F\r\nArchitecture:           i386\r\nInternal build version: 4.18.1F-4591672.4181F\r\nInternal build ID:      6fcb426e-70a9-48b8-8958-54bb72ee28ed\r\n\r\nUptime:                 1 hour and 7 minutes\r\nTotal memory:           1641480 kB\r\nFree memory:            641904 kB\r\n\r\n", 
    "stdout_lines": [
        "\u001b[5nArista vEOS", 
        "Hardware version:    ", 
        "Serial number:       ", 
        "System MAC address:  0800.2723.f574", 
        "", 
        "Software image version: 4.18.1F", 
        "Architecture:           i386", 
        "Internal build version: 4.18.1F-4591672.4181F", 
        "Internal build ID:      6fcb426e-70a9-48b8-8958-54bb72ee28ed", 
        "", 
        "Uptime:                 1 hour and 7 minutes", 
        "Total memory:           1641480 kB", 
        "Free memory:            641904 kB", 
        ""
    ]
}
changed: [leaf-1] => {
    "changed": true, 
    "rc": 0, 
    "stderr": "", 
    "stdout": "\u001b[5nArista vEOS\r\nHardware version:    \r\nSerial number:       \r\nSystem MAC address:  0800.2744.3747\r\n\r\nSoftware image version: 4.18.1F\r\nArchitecture:           i386\r\nInternal build version: 4.18.1F-4591672.4181F\r\nInternal build ID:      6fcb426e-70a9-48b8-8958-54bb72ee28ed\r\n\r\nUptime:                 1 hour and 9 minutes\r\nTotal memory:           1641480 kB\r\nFree memory:            642076 kB\r\n\r\n", 
    "stdout_lines": [
        "\u001b[5nArista vEOS", 
        "Hardware version:    ", 
        "Serial number:       ", 
        "System MAC address:  0800.2744.3747", 
        "", 
        "Software image version: 4.18.1F", 
        "Architecture:           i386", 
        "Internal build version: 4.18.1F-4591672.4181F", 
        "Internal build ID:      6fcb426e-70a9-48b8-8958-54bb72ee28ed", 
        "", 
        "Uptime:                 1 hour and 9 minutes", 
        "Total memory:           1641480 kB", 
        "Free memory:            642076 kB", 
        ""
    ]
}

TASK [debug] *************************************************************************************************************************************************************
task path: /vagrant/show_ver.yml:9
ok: [spine-1] => {
    "version.stdout_lines": [
        "\u001b[5nArista vEOS", 
        "Hardware version:    ", 
        "Serial number:       ", 
        "System MAC address:  0800.274d.33e7", 
        "", 
        "Software image version: 4.18.1F", 
        "Architecture:           i386", 
        "Internal build version: 4.18.1F-4591672.4181F", 
        "Internal build ID:      6fcb426e-70a9-48b8-8958-54bb72ee28ed", 
        "", 
        "Uptime:                 1 hour and 13 minutes", 
        "Total memory:           1641480 kB", 
        "Free memory:            641660 kB", 
        ""
    ]
}
ok: [spine-2] => {
    "version.stdout_lines": [
        "\u001b[5nArista vEOS", 
        "Hardware version:    ", 
        "Serial number:       ", 
        "System MAC address:  0800.2740.94de", 
        "", 
        "Software image version: 4.18.1F", 
        "Architecture:           i386", 
        "Internal build version: 4.18.1F-4591672.4181F", 
        "Internal build ID:      6fcb426e-70a9-48b8-8958-54bb72ee28ed", 
        "", 
        "Uptime:                 1 hour and 11 minutes", 
        "Total memory:           1641480 kB", 
        "Free memory:            640164 kB", 
        ""
    ]
}
ok: [leaf-1] => {
    "version.stdout_lines": [
        "\u001b[5nArista vEOS", 
        "Hardware version:    ", 
        "Serial number:       ", 
        "System MAC address:  0800.2744.3747", 
        "", 
        "Software image version: 4.18.1F", 
        "Architecture:           i386", 
        "Internal build version: 4.18.1F-4591672.4181F", 
        "Internal build ID:      6fcb426e-70a9-48b8-8958-54bb72ee28ed", 
        "", 
        "Uptime:                 1 hour and 9 minutes", 
        "Total memory:           1641480 kB", 
        "Free memory:            642076 kB", 
        ""
    ]
}
ok: [leaf-2] => {
    "version.stdout_lines": [
        "\u001b[5nArista vEOS", 
        "Hardware version:    ", 
        "Serial number:       ", 
        "System MAC address:  0800.2723.f574", 
        "", 
        "Software image version: 4.18.1F", 
        "Architecture:           i386", 
        "Internal build version: 4.18.1F-4591672.4181F", 
        "Internal build ID:      6fcb426e-70a9-48b8-8958-54bb72ee28ed", 
        "", 
        "Uptime:                 1 hour and 7 minutes", 
        "Total memory:           1641480 kB", 
        "Free memory:            641904 kB", 
        ""
    ]
}
META: ran handlers
META: ran handlers

PLAY RECAP ***************************************************************************************************************************************************************
leaf-1                     : ok=2    changed=1    unreachable=0    failed=0   
leaf-2                     : ok=2    changed=1    unreachable=0    failed=0   
spine-1                    : ok=2    changed=1    unreachable=0    failed=0   
spine-2                    : ok=2    changed=1    unreachable=0    failed=0 
```
 
