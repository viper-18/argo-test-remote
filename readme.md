# Approach, Challenges, and Solutions

## Approach

Our approach to solving the assignment involved a combination of Git and Kubernetes operations to manage application deployments and configurations. We utilized Git for version control and managing changes to configuration files, while Kubernetes was used for orchestrating containerized applications.

## Challenges

### Lack of Helm Installation
- **Challenge**: Initially, Helm was not installed in the environment, preventing us from using Helm charts for managing Kubernetes applications.
- **Solution**: We addressed this challenge by installing Helm using Homebrew package manager.

### Namespace Deletion Error
- **Challenge**: An error occurred while trying to delete the `argocd` namespace, possibly due to existing resources or permissions issues.
- **Solution**: We successfully deleted the namespace after identifying and resolving the underlying issue.

### Command Execution Errors
- **Challenge**: Some commands, such as `kubectl get rollout`, resulted in errors indicating that the server didn't recognize the resource type.
- **Solution**: We adjusted our approach and used alternative commands (`kubectl get pods`) to gather relevant information about the cluster status.


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





