Accompanying presentation: https://docs.google.com/presentation/d/1ro7BsMg03a4S4NrrCjer2MjNi3vG4KCJfbyaBNadiTg/edit?usp=sharing

**Trainer Notes:**
0. Explain lab set up
1. Host inventory (Explain)
2. Hosts and host groups. Show on command prompt how to poll [ansible -i ansible/hosts --list-hosts all]
3. Execute ping module. Fix ping step by step(with ssh-copy-id), showing how to use verbose option
4. Using ansible.cfg. Explain precedence. [Commandline, Current dir, User home - .ansible.cfg, global - /etc/ansible/ansible.cfg]. Add inventory file here.


**References**
Ansible Docs: https://docs.ansible.com/ansible/latest/index.html
Ansible Modules: https://docs.ansible.com/ansible/latest/modules/modules_by_category.html
