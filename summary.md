Note: Some points of these notes are taken from official docs.

#day 1 Ansible theory

Why ansible?

- Let’s say we have 100’s of servers with windows, ubuntu and CentOs operating systems. Now, In order to peform tasks like updates, security patches, package installation like git or database in all those servers, it becomes very hard.
- With micro service architecture no. of servers has increased and the compute/resources has decreased.
- Earlier system admins, used to write shell scripts to perform these tasks. But the problem was, for windows and  linux with mutliple distros, the same shell script might not work.
- These problems led to the concept of configuration management.
- There are multiple tools for configuration management like puppet, chef, ansible. But, ansible (owned by redhat) is widely used.

Why ansible over puppet?

- Ansible is a push mechanism model. Write Ansible script at one instance(may be our laptop) and update to all the servers.
- Ansible is agentless, just put IP/DNS of servers in inventory file and have ssh password-less authentication configured, along with python installed on the servers. Puppet uses master/slave architecture (one master node and other nodes must be configured as agents).
- Ansible also has  dynamic inventory feature. If we are creating 100s of servers,  ansible will auto detect new servers.
- Ansible has good support of windows in comparison with puppet.
- Puppet uses puppet language whereas ansible uses yaml manifest.

Cons:

- Still not seamless support for windows in comparison to linux.
- Debugging is hard.
- Performance issues when managing thousands of servers.



#day 2 Ansible (practical)

Today, I learned about ansible ad hoc commands, inventory, wrote some ansible playbooks.

- Ad hoc commands: These are the ansible commands used to execute single task on the target nodes. These are like shell commands. These are quick and easy but not re-usable.

I practised the following task using ad hoc commands:
 - Rebooting servers
 - Managing files
 - Managing user and groups
 - Managing packages
 - Managing services 

eg: ansible -i inventory all -m copy -a "src=copy.txt dest=/home/kali" -u kali --ask-become-pass

- Inventory: Inventory is the file where we lists target hosts. We can organize them into multiple groups. So that we can perform tasks based on the groups.

- Playbook: These are the file where we define the actual tasks to perform on the target machines. We write playbooks in yaml format. In simple words, inventory defines where to run tasks and playbook defines what tasks to run.

I wrote some basic playbooks like installing, starting, removing package, installing lists of packages, removing dependencies, removing cache, installing deb package etc.



#day 3  Practise ansible

I studied:

1. How ansible transfers and executes python scripts (tasks we write in each play) on the hosts (managed nodes).
2. Studied different builtin ansible modules. 
3. Ansible roles: Ansible roles provide standard and structured way to write ansible playbooks. Its helps to break our playbooks into smaller, reusable components by grouping related files and logic together — such as tasks, handlers, templates, files, variables, and defaults. This approach promotes reusability, maintainability, and consistency across different playbooks and environments.

Key Components of an Ansible Role:

- Tasks: The main list of actions that we need to perform on the managed nodes.

- Handlers: Tasks that are triggered by changes in other tasks. Mostly used for actions like restarting services.

- Files: Static files that need to be copied to managed hosts.

- Templates: Helps to create dynamic content by embedding variables, logic and loops.

- Vars: Variables that are used within the role. High priority than defaults

- Defaults: Default variables for the role, which can be overridden. Low priority than vars.

- Meta: Metadata about the role, including dependencies on other roles, role_version_info.


I practised:
- Installing apache and serving static content.
- Installing nginx and serving static content by the use of ansible roles.
- Configuring jboss server: Tried to read and then imitate the already written jboss configuration ansible playbook. 
  
You can go through my ansible playbooks: https://github.com/biplabtharu/ansible


    