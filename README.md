WordPress Deployment Guide
This guide outlines the steps to deploy WordPress on Kubernetes using YAML manifests. The deployment includes WordPress itself along with a MySQL database backend.

Prerequisites
Before you begin, ensure you have the following:

Kubernetes cluster configured and access to deploy resources.
kubectl command-line tool installed and configured to manage your Kubernetes cluster.
Deployment Steps

Step 1: Deploy MySQL
First, deploy MySQL using the following manifest (mysql.yaml):

yaml
Copy code
<MySQL YAML content>
Apply the MySQL manifest:

bash
Copy code
kubectl apply -f mysql.yaml
Step 2: Deploy WordPress
Next, deploy WordPress using the following manifest (deployment.yaml):

yaml
Copy code
<WordPress YAML content>
Apply the WordPress manifest:

bash
Copy code
kubectl apply -f deployment.yaml

Step 3: Access WordPress
Wait for the deployments to be ready. Retrieve the external IP address assigned to the WordPress service:

bash
Copy code
kubectl get svc wordpress
Access WordPress using a web browser by navigating to http://<EXTERNAL_IP>:3000.

Step 4: Configuration
WordPress Setup: Follow the on-screen instructions to complete the WordPress setup.

Database Configuration: Use the following details during WordPress setup:

Database Name: wordpress
Database User: admin (as per the configuration)
Database Password: Use the MySQL password stored in the mysql-secrets secret.

Step 5: Cleanup (Optional)
To delete the deployments and associated resources:

bash
Copy code
kubectl delete deployment wordpress
kubectl delete svc wordpress
kubectl delete pvc wp-pv-claim
bash
Copy codeWordPress Deployment Guide
This guide outlines the steps to deploy WordPress on Kubernetes using YAML manifests. The deployment includes WordPress itself along with a MySQL database backend.

Prerequisites
Before you begin, ensure you have the following:

Kubernetes cluster configured and access to deploy resources.
kubectl command-line tool installed and configured to manage your Kubernetes cluster.
Deployment Steps

Step 1: Deploy MySQL
First, deploy MySQL using the following manifest (mysql.yaml):

yaml
Copy code
<MySQL YAML content>
Apply the MySQL manifest:

bash
Copy code
kubectl apply -f mysql.yaml
Step 2: Deploy WordPress
Next, deploy WordPress using the following manifest (deployment.yaml):

yaml
Copy code
<WordPress YAML content>
Apply the WordPress manifest:

bash
Copy code
kubectl apply -f deployment.yaml

Step 3: Access WordPress
Wait for the deployments to be ready. Retrieve the external IP address assigned to the WordPress service:

bash
Copy code
kubectl get svc wordpress
Access WordPress using a web browser by navigating to http://<EXTERNAL_IP>:3000.

Step 4: Configuration
WordPress Setup: Follow the on-screen instructions to complete the WordPress setup.

Database Configuration: Use the following details during WordPress setup:

Database Name: wordpress
Database User: admin (as per the configuration)
Database Password: Use the MySQL password stored in the mysql-secrets secret.

Step 5: Cleanup (Optional)
To delete the deployments and associated resources:

bash
Copy code
kubectl delete deployment wordpress
kubectl delete svc wordpress
kubectl delete pvc wp-pv-claim
bash
Copy code
kubectl delete statefulset mysql-statefulset
kubectl delete svc mysql-service
kubectl delete pvc mysql-pvc
kubectl delete secret mysql-secrets

Additional Notes
Persistence: PersistentVolumeClaims (PVCs) are used for both MySQL and WordPress to ensure data persistence.
Secrets Management: MySQL passwords are stored securely in Kubernetes secrets (mysql-secrets).
Load Balancing: WordPress service is configured as type LoadBalancer with port 3000 mapped to port 80 of the WordPress container.

Adjust the <MySQL YAML content> and <WordPress YAML content> placeholders with the actual content from  mysql.yaml and deployment.yaml files respectively.


kubectl delete statefulset mysql-statefulset
kubectl delete svc mysql-service
kubectl delete pvc mysql-pvc
kubectl delete secret mysql-secrets

Additional Notes
Persistence: PersistentVolumeClaims (PVCs) are used for both MySQL and WordPress to ensure data persistence.
Secrets Management: MySQL passwords are stored securely in Kubernetes secrets (mysql-secrets).
Load Balancing: WordPress service is configured as type LoadBalancer with port 3000 mapped to port 80 of the WordPress container.

Adjust the <MySQL YAML content> and <WordPress YAML content> placeholders with the actual content from  mysql.yaml and deployment.yaml files respectively.

