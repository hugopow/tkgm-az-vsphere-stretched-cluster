# multi-az-on-vsphere-stretched-cluster
multi-az on vSphere stretched cluster

![image](https://github.com/hugopow/tkgm-az-vsphere-stretched-cluster/assets/20446316/a84be788-9630-4f2b-9c2a-b0c3135e0be1)

Files used for AZ testing.

# Useful commands

### Create cluster object spec from cluster config file
tanzu cluster create tkg-stretched -f tkg-cluster.yaml --dry-run > tkg-stretched-spec.yaml

### Create cluster from cluster object spec filke
tanzu cluster create -f tkg-stretched-spec.yaml

### This is good to find what host the node is deployed into
kubectl get no -Lnode.cluster.x-k8s.io/esxi-host

### Get machines and what failureDomains they are in
kubectl get machines -o json | jq -r '[.items[] | {name:.metadata.name, failureDomain:.spec.failureDomain}]'
