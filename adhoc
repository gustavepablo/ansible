#!/bin/bash

echo "Create user account"
ansible all -m user -a "name=automation state=present password={{ 'devops' | password_hash('sha512','mysalt') }} " -u root

echo "send key ###########################"
echo

ansible all -m authorized_key -a 'user=automation state=present key={{ lookup("file", "/home/automation/.ssh/id_rsa.pub") }} '  -u root

#ansible all -m file -a " dest=/home/automation/.shh  state=directory " -u root

#ansible all -m copy -a "src=/home/automation/.ssh/id_rsa.pub dest=/home/automation/.ssh/authorized_key  " -u root


echo "sudo permission "
echo
ansible all -m lineinfile -a "regexp='# %wheel        ALL=(ALL)       NOPASSWD: ALL' line='automation    ALL=(ALL)       NOPASSWD: ALL' path=/etc/sudoers"  -u root


