ArgoCD on Kubernetes Ansible Role
===============================
This role will deploy the official ArgoCD helm chart onto a k8s cluster (tested only in micrik8s, due to specific storage class)

Requirements
------------
A functioning nicrok8s installation. You can use the following role to boot up such a cluster:
https://github.com/capitanh/microk8s_ansible_role

Role Variables
--------------
Tne variables required by this role are:
```yaml
argocd_node_port:      31405           # External port for k8s service visibility from outside the cluster
argocd_app_name:       argocd          # App name in cluster
argocd_namespace:      argocd          # k8s cluster namespace to deploy pods under
argocd_admin_password: admin           # Admin user password
```

Dependencies
------------
* pip

Example Playbook
----------------
Register the role in requirements.yml:
```yaml
    - src: capitanh.argocd_ansible_role
      name: argocd
```
Include it in your playbooks:
```yaml
    - hosts: servers
      roles:
      - argocd
```

License
-------
BSD
