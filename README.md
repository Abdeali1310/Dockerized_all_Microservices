# Dockerized Flight Project

Welcome to the Dockerized Flight Project! This repository provides a Dockerized setup for a microservices-based flight booking system. It includes several microservices along with an API gateway, all orchestrated using Docker Compose.

## Project Overview

This project demonstrates a microservices architecture for a flight booking system. It consists of the following components:

- **API-Gateway:** Routes incoming requests to the appropriate microservices.
- **Flight-Service:** Manages flight data and operations.
- **Flight-Booking-Service:** Handles flight bookings and reservations.
- **Notification-Service:** Sends notifications to users regarding flight status, bookings, etc.

## Prerequisites

Before you start, ensure you have the following installed:

- [Docker](https://docs.docker.com/get-docker/) (v20.10 or later)
- [Docker Compose](https://docs.docker.com/compose/install/) (v1.27 or later)

## Setup Instructions

### 1. Clone the Repository

Clone this repository to your local machine using:

bash
git clone https://github.com/your-username/Dockerized_Flight_Project.git
cd Dockerized_Flight_Project

## 2. Create the Docker Network
The Docker Compose configuration requires a network bridge named "micro-net". Create this network with the following command:

docker network create --driver bridge micro-net

## 3. Build and Start the Services
From the root directory of the project (where the docker-compose.yml file is located), run:

docker compose up -d

This command builds the Docker images and starts the containers in detached mode.

## 4. Configuration Details
Network Bridge: micro-net is used for communication between the containers.

Volumes: Persistent volumes for node_modules to manage dependencies:

api_gateway_node_modules
flight_service_node_modules
flight_booking_service_node_modules
flight_notification_node_modules

Bind Mounts: Reflect local code changes inside the containers:

./API-Gateway:/developer/flights_api_gateway
./Flight-service:/developer/flights_service
./flight-booking-service:/developer/flights_booking_service
./Notification-service:/developer/flights_noti_service

## 5. Accessing the Services
After starting the services, you can access them via the following URLs:

API Gateway: http://localhost:5000
Flight Service: http://localhost:3000
Flight Booking Service: http://localhost:4000
Notification Service: http://localhost:6000

## 6. Stopping and Removing Containers
To stop and remove all containers, networks, and volumes created by Docker Compose, use:

docker compose down

## 7. Troubleshooting
Network Issues: Verify that the micro-net network bridge is created and that all containers are connected.

Logs: To view logs for a specific service:

docker compose logs <service-name>

Replace <service-name> with the name of the service (e.g., api-gateway).

## 8. Contributing
Contributions are welcome! If you have suggestions or improvements, please submit a pull request. Ensure your changes adhere to the project's coding standards and include relevant tests.

## 9. License
This project is licensed under the MIT License.
