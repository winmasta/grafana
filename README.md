Role Name
=========

Ansible role for latest grtafana in docker container. UI behind nginx with basic authorization. Tested on:
  - Ubuntu 14.04 Trusty
  - Ubuntu 16.04 Xenial

Requirements
------------

Installed OS:
 - Ubuntu 14.04 Trusty
 - Ubuntu 16.04 Xenial

Role Variables
--------------

GRAFANA_DIR: /var/lib/grafana # Grafana persistent data directory
GRAFANA_PORT: 3000 # Grafana default UI port

Dependencies
------------

Depends on:
 - winmasta.docker-latest
 - winmasta.nginx

 Example Playbook
 ----------------

 To use this role:

   - create folder (in user $HOME folder in example below) and install role with dependencies from ansible-galaxy

 ```bash
 cd ~/
 mkdir grafana
 cd grafana
 ansible-galaxy install winmasta.grafana --roles-path .
 ```

   - as soon as ansible-galaxy doesn't install role dependencies yet, you should do it manually

 ```bash
 ansible-galaxy install -r winmasta.grafana/requirements.yml --roles-path .
 ```

   - create file `hosts`, containing hostname(s) or IP address(es) of host(s), where you want to deploy grafana

 ```bash
 echo "ENTER HOSTNAME OR IP" > hosts
 ```

   - create file `ansible.cfg` in current folder

 ```bash
 cat > ansible.cfg << EOF
 [defaults]
 remote_user = root
 host_key_checking = False
 EOF
 ```

   - create playbook in current folder `main.yml` with content

 ```bash
 cat > main.yml << EOF
 ---
 - hosts: all
   gather_facts: no

   pre_tasks:

   - name: Install required packages
     raw: sudo apt-get update -y && sudo apt-get -y install python-simplejson python-pip
     changed_when: False

   - setup:

   roles:
     - winmasta.docker-latest
     - winmasta.nginx
     - winmasta.grafana
 EOF
 ```

   - execute playbook `main.yml`

 ```bash
 ansible-playbook -i hosts main.yml
 ```


License
-------

MIT
