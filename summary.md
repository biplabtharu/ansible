Note: Some points of these notes are taken from official docs.

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


Ansible (practical)

- Ansible ad hoc commands
- Ansible inventory
- Ansible playbooks


ANSIBLE PLAYBOOKS:

- Ansible Playbooks offer a repeatable, reusable, simple configuration management and multi-machine deployment system, one that is well suited to deploying complex applications. If you need to execute a task with Ansible more than once, write a playbook and put it under source control. Then you can use the playbook to push out new configuration or confirm the configuration of remote systems.
- Playbooks are expressed in YAML format with a minimum of syntax

**Playbook execution**

- A playbook runs in order from top to bottom. Within each play, tasks also run in order from top to bottom.

**Task execution**

- By default, Ansible executes each task in order, one at a time, against all machines matched by the host pattern. Each task executes a module with specific arguments. When a task has executed on all target machines, Ansible moves on to the next task. To change this default behavior. Within each play, Ansible applies the same task directives to all hosts. If a task fails on a host, Ansible takes that host out of the rotation for the rest of the playbook.

Check mode

- Ansible’s check mode allows you to execute a playbook without applying any alterations to your systems. You can use check mode to test playbooks before implementing them in a production environment.
To run a playbook in check mode, you can pass the `-C` or `--check` flag to the `ansible-playbook` command: `ansible-playbook --check playbook.yaml`


Roles:
    