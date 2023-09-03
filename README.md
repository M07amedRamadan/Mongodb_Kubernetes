# Mongodb_Kubernetes

This repository contains Kubernetes configuration files for deploying MongoDB and Mongo Express using Kubernetes. These configuration files are used to define the resources needed to deploy MongoDB as well as Mongo Express for database management.

## Deployment Configuration

### MongoDB Deployment

- **File**: `mongodb.yml`
- **Description**: Defines a Kubernetes Deployment for MongoDB.
- **Specifications**:
  - MongoDB Docker image: `mongo`
  - Resource limits: 128Mi memory, 500m CPU
  - Exposes port 27017
  - Uses a secret for MongoDB root username and password

### Mongo Express Deployment

- **File**: `mongo-express.yml`
- **Description**: Defines a Kubernetes Deployment for Mongo Express.
- **Specifications**:
  - Mongo Express Docker image: `mongo-express`
  - Exposes port 8081
  - Uses environment variables for MongoDB admin credentials (from a secret)
  - Uses a config map for the MongoDB server URL

## Service Configuration

### MongoDB Service

- **File**: `mongodb-service.yml`
- **Description**: Defines a Kubernetes Service for exposing the MongoDB Deployment.
- **Specifications**:
  - Type: LoadBalancer
  - Exposes port 8081 externally (via LoadBalancer)
  - Maps to port 8081 internally
  - Uses a nodePort (port 30000) for external access

### Mongo Express Service

- **File**: `mongo-express-service.yml`
- **Description**: (Not provided in the original files but can be added for Mongo Express if needed)

## ConfigMap and Secret Configuration

### MongoDB ConfigMap

- **File**: `mongodb-configmap.yml`
- **Description**: Defines a Kubernetes ConfigMap for storing the MongoDB server URL.

### MongoDB Secret

- **File**: `mongodb-secret.yml`
- **Description**: Defines a Kubernetes Secret for storing the MongoDB root username and password.

## Getting Started

To use these Kubernetes configuration files, follow these steps:

1. Make sure you have a running Kubernetes cluster.
2. Ensure that the required Docker images (mongo and mongo-express) are accessible from your cluster.
3. Create the necessary ConfigMap and Secret resources.
4. Apply the provided YAML files using the `kubectl apply -f <filename>.yml` command.
5. Make sure that you run the kubectl command with ConfigMap and Secret Configuration files firstly.

You can customize these configuration files to suit your specific needs, such as adjusting resource limits, passwords, or other settings.

Feel free to reach out if you have any questions or encounter issues while deploying MongoDB and Mongo Express using these configuration files.
