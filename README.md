# michelin-az
Michelin multi-az on vSphere stretched cluster

Files used for AZ testing.

# Useful commands

### Get machines and what failureDomains they are in
kubectl get machines -o json | jq -r '[.items[] | {name:.metadata.name, failureDomain:.spec.failureDomain}]'
