
# Centralized Log Management System

<img width="1259" alt="elastic_stack_dashboard" src="https://github.com/george-mountain/Centralized-Log-Management/assets/19597087/7a2e9686-0b14-4867-bd4d-a67dbab4b289">


This repository showcases how to centralize and manage logs from microservice applications using the Elastic Stack (Logstash, Elasticsearch, and Kibana) and Loguru for logging within a FastAPI app.

## Project Overview

This project is designed for a school management system comprising multiple microservices:

- **Students App**
- **Library Management App**
- **Faculty App**

Each of these microservices can operate independently but are currently integrated using a common API gateway. We use Loguru for logging and the Elastic Stack for centralized log management.

## Key Components

### FastAPI App
The FastAPI app serves as the core of the school management system, integrating the various microservices.

### Elastic Stack
- **Logstash:** Collects and processes logs from the FastAPI app.
- **Elasticsearch:** Stores and indexes logs for efficient searching and analysis.
- **Kibana:** Provides a web interface for visualizing and exploring logs.

### Docker
All applications, including the Elastic Stack, are dockerized for easy deployment and management.

## Prerequisites

To run this project, you need to have Docker installed on your machine.

## Getting Started

### 1. Fork or clone the Repository

```sh
git clone https://github.com/george-mountain/Centralized-Log-Management.git
cd centralized-log-management
```

### 2. Create a `.env` File

Create a `.env` file in the root directory of the project and configure it as shown in the `env-sample` file provided in the repository.

### 3. Update the `.env` File

Your `.env` file should look like this:

```env
ELASTIC_PASSWORD=YOURELASTICPASSWORDHERE #e.g elastic1234
ELASTICSEARCH_USERNAME=YOURELASTICUSERNAMEHERE #e.g elastic
ELASTICSEARCH_PASSWORD=YOURELASTICSEARCHPASSWORDHERE #e.g elastic1234
```

### 4. Run the Application

Use Docker Compose to start all services:

```sh
docker-compose up --build 
```

This command will start the FastAPI app, Logstash, Elasticsearch, and Kibana.

## Configuration

### Docker Compose

The `docker-compose.yml` file is configured to:

- Start the Elasticsearch container with security enabled.
- Start the Logstash container to collect logs from the FastAPI app.
- Start the Kibana container to visualize logs.
- Start the FastAPI app for the school management system.

### Logstash Configuration

The Logstash configuration file `logstash.conf` uses environment variables for credentials, ensuring sensitive information is not hard-coded.

### Environment Variables

Environment variables for credentials are stored in the `.env` file, ensuring they are securely managed and can be easily changed without modifying the codebase.

## Accessing Services

### FastAPI App
The FastAPI app will be available at `http://localhost:8000`.

The fastapi endpoints are:

http://localhost:8000/docs#/ --- This is the central application endpoint documentation

http://localhost:8000/school-management/student/docs#/  --- This is the student app endpoints documentation

http://localhost:8000/school-management/library/docs#/  --- This is the library app endpoints documentation

http://localhost:8000/school-management/faculty/docs#/  --- This is the faculty app endpoints documentation.


### Kibana
Kibana will be available at `http://localhost:5601`. Use the credentials configured in your `.env` file to log in.
Note: When you access the above url, you will be promted to login. Use the username and password which you configured
on the .env file for the elastic stack.

### Elasticsearch
Elasticsearch will be available at `http://localhost:9200`. Use the credentials configured in your `.env` file to access it.


For any questions or issues, please open an issue in the repository

