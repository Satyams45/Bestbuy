# Best Buy Cloud-Native App

## Updated Application Architecture

![Architecture Diagram](https://github.com/user-attachments/assets/050392e8-db37-4a0f-9818-8c743e5f9047)


## Application and Architecture Explanation

### Microservices

**Store-Front**: Customer-facing web app for browsing products and placing orders.

**Store-Admin**: Internal tool for Best Buy employees to manage products and view orders.

**Order-Service**: Handles order placement logic and publishes messages to Azure Service Bus.

**Makeline-Service:** Subscribes to the Azure Service Bus queue and processes orders.

**Product-Service:** Manages product CRUD operations and interacts with MongoDB.

**AI-Service:** Uses GPT-4 to generate product descriptions and DALL-E to generate product images.

### Database

**MongoDB** is used as a document store to persist product and order data.

### AI Integration

**OpenAI GPT-4** is used for generating descriptive product text.

**DALL-E** is used to create AI-generated product images.

### Kubernetes Deployment

Each microservice is deployed in a separate pod.

ConfigMaps and Secrets manage non-sensitive and sensitive configurations.

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
| Store-Front      | [store-front](https://github.com/Satyams45/store-front)       |
| Store-Admin      | [store-admin](https://github.com/Satyams45/store-admin)       |
| Order-Service    | [order-service](https://github.com/Satyams45/order-service)       |
| Product-Service  | [product-service](https://github.com/Satyams45/product-service)       |
| Makeline-Service | [makeline-service](https://github.com/Satyams45/makeline-service)       |
| AI-Service       | [ai-service](https://github.com/Satyams45/ai-service)       |

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
## Bonus Step 
### Continuous Integration/Continuous Deployment (CI/CD) pipeline
![image](https://github.com/user-attachments/assets/15465647-1571-4ea5-8230-206b77a86ab0)

## Known Issues or Limitations
- Insufficient quota and faced problem to deploy Dell-e
- GPT-4 API rate-limits under high load; consider retry logic for production use

# Demo Video
Link to Demo Video 
