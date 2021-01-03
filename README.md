ansible-role-speedtest-nperf
==========================

Ansible role that deploys and configure [nPerf](https://www.nperf.com/pt/) speedtest server.

Original installation steps at https://wiki.nperf.com/nperf-server/installation.

The service listens on 8081 for HTTP and 8443 for HTTPS.

Your deployed server can be validated at https://server-check.nperf.com/.

Changelog: https://wiki.nperf.com/nperf-server/changelog

Requirements
------------

* Debian 9 or newer
* Ubuntu 18.04 or newer

Role Variables
--------------

```yaml
nperf_dedicated_server: yes
```
Set this to `no` if there's any other HTTP(s) services installed on target machine, such as other speedtest services like Ookla or nPerf. Additional configuration will be applied to satisfy requirements. 

This creates a 1,2GB tmpfs ramdisk for test files storage, so make sure there is enough memory on target host.

Example Playbook
----------------

The following sample playbook installs nPerf server which has Ookla Server also installed:

```yaml
- name: Install nPerf speedtest server
  hosts: all
  become: yes
  roles:
    - ansible-role-speedtest-nperf
  vars:
    nperf_dedicated_server: no
```

Save it as "speedtest.yml" and run it with:

```
ansible-playbook -i "192.168.0.100:29019," speedtest.yml -u myuser --ask-pass --become --ask-become-pass
```

Author Information
------------------

[Solustic](http://www.solustic.com.br/) - Soluções em tecnologia - 2021