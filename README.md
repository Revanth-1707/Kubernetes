# Kubernetes Commands Cheat Sheet

This document provides a comprehensive list of Kubernetes commands using `kubectl`, categorized for easy reference.

## Table of Contents
- [Basic Commands](#basic-commands)
- [Namespace Management](#namespace-management)
- [Pod Management](#pod-management)
- [Deployment Management](#deployment-management)
- [Service Management](#service-management)
- [ConfigMaps & Secrets](#configmaps--secrets)
- [Persistent Volumes](#persistent-volumes)
- [Node Management](#node-management)
- [Logs & Debugging](#logs--debugging)
- [Scaling & Auto-Scaling](#scaling--auto-scaling)
- [Taints & Tolerations](#taints--tolerations)
- [Role-Based Access Control (RBAC)](#role-based-access-control-rbac)
- [Helm Commands](#helm-commands)

---

## Basic Commands
```sh
kubectl version                 # Check the Kubernetes version
kubectl cluster-info            # View cluster details
kubectl config get-contexts     # List available contexts
kubectl config use-context <name>  # Switch context
kubectl get all                 # List all resources in the current namespace
kubectl get nodes               # List all nodes in the cluster
kubectl config view             # View kubeconfig settings
kubectl config current-context  # Display the current context
kubectl apply -f <file.yaml>    # Apply a configuration file
kubectl delete -f <file.yaml>   # Delete resources from a file
```

## Namespace Management
```sh
kubectl get namespaces          # List all namespaces
kubectl create namespace <name> # Create a new namespace
kubectl delete namespace <name> # Delete a namespace
kubectl config set-context --current --namespace=<name> # Set the default namespace
```

## Pod Management
```sh
kubectl get pods -A             # List all pods across all namespaces
kubectl get pods                # List pods in the current namespace
kubectl describe pod <pod-name> # Get detailed information about a pod
kubectl delete pod <pod-name>   # Delete a specific pod
kubectl exec -it <pod-name> -- /bin/sh # Access a running pod's shell
kubectl run <pod-name> --image=<image> # Create a pod with a specific image
kubectl port-forward pod/<pod-name> 8080:80 # Forward port from pod to local machine
```

## Deployment Management
```sh
kubectl create deployment <name> --image=<image>  # Create a deployment
kubectl get deployments        # List deployments
kubectl delete deployment <name> # Delete a deployment
kubectl rollout restart deployment <name> # Restart a deployment
kubectl rollout status deployment <name> # View rollout status
kubectl rollout undo deployment <name>   # Rollback a deployment
```

## Service Management
```sh
kubectl get svc                # List all services
kubectl expose deployment <name> --type=NodePort --port=80  # Expose a deployment as a service
kubectl delete svc <service-name> # Delete a service
kubectl get endpoints          # View service endpoints
```

## ConfigMaps & Secrets
```sh
kubectl create configmap <name> --from-literal=key=value # Create a ConfigMap
kubectl get configmaps         # List ConfigMaps
kubectl delete configmap <name> # Delete a ConfigMap
kubectl describe configmap <name> # View details of a ConfigMap

kubectl create secret generic <name> --from-literal=key=value # Create a Secret
kubectl get secrets            # List secrets
kubectl delete secret <name>   # Delete a secret
kubectl describe secret <name> # View details of a secret
```

## Persistent Volumes
```sh
kubectl get pv                 # List PersistentVolumes
kubectl get pvc                # List PersistentVolumeClaims
kubectl delete pvc <pvc-name>  # Delete a PersistentVolumeClaim
kubectl describe pv <pv-name>  # View details of a PersistentVolume
kubectl describe pvc <pvc-name> # View details of a PersistentVolumeClaim
```

## Node Management
```sh
kubectl get nodes              # List all nodes
kubectl describe node <node-name> # Get node details
kubectl cordon <node-name>     # Mark a node as unschedulable
kubectl uncordon <node-name>   # Mark a node as schedulable
kubectl drain <node-name>      # Evacuate all pods from a node
```

## Logs & Debugging
```sh
kubectl logs <pod-name>        # View logs for a pod
kubectl logs -f <pod-name>     # Stream logs for a pod
kubectl logs -l name=myLabel   # Dump logs for pods with a specific label
kubectl logs my-pod -c my-container # Dump logs for a specific container in a pod
kubectl logs -l name=myLabel -c my-container # Dump logs for a container in labeled pods
kubectl describe pod <pod-name> # Get detailed pod information
kubectl top pods               # Show resource usage by pods
kubectl top nodes              # Show resource usage by nodes
kubectl debug pod/<pod-name> -it --image=busybox # Debug a pod by attaching a new container
```

## Scaling & Auto-Scaling
```sh
kubectl scale deployment <name> --replicas=<num> # Scale a deployment
kubectl autoscale deployment <name> --min=1 --max=5 --cpu-percent=50 # Set up auto-scaling
```

## Taints & Tolerations
```sh
kubectl taint nodes <node-name> key=value:NoSchedule # Add a taint to a node
kubectl describe node <node-name> # Check taints on a node
kubectl taint nodes <node-name> key=value:NoSchedule- # Remove a taint
```

## Role-Based Access Control (RBAC)
```sh
kubectl create role <role-name> --verb=get --verb=list --resource=pods  # Create a role
kubectl create rolebinding <binding-name> --role=<role-name> --user=<user>  # Bind role to a user
kubectl get roles                # List roles
kubectl get rolebindings          # List role bindings
```

## Helm Commands
```sh
helm repo add <repo-name> <repo-url>  # Add a Helm repository
helm repo update                      # Update Helm repositories
helm install <release-name> <chart>   # Install a Helm chart
helm list                              # List installed releases
helm uninstall <release-name>          # Uninstall a Helm release
```

---
## Conclusion
This document provides a quick reference to essential Kubernetes commands. For more details, refer to the [official Kubernetes documentation](https://kubernetes.io/docs/).

