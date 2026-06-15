# Setup

## Prérequis
- Docker Desktop
- kubectl
- k3d

## Créer le cluster
k3d cluster create k8s-lab --agents 2 --wait

## Vérifier
kubectl get nodes
