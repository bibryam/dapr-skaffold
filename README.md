# Dapr Skaffold Example

## Overview
This example demonstrates how to deploy a Dapr-enabled application using Skaffold.

## Prerequisites

### Install Skaffold
To install Skaffold, use the following command:
```bash
brew install skaffold
```

### Install Redis
Install Redis using Helm:
```bash
helm repo add bitnami https://charts.bitnami.com/bitnami
helm repo update
helm install redis bitnami/redis --set cluster.enabled=false --set replica.replicaCount=0 --set fullnameOverride=dapr-dev-redis
```

## Build the Application
This application comprises a Python app that generates messages and a Node app that stores these messages in a Redis state store. Follow these steps to deploy both applications:

Clone the repository:
```bash
   git clone git@github.com:bibryam/dapr-skaffold.git
   cd dapr-skaffold
```

Build the Java applications in their respective directories:
```bash
   mvn clean install
 ```

## Deployment
To deploy the application, run the following command:
```bash
skaffold dev
```

## Sync Changes
Update the application YAML files or change the code in the Java files. After building the application, the changes will be detected and redeployed automatically.
