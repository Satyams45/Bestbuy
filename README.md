# Best Buy Cloud-Native App

## Updated Application Architecture

![Architecture Diagram](FinalAssignment-1.png)

## Application and Architecture Explanation

This application is a cloud-native implementation of a **Best Buy website**, consisting of multiple microservices for managing storefront interactions, orders, products, and more. Each microservice performs a specific role within the architecture:

- **store-front**: The customer-facing web application built with Vue.js.
- **store-admin**: The administrative web application for managing orders and products, built with Vue.js.
- **order-service**: Handles order placement and queuing using RabbitMQ.
- **product-service**: Manages product CRUD operations with Rust.
- **makeline-service**: Processes orders from the queue and marks them complete.
- **ai-service**: Provides generative AI functionality for text and graphics.
- **rabbitmq**: Acts as the message broker for order queues.
- **mongodb**: Stores persistent application data.

The architecture leverages Kubernetes for container orchestration, ensuring scalability, resilience, and efficient resource utilization.

## Deployment Instructions

Follow these steps to deploy each of these containerized microservices in a Kubernetes cluster:

1. **Clone the repository**:
   ```bash
   git clone <repository-url>
   cd <repository-name>
   ```

2. **Set up your Kubernetes cluster**:
   - Use Azure Kubernetes Service (AKS) to create one master node and two worker nodes to run the containers on.

3. **Apply the deployment files**:
   ```bash
   kubectl apply -f Deployment_Files/
   ```

4. **Verify the deployment**:
   ```bash
   kubectl get pods
   kubectl get services
   ```

5. **Access the application**:
   - Use the `EXTERNAL-IP` of the **store-front** service to access the customer-facing application.
   - Use the `EXTERNAL-IP` of the **store-admin** service to access the admin dashboard.

6. **Optional**: Monitor logs for debugging:
   ```bash
   kubectl logs -f <pod-name>
   ```

## Table of Microservice Repositories

| Service          | Repository Link        |
|------------------|------------------------|
| Store-Front      | [store-front](https://github.com/ngugi-james/store-front-a2)       |
| Store-Admin      | [store-admin](https://github.com/ngugi-james/store-admin-a2)       |
| Order-Service    | [order-service](https://github.com/ngugi-james/order-service-a2)       |
| Product-Service  | [product-service](https://github.com/ngugi-james/product-service-a2)       |
| Makeline-Service | [makeline-service](https://github.com/ngugi-james/makeline-service-a2)       |
| AI-Service       | [ai-service](https://github.com/ngugi-james/ai-service-a2)       |

## Table of Docker Images

| Service          | Docker Image Link      |
|------------------|------------------------|
| Store-Front      | [store-front](https://hub.docker.com/r/jamesngugi/store-front-a2)   |
| Store-Admin      | [store-admin](https://hub.docker.com/r/jamesngugi/store-admin-a2)   |
| Order-Service    | [order-service](https://hub.docker.com/r/jamesngugi/order-service-a2)   |
| Product-Service  | [product-service](https://hub.docker.com/r/jamesngugi/product-service-a2)   |
| Makeline-Service | [makeline-service](https://hub.docker.com/r/jamesngugi/makeline-service-a2)   |
| AI-Service       | [ai-service](https://hub.docker.com/r/jamesngugi/ai-service-a2)   |


## Deployment Files

All Kubernetes deployment YAML files are located in the `Deployment_Files` folder:

- `store-front-deployment.yaml`
- `store-admin-deployment.yaml`
- `order-service-deployment.yaml`
- `product-service-deployment.yaml`
- `makeline-service-deployment.yaml`
- `ai-service-deployment.yaml`
- `rabbitmq-deployment.yaml`
- `mongodb-deployment.yaml`

---

For any questions or issues, please contact [your contact info].

# Demo Video
Link to Demo Video https://youtu.be/TCvo9jbtJHE 

https://youtu.be/TCvo9jbtJHE 
