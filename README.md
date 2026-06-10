## Visualpathit VProfile Webapp

A Java-based web application for profile management, built with Spring MVC, Spring Security, Spring Data JPA, Hibernate, and Jakarta EE technologies.

## Overview

This repository contains the `vprofile` web application packaged as a WAR file for deployment to a Java application server. The app includes:

- User authentication and authorization
- Profile management and user registration
- MySQL database persistence
- RabbitMQ messaging support
- Elasticsearch integration
- File upload support
- UI views in JSP with Bootstrap and custom styling

## Key Features

- Spring MVC-based web interface
- Spring Security configuration for login and access control
- JPA persistence with Hibernate and MySQL
- RabbitMQ messaging integration
- Elasticsearch REST client support
- Docker build support using multi-stage Dockerfile
- CI/CD pipeline with GitHub Actions, SonarQube, and ECR image publishing

## Technologies

- Java 17
- Maven
- Spring Framework 6
- Spring Security 6
- Spring Data JPA 3
- Hibernate 7
- Jakarta Servlet API
- MySQL Connector/J
- RabbitMQ / Spring AMQP
- Elasticsearch Java REST client
- Logback and Log4j
- JSP + Bootstrap frontend

## Repository Structure

- `src/main/java` - application source code
- `src/main/resources` - application resources and configuration
- `src/main/webapp` - web resources, JSP views, static assets, and `WEB-INF` configuration
- `Docker-files` - Dockerfiles for app, web, and database images
- `ci.yml` - GitHub Actions workflow for build, test, SonarQube, and Docker publishing

## Build

To build the project locally:

```bash
mvn clean package
```

The build produces a WAR file under `target/`.

## Run

This application is packaged as a WAR and should be deployed to a compatible servlet container such as Tomcat or a Jakarta EE application server.

Alternatively, use the provided Docker build:

```bash
docker build --file Docker-files/app/multistage/Dockerfile --tag vprofile-app:latest .
```

## Configuration

Application settings can be found in `src/main/resources/application.properties`.

Database initialization and schema resources are available in:

- `src/main/resources/accountsdb.sql`
- `src/main/resources/db_backup.sql`

The web application is configured in `src/main/webapp/WEB-INF/web.xml` and Spring context files under `WEB-INF`.

## CI/CD

The `ci.yml` workflow runs on GitHub Actions and includes:

- Maven build, unit tests, and Checkstyle
- SonarQube scan and quality gate verification
- Docker image build and push to AWS ECR on `push` events
- Helm values update in a separate Helm repository

## Notes

- Ensure required secrets and variables are available for GitHub Actions: `SONAR_TOKEN`, `AWS_ACCESS_KEY_ID`, `AWS_SECRET_ACCESS_KEY`, `HELM_REPO_USER`, `GITOPS_PAT`.
- `AWS_REGION`, `ECR_REPOSITORY`, `HELM_REPO_NAME`, and `SONAR_HOST_URL` are supplied via repository variables.

##### completed
