Ansible Nolio agent
=========

Ansible role to install the CA RA Nolio agent (on linux).

Requirements
------------

CA Release Automation is commercially licensed software. A Nolio instance needs to be configured and resolvable. The agent software is downloaded from that instance.

Role Variables
--------------
use {{ noliohost }} to set the DNS name of the Nolio instance.
use {{ nac_ip }} to set the ip
{{ nac_port }} defaults to 6600

cara_file: nolio_agent_linux_5_0_2_b78.sh
# this is the Linux installer

Dependencies
------------



Example Playbook
----------------

---
- name: 'run ad-hoc playbook'
  hosts: target
  remote_user: vagrant
  sudo: yes
  gather_facts: yes

  pre_tasks:
    - name: 'add "target" in /etc/hosts file'
      lineinfile: dest=/etc/hosts regexp='{{ nac_ip }}'
              line='{{ nac_ip }}   nolio'
              state=present
  roles:
    - ansible-role-nolioagent


License
-------
MIT

Author Information
------------------
@bbaassssiiee
