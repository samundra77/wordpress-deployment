# WordPress and MySQL Deployment on Kubernetes
 
This repository contains Kubernetes manifests to deploy WordPress and MySQL with PersistentVolumeClaims (PVCs) and Services.
 
## Prerequisites
 
- A Kubernetes cluster
- `kubectl` configured to access your Kubernetes cluster
 
## Deployment
 
1. **Clone the Repository:**
 
    ```sh
    git clone https://github.com/samundra77/wordpress-deployment.git
    cd your-repository
    ```
 
2. **Deploy MySQL:**
 
    Apply the MySQL manifest:
 
    ```sh
    kubectl apply -f mysql.yaml
    ```
 
3. **Deploy WordPress:**
 
    Apply the WordPress manifest:
 
    ```sh
    kubectl apply -f deployment.yaml
    ```
 
## Accessing WordPress
 
Once deployed, WordPress can be accessed using the external IP of the LoadBalancer service on port `3000`. You can get the external IP by running:
 
```sh
kubectl get services


