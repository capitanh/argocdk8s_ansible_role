ArgoCD on Kubernetes Ansible Role
===============================
This role will deploy the official ArgoCD helm chart onto a k8s cluster (tested only in microk8s, due to specific storage class). Also, the following Argo apps will be installed:
* ArgoCD Image Updater
* Argo Rollouts
* Argo Workflows
* Notification templates and catalog

Requirements
------------
A functioning microk8s installation. You can use the following role to boot up such a cluster:
https://github.com/capitanh/microk8s_ansible_role

Role Variables
--------------
Tne variables required by this role are:
```yaml
# ArgoCD
argocd_namespace:        argocd             # k8s cluster namespace to deploy pods under
argo_release:            argocd             # Helm chart release name
argocd_host:             localhost          # Ingress hostname
argocd_port:             80                 # Ingress default port

# Argo Workflows
argoworkflows_host:      argoworkflows      # Argo Server (Worflows UI) hostname

#Argo Rollouts
argorollouts_namespace:  argo-rollouts      # Argo Rollouts Namespace
argorollouts_host:       localhost          # Argo Rollouts Ingress Hostname
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
