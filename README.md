# WordPress Deployment on Kubernetes

This repository contains Kubernetes manifests for deploying WordPress
with MySQL as the database backend.

## Prerequisites

Before you begin, ensure you have the following installed/configured:

-   Kubernetes cluster (minikube, Docker Desktop Kubernetes, or a cloud
    provider)

-   kubectl CLI configured to communicate with your cluster

## Components

### MySQL Deployment

-   **Service**: Exposes MySQL database within the cluster.

-   **StatefulSet**: Manages the MySQL instance with persistent storage.

-   **PersistentVolumeClaim**: Claims storage for MySQL data.

-   **Secret**: Stores MySQL credentials securely.

### WordPress Deployment

-   **Service**: Exposes WordPress application to the outside world.

-   **Deployment**: Manages the WordPress application container.

-   **PersistentVolumeClaim**: Claims storage for WordPress files.

## Setup

1.  **Clone the Repository:**

bash

Copy code

git clone \https://github.com/samundra77/wordpress-deployment.git

cd /wordpress-deployment

2.  **Deploy MySQL:**

bash

Copy code

kubectl apply -f mysql.yaml

This will deploy MySQL with persistent storage and create the necessary
services and secrets.

3.  **Deploy WordPress:**

bash

Copy code

kubectl apply -f deployment.yaml

This will deploy WordPress configured to connect to the MySQL database.

## Accessing WordPress

1.  **Find WordPress Service External IP:**

After applying the deployment manifests, wait for the LoadBalancer type
service to provision an external IP address. You can check using:

bash

Copy code

kubectl get svc wordpress

Look for the EXTERNAL-IP under STATUS.

2.  **Access WordPress:**

Open a web browser and enter the EXTERNAL-IP followed by port 3000 (as
per the service configuration). For example:

Copy code

http://\<EXTERNAL-IP\>:3000

3.  **WordPress Setup:**

Complete the WordPress installation using the web interface, providing
the MySQL database connection details (host, database name, username,
password).

## Notes

-   **Persistence**: MySQL and WordPress both use PersistentVolumeClaims
    for data storage, ensuring data persistence across pod restarts.

-   **Security**: Secrets are used to store sensitive information like
    database credentials.

-   **Scalability**: This setup is basic and suitable for testing or
    small-scale usage. For production, consider scaling MySQL and
    WordPress accordingly.
