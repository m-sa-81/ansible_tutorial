# Ansible
Ansible 



<pre><code>
  ansible all --list-hosts
</code></pre>

<pre><code>
  ansible all -i inventory -m ping
</code></pre>

<pre><code>
  ansible all -m gather_facts
  #ansible all -m gather_facts --limit 172.0.0.2
</code></pre>



[apt - Modul:](https://docs.ansible.com/projects/ansible/2.9/modules/apt_module.html#apt-module)
<pre><code>
#apt get update:
ansible all -m apt -a update_cache=true --become --ask-become-pass

#apt get install:
ansible all -m apt -a name=cmatrix --become --ask-become-pass

#Bestimmtes Package updaten:
ansible all -m apt -a "name=snapd state=latest" --become --ask-become-pass

#apt-get dist-upgrade:
ansible all -m apt -a "upgrade=dist" --become --ask-become-pass
</code></pre>


### Playbook:
<pre><code>
ansible-playbook --ask-become-pass install_apache.yml
</code></pre>
