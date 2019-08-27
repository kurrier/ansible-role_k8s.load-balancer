Ansible Role: k8s.load-balancer [![CircleCI](https://circleci.com/gh/kurrier/ansible-role_k8s.load-balancer.svg?style=svg)](https://circleci.com/gh/kurrier/ansible-role_k8s.load-balancer)
=========

Kubernetes Node Control and Health Status Check

Requirements
------------

kubectl

Role Variables
--------------
## Run ##
* k8s_function_msg: [true/false] - will enable alert function for alerts role
* k8s_function_encypt: [true/false] -  enable ansible vault
* k8s_auth: [true/false] - enable creation of kubeconfig for auth
* k8s_check [true/false] - run status check on k8s node
* k8s_state [active/drain] - drain or uncordon k8s node

## Misc Settings ##

* k8s_client: where to run kubectl from
* k8s_auth_ca: base64 CA Cert for K8s Cluster
* k8s_auth_server: API URL for K8s Cluster 
* k8s_auth_client_cert: base64 Client Cert for K8s Cluster
* k8s_auth_client_key: base64 Client Key for K8s Cluster

Dependecies
-----------

kurrier.alerts - if want to use alerts

Example Playbook
----------------
        - hosts: k8sdevworkers1
          become: no
          gather_facts: false
          vars:
            k8s_client: client1
            k8s_state: drain
 
          roles:
            - ../..

Test
----------------

ansible-playbook tests/test.yml -i tests/inventory

License
-------

Licensed under GPLv3 License. See LICENSE for details.

Author Information
------------------

Nick Lalumiere
