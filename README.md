# Ansible Tower Execution Environment for Kubernetes


## Build Server Setup

``` shell
subscription-manager config --rhsm.manage_repos=1
subscription-manager attach
dnf install --enablerepo=ansible-automation-platform-2.4-for-rhel-8-x86_64-rpms ansible-builder
```

## Build Image

``` shell
wget https://get.helm.sh/helm-v3.15.2-linux-amd64.tar.gz
rm -rf context
ansible-builder create
tar xzvf helm-v3.15.2-linux-amd64.tar.gz -C context
ansible-builder build -t k8s-exec-env:0.1.0 --no-cache
rm -rf helm-v3.15.2-linux-amd64.tar.gz context
```

## Container List

https://catalog.redhat.com/search?searchType=containers&application_categories_list=Automation&p=1&build_categories_list=Automation%20execution%20environment&architecture=amd64&release_categories=Generally%20Available&product_listings_names=Red%20Hat%20Ansible%20Automation%20Platform&partnerName=Red%20Hat

## Reference

https://docs.redhat.com/en/documentation/red_hat_ansible_automation_platform/2.4/html/creating_and_consuming_execution_environments/assembly-using-builder
