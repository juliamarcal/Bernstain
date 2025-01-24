# Bernstein
# Project Overview: Kubernetes-Orchestrated Web Poll Application

This project involves deploying a **simple web poll application** to a **multi-host Kubernetes cluster**. The application showcases Kubernetes' capabilities in managing containerized applications, emphasizing **scalability, automation**, and **load balancing**.

Find out more information about the project at [Project PDF](./B-DOP-500_bernstein.pdf)

## Core Components

The application consists of **five interconnected services**:

1. **Poll**:
   - **Technology**: Flask (Python).
   - **Purpose**: A web interface that collects votes from users.
   - **Operation**: Sends the collected votes to the Redis queue for processing.

2. **Redis Queue**:
   - **Technology**: Redis (In-memory data structure store).
   - **Purpose**: Acts as a buffer, temporarily holding the votes received from the Poll service.
   - **Operation**: Waits for the Worker service to consume the votes.

3. **Worker**:
   - **Technology**: Java application.
   - **Purpose**: Processes the votes from the Redis queue.
   - **Operation**: Consumes votes and stores them in a persistent PostgreSQL database.

4. **PostgreSQL Database**:
   - **Technology**: PostgreSQL (Relational Database).
   - **Purpose**: Stores the votes persistently.
   - **Operation**: Serves as the data source for the Result application.

5. **Result**:
   - **Technology**: Node.js.
   - **Purpose**: A web interface displaying the voting results.
   - **Operation**: Fetches results from the PostgreSQL database.

## Kubernetes Features Used

- **Multi-host Cluster**: Enables the deployment of components across multiple nodes for high availability.
- **Traefik**:
  - Acts as a **reverse proxy** to route traffic to appropriate services.
  - Functions as a **load balancer** to distribute traffic evenly across multiple instances of a service.
- **Containerization**:
  - Each service is containerized, ensuring portability and scalability.
  - Kubernetes manages these containers with Pods, Deployments, and Services.
- **Monitoring**:
  - Use of tools like **cAdvisor** to monitor resource usage and performance.
- **Configuration Management**:
  - **ConfigMaps** store environment variables for non-sensitive data.
  - **Secrets** manage sensitive information like database credentials securely.

## Objectives

1. **Deploy the Application**: Set up all five services on Kubernetes with proper inter-service communication.
2. **Implement Load Balancing**: Use Traefik to distribute traffic evenly.
3. **Ensure Scalability**: Configure the cluster to handle increased loads by scaling services as needed.
4. **Maintain Persistence**: Use PostgreSQL to ensure votes are stored and retrievable even after restarts.
5. **Monitor and Debug**: Leverage Kubernetes' tools and cAdvisor for maintaining a healthy application.

## Outcome

The final product will be a fully functional, containerized web poll application, deployed and managed through Kubernetes. It will demonstrate best practices in container orchestration, scalability, and reliability, leveraging the power of Traefik and Kubernetes features.

## Group:
 - Júlia Bomfá
 - Gleb Mikheev
 - Erwann Wicart

