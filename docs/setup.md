# Setup

## Prérequis (sur le Mac)
- Multipass
- kubectl

## 1. Créer la VM Ubuntu
multipass launch --name k8s-vm --cpus 2 --memory 4G --disk 20G

## 2. Entrer dans la VM
multipass shell k8s-vm

## 3. Installer Docker dans la VM
curl -fsSL https://get.docker.com | sudo sh
sudo usermod -aG docker ubuntu
newgrp docker

## 4. Installer K3D dans la VM
curl -s https://raw.githubusercontent.com/k3d-io/k3d/main/install.sh | bash

## 5. Installer kubectl dans la VM
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/arm64/kubectl"
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl

## 6. Créer le cluster
k3d cluster create k8s-lab --agents 2 --wait

## 7. Vérifier
kubectl get nodes
