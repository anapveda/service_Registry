# Service Registry

This project is a **Spring Boot** application that acts as a **Service Registry** using **Netflix Eureka Server**. It allows different microservices in the system to register themselves and discover other services without needing hardcoded hostnames and ports. This is a central part of a microservices architecture, enabling load balancing and fault tolerance.

---

## Features

* Service discovery and registration with Eureka.
* Centralized registry for all microservices.
* Provides a dashboard to monitor registered services.
* Eliminates the need for hard-coded service URLs.

---

## Tech Stack

* **Java**: 17+ (compatible with 11+ if configured)
* **Spring Boot**: 3.x
* **Spring Cloud Netflix Eureka**: 2023.x
* **Maven**: For build and dependency management

---

## Getting Started

### Prerequisites

Make sure you have installed:

* [Java JDK 17+](https://adoptopenjdk.net/)
* [Maven 3.8+](https://maven.apache.org/)
* (Optional) [Docker](https://www.docker.com/) if containerizing

### Run Locally

1. Clone the repository:

   ```bash
   git clone https://github.com/your-org/service-registry.git
   cd service-registry
   ```

2. Build and run with Maven:

   ```bash
   mvn clean install
   mvn spring-boot:run
   ```

3. The Eureka Dashboard will be available at:
   👉 [http://localhost:8761](http://localhost:8761)

---

## Configuration

Key application properties (`application.properties`):

```properties
spring.application.name=Service-Registry
server.port=8761
eureka.instance.hostname=localhost
eureka.client.register-with-eureka=false
eureka.client.fetch-registry=false
```

* **spring.application.name**: Logical name of the service registry.
* **server.port**: Runs the registry server on port 8761.
* **eureka.client.register-with-eureka**: Disabled because this server should not register itself.
* **eureka.client.fetch-registry**: Disabled because this server does not need to fetch from another registry.

---

## Usage

* Start this service before any other microservices.
* Other microservices must be configured with:

  ```properties
  eureka.client.service-url.defaultZone=http://localhost:8761/eureka/
  ```
* Once microservices are running, check the Eureka Dashboard at `/` to see all registered instances.

---

## Docker Support (Optional)

To build and run with Docker:

```bash
docker build -t service-registry .
docker run -p 8761:8761 service-registry
```

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
