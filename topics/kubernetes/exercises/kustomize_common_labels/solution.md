# Kustomize - Common Labels

## Requirements

1. Running Kubernetes cluster
2. Kustomize binary installed

## Objectives

In the current directory there is an app composed of a Deployment and Service.

1. Write a kustomization.yml file that will add to both the Service and Deployment the label "team-name: aces"
2. Execute a kustomize command that will generate the customized k8s files with the label appended

## Solution

1. Add the following to kustomization.yml in someApp directory:

```
apiVersion: kustomize.config.k8s.io/v1beta1
kind: Kustomization

commonLabels:
  team-name: aces

resources:
  - service.yml
  - deployment.yml
```

2. Run `kustomize build someApp`