# Softy Pinko Docker Project

## Overview

This project demonstrates containerization, service communication, reverse proxying, and horizontal scaling using Docker, Docker Compose, Flask, and Nginx.

The project is divided into several tasks that gradually build a complete containerized application.

---

# Task 0 - Docker Basics

## Objective

Create and run a basic Docker container using Ubuntu.

## Concepts

* Docker images
* Docker containers
* Dockerfile
* Image building

---

# Task 1 - Back-End Service

## Objective

Create a Flask API running inside a Docker container.

## Endpoint

```text
/api/hello
```

## Response

```json
{
  "message": "Hello, World!"
}
```

## Technologies

* Python
* Flask
* Docker

---

# Task 2 - Front-End Service

## Objective

Containerize the Softy Pinko front-end using Nginx.

## Features

* Static website hosting
* Nginx web server
* Independent container

## Ports

```text
9000:9000
```

---

# Task 3 - Connect Front-End and Back-End

## Objective

Allow the front-end to retrieve data from the Flask API.

## Features

* AJAX requests
* Flask-CORS support
* Dynamic content rendering

## Communication Flow

```text
Browser
   ↓
Front-End
   ↓
Back-End API
```

---

# Task 4 - Docker Compose

## Objective

Manage multiple services using Docker Compose.

## Services

* back-end
* front-end

## Benefits

* Single command deployment
* Shared network
* Simplified management

## Command

```bash
docker compose up
```

---

# Task 5 - Reverse Proxy

## Objective

Add an Nginx reverse proxy in front of the application.

## Architecture

```text
Client
   ↓
Proxy (Nginx)
   ↓
 ┌─────────────┬─────────────┐
 ↓             ↓
Front-End    Back-End
```

## Routing

### Static Content

```text
/
```

Forwarded to:

```text
front-end
```

### API Requests

```text
/ api / hello
```

Forwarded to:

```text
back-end
```

---

# Task 6 - Horizontal Scaling

## Objective

Scale the API service horizontally and distribute traffic between multiple back-end containers.

## Command

```bash
docker-compose up --scale back-end=2
```

## Architecture

```text
Client
   ↓
Proxy (Nginx)
   ↓
 ┌─────────────┬─────────────┐
 ↓             ↓
Back-End 1   Back-End 2
```

## Load Balancing

Nginx automatically uses the Round-Robin algorithm.

Example:

```text
Request 1 → back-end-1
Request 2 → back-end-2
Request 3 → back-end-1
Request 4 → back-end-2
```

## Verification

Reload the page multiple times and observe requests alternating between:

```text
back-end-1
back-end-2
```

---

# Technologies Used

* Docker
* Docker Compose
* Python
* Flask
* Flask-CORS
* Nginx
* HTML
* CSS
* JavaScript

---

# Project Structure

```text
holbertonschool-softy-pinko-docker/
│
├── task0/
├── task1/
├── task2/
├── task3/
├── task4/
├── task5/
└── task6/
```

---

# Learning Outcomes

By completing this project, the following concepts were practiced:

* Building Docker images
* Running containers
* Container networking
* Service communication
* Reverse proxy configuration
* Docker Compose orchestration
* Horizontal scaling
* Nginx load balancing
* Microservice architecture fundamentals
