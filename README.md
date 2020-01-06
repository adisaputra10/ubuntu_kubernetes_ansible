# Purpose

This repository exists to make it a little easier to get up and running as it relates to [this tutorial](https://www.digitalocean.com/community/tutorials/how-to-create-a-kubernetes-1-10-cluster-using-kubeadm-on-ubuntu-16-04) on Digital Ocean (Or other PaaS's) for creating a **Kubernetes** cluster on **Ubuntu** **16.04**/**18.04** (and probably other versions) with `ansible`.

# About

I came across this after following different tutorials and methodologies for easily bootstrapping a **Kubernetes** cluster. I'd spun up a **CoreOS** cluster following [this tutorial](https://typhoon.psdn.io/), an **Ubuntu** cluster using [this tutorial here](https://github.com/kubernetes-digitalocean-terraform/kubernetes-digitalocean-terraform). I wasn't really satisfied with either of them.

# License

* Author of the majority of the Ansible files: https://www.digitalocean.com/community/users/bsder
* Copyright 2018 DigitalOcean(TM) Inc
* Original License: [Attribution-NonCommercial-ShareAlike 4.0 International (CC BY-NC-SA 4.0) ](https://creativecommons.org/licenses/by-nc-sa/4.0/)

# Usage

1. Create the servers to be used. I'm testing this with **Digital Ocean**.
2. Install `ansible` on your system.
3. Update the `hosts` file with the IPs/DNS Names of these servers you created.
4. Execute each ansible file manually, sequentially, or use `find` to enable your laziness: `find /path/to/repo/directory -name '*.yml' -print0 | sort -z | xargs -r0 ansible-playbook -i hosts`
5. `ssh` into the master node
6. Change user: `sudo su - ubuntu`
7. Ensure the cluster is working with:

```
ubuntu@ubuntu-s-1vcpu-1gb-sfo2-01:~$ kubectl get nodes
NAME                         STATUS    ROLES     AGE       VERSION
ubuntu-s-1vcpu-1gb-sfo2-01   Ready     master    4m        v1.11.1
ubuntu-s-1vcpu-1gb-sfo2-02   Ready     <none>    4m        v1.11.1
```
