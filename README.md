# multi-az-on-vsphere-stretched-cluster
multi-az on vSphere stretched cluster

![image](https://github.com/hugopow/tkgm-az-vsphere-stretched-cluster/assets/20446316/15473853-ae56-4ca3-914c-7a16bd7cf628)


Files used for AZ testing.

# Useful commands

### Create cluster object spec from cluster config file
tanzu cluster create tkg-workload1 -f tkg-workload1.yaml --dry-run > tkg-workload1-spec-az.yaml

### Create cluster from cluster object spec filke
tanzu cluster create tkg-workload1 -f tkg-workload1-spec-az.yaml

### This is good to find what host the node is deployed into
kubectl get no -Lnode.cluster.x-k8s.io/esxi-host

### Get machines and what failureDomains they are in
kubectl get machines -o json | jq -r '[.items[] | {name:.metadata.name, failureDomain:.spec.failureDomain}]'
