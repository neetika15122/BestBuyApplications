# BestBuy Store
Welcome to the BestBuy Store application.

This sample demo app consists of a group of containerized microservices that can be easily deployed into a Kubernetes cluster. This is meant to show a realistic scenario using a polyglot architecture, event-driven design, and common open source back-end services (eg - RabbitMQ, MongoDB). The application also leverages OpenAI's models to generate product descriptions and images. This can be done using either [Azure OpenAI](https://learn.microsoft.com/azure/ai-services/openai/overview) or [OpenAI](https://openai.com/).

## Lab Objectives
1. Deploy the BestBuy Store application to a Kubernetes cluster.
2. Configure and manage essential Kubernetes resources like StatefulSets, Secrets, ConfigMaps, and Deployments.
3. Test the application's features, including backend services, frontend interfaces, and AI integration.
4. Scale services and monitor application health.
5. Simulate customer and worker tasks using Virtual Customer and Virtual Worker services. 

## Understanding Key Kubernetes Resources: StatefulSets, Deployments, Secrets, and ConfigMaps
In this section, you will learn about essential Kubernetes resources used to deploy and manage applications in a cluster.

### **Deployments**
A **Deployment** is a Kubernetes resource that ensures a specified number of pod replicas are running. It provides mechanisms for rolling updates, scaling, and version management.

#### **Key Features of Deployments**:
1. **Replica Management**:
Ensures a defined number of pod replicas are running at all times.
2. **Rolling Updates**:
Updates pods incrementally to ensure minimal downtime.
3. **Self-healing**:
Automatically replaces failed pods.
#### **Use Cases**:
- Stateless applications like web servers or APIs.
- Backend microservices.

### **StatefulSets**
A **StatefulSet** is a Kubernetes resource used to manage stateful applications. Unlike Deployments, StatefulSets are designed for applications that require unique network identifiers, stable storage, and consistent state across pod restarts.

#### **Key Features of StatefulSets**:
1. **Stable Pod Names**:
   Pods in a StatefulSet have predictable names, such as `pod-name-0`, `pod-name-1`.
2. **Persistent Storage**:
   Each pod can be associated with its own Persistent Volume, ensuring data is retained across restarts.
3. **Ordered Scaling and Updates**:
   Pods are created, updated, and deleted in a controlled order.

#### **Use Cases**:
- Databases like MongoDB, MySQL, or PostgreSQL.
- Message queues like RabbitMQ.

## Step 1: Clone the BestBuyApplication Repository

To begin, clone the [**BestBuyApp**](https://github.com/neetika15122/BestBuyApplications.git) repository, which contains all necessary deployment files.

 **Review the Deployment Files**:
   - Navigate to the `Deployment Files` folder
   - This folder contains YAML files for deploying all necessary Kubernetes resources, including services, deployments, StatefulSets, ConfigMaps, and Secrets.

The application has the following services: 

| Service | Description | Github Repo |
| --- | --- | --- |
| `store-front` | Web app for customers to place orders (Vue.js) | [store-admin-Bestbuy](https://github.com/neetika15122/store-front-Bestbuy.git) |
| `store-admin` | Web app used by store employees to view orders in queue and manage products (Vue.js) | [store-admin-Bestbuy](https://github.com/neetika15122/store-admin-Bestbuy.git) |
| `order-service` | This service is used for placing orders (Javascript) | [order-service-Bestbuy](https://github.com/neetika15122/order-service-Bestbuy.git) |
| `product-service` | This service is used to perform CRUD operations on products (Rust) | [product-service-Bestbuy](https://github.com/neetika15122/product-service-Bestbuy.git) |
| `makeline-service` | This service handles processing orders from the queue and completing them (Golang) | [makeline-service-Bestbuy](https://github.com/neetika15122/makeline-service-Bestbuy.git) |
| `ai-service` | Optional service for adding generative text and graphics creation (Python) | [ai-service-Bestbuy](https://github.com/neetika15122/ai-service-Bestbuy.git) |
| `rabbitmq` | RabbitMQ for an order queue | [rabbitmq](https://github.com/docker-library/rabbitmq) |
| `mongodb` | MongoDB instance for persisted data | [mongodb](https://github.com/docker-library/mongo) |
| `virtual-customer` | Simulates order creation on a scheduled basis (Rust) | [virtual-customer-Bestbuy](https://github.com/neetika15122/virtual-customer-Bestbuy.git) |
| `virtual-worker` | Simulates order completion on a scheduled basis (Rust) | [virtual-worker-Bestbuy](https://github.com/neetika15122/virtual-worker-Bestbuy.git) |


![Logical Application Architecture Diagram](assets/Algonquin%20Pet%20Store%20On%20Steroids.png)

## Run the app on Azure Kubernetes Service (AKS)

You can use the kubernetes YAML files provided in the [Deployment Files](./Deployment%20Files/) folder to deploy the app to an AKS cluster.



