# BestBuy Store
Welcome to the BestBuy Store application.

This sample demo app consists of a group of containerized microservices that can be easily deployed into a Kubernetes cluster. This is meant to show a realistic scenario using a polyglot architecture, event-driven design, and common open source back-end services (eg - RabbitMQ, MongoDB). The application also leverages OpenAI's models to generate product descriptions and images. This can be done using either [Azure OpenAI](https://learn.microsoft.com/azure/ai-services/openai/overview) or [OpenAI](https://openai.com/).


> [!NOTE]
> This is not meant to be an example of perfect code to be used in production, but more about showing a realistic application running in kubernetes. 

## Architecture

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



