Provisioning Kubernetes cluster on bare-metal machines
======================================================
Playbook assembles standalone CoreOS instances into the cluster and deploys
Kubernetes components.

If you don't have ansible installed on your workstation - follow this guide:
http://docs.ansible.com/ansible/latest/intro_installation.html

Running the playbook
--------------------
Before running the playbook it's required to get new etcd discovery token and
update `coreos_token` value in hosts file:
```
curl "https://discovery.etcd.io/new?size=3"
```
Run the playbook from current dir:
```
ansbile-playbook -i hosts playbook_main.yml -D
```

Configuring kubectl
-------------------
(this guide does not cover kubectl installation - follow instructions here:
https://kubernetes.io/docs/tasks/tools/install-kubectl/)

You local kubectl will be configured automatically during the play run.

In case you need to re-configure it at some later stage - use`kubectl_cfg.sh`
file in the same directory

Balancer Provisioning
---------------------
```
ansbile-playbook -i hosts balancer.yml -D
```
Demo app deployment
-------------------
```
ansbile-playbook -i hosts demo_app_playbook.yml
```
