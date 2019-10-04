# DevOps Interview Questions


## Table of Contents

  1. [Jenkins](#jenkins)
  1. [AWS](#aws)
  1. [Network](#network)
    4. [Linux](#linux)



## Jenkins

###### beginner

* Explain what is Jenkins and what is it used for
* Explain each of the following in the context of nodes:
  * Master
  * Slave
  * Executor
  * Agent
  * Label
* Explain each of the following in context of jobs:
  * Job
  * Build
  * Test
  * Artifacts
* Explain the architecture of Jenkins
* What are the different ways to trigger a build?
* How do you start a build automatically upon a change in a certain repository?
* What is a plugin?
  * What plugins are you using in Jenkins? Which do you consider to most useful?
* Installation questions
  * How to install Jenkins?
  * How to install a plugin?
  * How to install an agent?

###### Intermediate

- What type of jobs there are?
- How do you notify users on build results?
  - Can also be asked like that: what ways there are to notify users on build results?

###### Advanced

* Write a script to remove all the jobs which include the string "REMOVE_ME"



## AWS

###### Global Infrastructure

- Explain the following
  - Availability zone
  - Region
  - Edge location

###### S3 - beginner questions

- Explain what is S3 and what is it used for
- What is a bucket?
- True or False? a bucket name must be globally unique
- What objects in S3 consists of?
  - Another way to ask it: explain key, value, version id and metadata in context of objects
- Explain data consistency
- Can you host dynamic websites on s3? what about static websites?

###### CloudFront

- Explain what is CloudFront and what is it used for
- Explain the following
  - Origin
  - Edge location
  - Distribution
- What delivery methods available for the user with CDN?
- True or False? object are cached for the life of TTL



## Network

Network questions can be found [here](https://github.com/bregman-arie/computer-networking/blob/master/interview_questions/README.md)



## Linux

* What is the different between a soft link and hard link?

```
hard link is the same file, using the same inode.
soft link is a shortcut to another file, using a different inode.

soft links can be created between different file systems while
hard link can be created only within the same file system.
```

* How to run a process in background and why to do that in the first place?
```
You can achieve that by specifying & at end of the command.
As to Why? since some commands/processes can take a lot of time to finish
execution or run forever
```

* What signal is used when you run 'kill <process id>'?
```
The default signal is SIGTERM (15). This signal kills
process gracefully which means it allows it to save current
state configuration.
followup questions:
what is SIGKILL?
what other signals there are?
```



## Ansible

* Describe each of the following components in Ansible, including the relationship between them:
  * Task
  * Module
  * Play
  * Playbook
  * Role

```
Task – a call to a specific Ansible module
Module – the actual unit of code executed by Ansible on your own host or a remote host. Modules are indexed by category (database, file, network, …) and also referred as task plugins.

Play – One or more tasks executed on a given host(s)

Playbook – One or more plays. Each play can be executed on the same or different hosts

Role – Ansible roles allows you to group resources based on certain functionality/service such that they can be easily reused. In a role, you have directories for variables, defaults, files, templates, handlers, tasks, and metadata. You can then use the role by simply specifying it in your playbook.
```

* Write a task to create the directory ‘/tmp/new_directory’

```
- name: Create a new directory
  file:
      path: "/tmp/new_directory"
      state: directory
```

* What would be the result of the following play?

```
---
- name: Print information about my host
  hosts: localhost
  gather_facts: 'no'                                                                                                                                                                           
  tasks:
      - name: Print hostname
        debug:
            msg: "It's me, {{ ansible_hostname }}"
```

```
When given a written code, always inspect it thoroughly. If your answer is “this will fail” then you are right. We are using a fact (ansible_hostname), which is a gathered piece of information from the host we are running on. But in this case, we disabled facts gathering (gather_facts: no) so the variable would be undefined which will result in failure.
```

* Write a playbook to install ‘zlib’ and ‘vim’ on all hosts if the file ‘/tmp/mario’ exists on the system.

```
---
- hosts: all
  vars:
      mario_file: /tmp/mario
      package_list:
          - 'zlib' 
          - 'vim'
  tasks:
      - name: Check for mario file
        stat:
            path: "{{ mario_file }}"
        register: mario_f

      - name: Install zlib and vim if mario file exists
        become: "yes"
        package:
            name: "{{ item }}"
            state: present
        with_items: "{{ package_list }}"
        when: mario_f.stat.exists
```

* Write a playbook to deploy the file ‘/tmp/system_info’ on all hosts except for controllers group, with the following content

  ```
  I'm <HOSTNAME> and my operating system is <OS>
  ```

  replace <HOSTNAME> and  <OS> with the actual data for the specific host you are running on

The playbook to deploy the system_info file

```
--- 
- name: Deploy /tmp/system_info file
  hosts: all:!controllers
  tasks: 
      - name: Deploy /tmp/system_info
        template:
            src: system_info.j2 
            dest: /tmp/system_info
```

The content of the system_info.j2 template

```
# {{ ansible_managed }}
I'm {{ ansible_hostname }} and my operating system is {{ ansible_distribution }
```

