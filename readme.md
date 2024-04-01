## Kubernetes Operations

1. **Apply Changes**:
   - Apply changes specified in `application.yaml` to the Kubernetes cluster:
     ```
     kubectl apply -f application.yaml
     ```

2. **View Cluster Status**:
   - Check the status of rollouts in the cluster:
     ```
     kubectl get rollout
     ```
   - View all namespaces in the cluster:
     ```
     kubectl get ns
     ```
   - View all pods in the cluster:
     ```
     kubectl get pods
     ```

3. **Namespace Management**:
   - Delete the `argocd` namespace:
     ```
     kubectl delete ns argocd
     ```

## Additional Operations

1. **Helm Repository Management**:
   - Add Argo Helm repository:
     ```
     helm repo add argo https://argoproj.github.io/argo-helm
     ```
   - Update Helm repositories:
     ```
     helm repo update
     ```

2. **Modify and Push Changes**:
   - Modify `dev/deployment-1.yaml` using a text editor:
     ```
     vi dev/deployment-1.yaml
     ```
   - Stage changes for commit:
     ```
     git add .
     ```
   - Commit changes with a message:
     ```
     git commit -m "deployment-1 v1.1 updated"
     ```
   - Push changes to the remote repository:
     ```
     git push -u origin main
     ```





