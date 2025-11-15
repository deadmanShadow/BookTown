# Booktown Microservice Project

## Introduction

Microservices have become a modern architectural approach due to the modularity, independence, and flexibility they provide. They enable large systems to be developed, scaled, and deployed continuously. Despite the abundance of educational resources available, applying these concepts directly to real-world scenarios can still be challenging.

This demo application was created to illustrate how microservices are structured, how they interact, and how various architectural patterns and best practices can be applied in practice.

## General Overview

Selecting the right domain is essential. Simple examples like to-do applications or basic CRUD systems are too limited to reflect the true value of microservices. An eCommerce system, on the other hand, includes a diverse set of well-understood entities and services.

A book store domain is therefore a suitable choice for demonstrating microservice concepts.

Following the principles of clean architecture, this project includes several independent services:

* [Ocelot API Gateway](Src/APIGateway/README.md)
* [Identity Service](Src/Services/Identity/README.md)
* [Orders Service](Src/Services/Orders/README.md)
* [Catalog Service](Src/Services/Catalog/README.md)
* [Basket Service](Src/Services/Basket/README.md)
* [Ratings Service](Src/Services/Ratings/README.md)
* [Payments Service](Src/Services/Payments/README.md)
* [Inventory Service](Src/Services/Inventory/README.md)
* [PriceCalculator Service](Src/Services/PriceCalculator/README.md)
* [RatingsAccumulator Service](Src/Services/RatingsAccumulator/README.md)
* Basket BFF
* Order BFF

Each service uses the most suitable type of data storage, whether relational or NoSQL. Technologies include:

* Postgres
* Redis
* MongoDB
* ElasticSearch
* Neo4j

For asynchronous communication, the system uses a service bus with the CQRS pattern alongside MediatR, FluentValidation, and AutoMapper. Masstransit with RabbitMQ is used as the message broker.

An API Gateway built with Ocelot protects the internal network. Additionally, a BFF layer is included to demonstrate synchronous service aggregation and the use of gRPC.

Monitoring and observability are incorporated through logging, metrics, tracing, and health checks.

Since the system has many moving parts, orchestration patterns such as Saga are also considered.

Testing is an essential requirement, and xUnit is used for unit and integration tests.

All microservices are containerized and can be run locally via Docker Compose or deployed to a local Kubernetes cluster.

The implementation is based on C# and ASP.NET Core 6.

A frontend or mobile client is intentionally excluded to maintain focus on backend architecture. Contributions or ideas for user-facing applications are welcome.

## Architectural Overview

This application is fully cross-platform thanks to .NET 6, allowing services to run inside Linux or Windows containers depending on the Docker host.

The architecture follows a microservice-oriented design with multiple autonomous services, each maintaining ownership of its own data. Different architectural styles—ranging from simple CRUD to DDD with CQRS—are applied based on the requirements of each domain area.

The system uses HTTP for communication between client applications and microservices, and asynchronous integration events are propagated through a Masstransit event bus backed by RabbitMQ or Kafka.

![Architecture](img/Booktown-architecture.png)

This project is not intended for production use, but rather as an educational showcase of architectural practices, patterns, and technologies. Suggestions and improvements are always welcome.
