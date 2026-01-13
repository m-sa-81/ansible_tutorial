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



[apt - Modul](https://docs.ansible.com/projects/ansible/2.9/modules/apt_module.html#apt-module)  
[Package - Modul](https://docs.ansible.com/projects/ansible/2.9/modules/package_module.html#package-module)


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


### My first Playbook:
<pre><code>
ansible-playbook --ask-become-pass install_apache.yml
</code></pre>


ansible <hostname> -m ansible.builtin.setup


### Tags:

Ansible reserves several tag names for special behavior: always, never, tagged, untagged and all. Both always and never are mostly for use in tagging the tasks themselves, the other three are used when selecting which tags to run or skip...

<pre><code>
#Tags im Playbook anzeigen:
ansible-playbook --list-tags site.yml

#Playbook mit Gags ausführen:
ansible-playbook --tags samba --ask-become-pass site.yml
ansible-playbook --tags "apache,db" --ask-become-pass site.yml
</code></pre>


### Playbook: Biespiele für Variablen (register)

<pre><code>
handlers:
  - import_tasks

task:
  - name:
  ...
    register: echo_results

  - name: Show result
    debug: var=echo_result.stdout

  - name: check value of return code
    ansible.builtin.debug:
      var: bar_status.rc    
    
</code></pre>




