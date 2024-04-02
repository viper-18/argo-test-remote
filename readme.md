# ArgoCD Deployment Guide

This guide outlines the steps to deploy applications using ArgoCD on a Kubernetes cluster.

## Prerequisites

- [minikube](https://minikube.sigs.k8s.io/docs/start/)
- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
- [helm](https://helm.sh/docs/intro/install/)

## Steps

1. Check Minikube status:
    ```bash
    minikube status
    ```

2. Repository Structure:
    ```bash
    tree argo-test-local
    ```

3. Create a namespace for ArgoCD:
    ```bash
    kubectl create ns argocd
    ```

4. Install ArgoCD:
    ```bash
    kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
    ```

5. Check ArgoCD pods:
    ```bash
    kubectl get pod -n argocd
    ```

6. Check ArgoCD services:
    ```bash
    kubectl get svc -n argocd
    ```

7. Port forward to access ArgoCD dashboard:
    ```bash
    kubectl port-forward -n argocd svc/argocd-server 8080:443
    ```

8. Access ArgoCD dashboard by visiting `http://localhost:8080` in your web browser.

9. Retrieve initial admin password:
    ```bash
    kubectl get secret argocd-initial-admin-secret -n argocd -o yaml
    echo "cIdW8cQWCsLi00Vt" | base64 --decode
    ```

10. Apply application configuration:
    ```bash
    kubectl apply -f application.yaml
    ```

11. Install Helm:
    - **Mac:**
      ```bash
      brew install helm
      ```
    - **Windows:**
      Follow [Helm installation guide](https://helm.sh/docs/intro/install/)
    - **Linux (Ubuntu/RedHat):**
      Follow [Helm installation guide](https://helm.sh/docs/intro/install/)

12. Add ArgoCD Helm repository and update:
    ```bash
    helm repo add argo https://argoproj.github.io/argo-helm
    helm repo update
    ```

## Note

- Default username for ArgoCD dashboard is `admin`.
- Retrieve the password using the secret `argocd-initial-admin-secret`.

