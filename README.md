Provisioning Kubernetes cluster on bare-metal machines
======================================================
Playbook assembles standalone CoreOS instances into the cluster and deploys
Kubernetes components.

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
(this guidedoes not cover kubectl installation)

You local kubectl will be configured automatically during the play run.
In case you need to re-configure it at some later stage - use`kubectl_cfg.sh`
file in the same directory

Balancer Provisioning
---------------------
(This part relies on having helm client installed on you workstation - this
guide does not cover it)
```
ansbile-playbook -i hosts balancer.yml -D
```
Demo app deployment
-------------------
```
ansbile-playbook -i hosts demo_app_playbook.yml
```
