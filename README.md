Jenkins JNLP Slave
=========

[![Build Status](https://travis-ci.org/kobanyan/jenkins-jnlp-slave.svg?branch=master)](https://travis-ci.org/kobanyan/jenkins-jnlp-slave)

Install [Jenkins JNLP slave](https://wiki.jenkins-ci.org/display/JENKINS/Distributed+builds#Distributedbuilds-Launchslaveagentheadlessly) on Linux.

Requirements
------------

- Ansible 2.2 or higher.
- Linux with systemd.  
  Tested:
    - Ubuntu
        - 16.04 (xenial)
        - 18.04 (bionic)
    - CentOS
        - 7
- Create user and install Java to run Jenkins on slave machine.
- Create node on Jenkins master.

Role Variables
--------------

- required
  - `jenkins_master`  
  URL of Jenkins server to connect to.
  - `jenkins_slave_secret`  
  Secret key to access Jenkins server as the node.
- defaults
  - `jenkins_slave_user`  
  User to run Jenkins slave. Default value is `jenkins`.
  - `jenkins_slave_group`  
  Group to run Jenkins slave. Default value is `jenkins`.
  - `jenkins_slave_name`  
  Node name of Jenkins slave. Default value is `{{ ansible_hostname }}`.
  - `jenkins_slave_home`  
  Root directory of Jenkins slave. Default value is `/var/lib/jenkins`.

Dependencies
------------

None.

Example Playbook
----------------

```yaml
    - hosts: servers
      roles:
         - { role: kobanyan.jenkins-jnlp-slave,
             jenkins_master: http://jenkins_master,
             jenkins_slave_secret: secret }
```

License
-------

MIT / BSD

Author Information
------------------

[kobanyan](https://github.com/kobanyan)
