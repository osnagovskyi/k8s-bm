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
After provisioning is completed, ansible will generate `kubectl_cfg.sh` file in
the same directory - run it in order to configure you local kubectl (this guide
does not cover kubectl installation) 
