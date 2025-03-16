# Taskify-Config Repository

This repository contains centralized configuration for all Taskify microservices.

## File Structure

```
/
├── application.yml       # Shared configurations for all services
├── auth-service.yml      # Auth service configurations
├── iam-service.yml       # IAM service configurations
├── organization-service.yml  # Organization service configurations
└── api-gateway.yml       # API Gateway configurations
```

## Usage

This repository is used by the Spring Cloud Config Server to provide centralized configuration to all microservices. Each service should have its own configuration file named `<service-name>.yml`.

To use this repository, set the following properties in your Config Server application:

```yaml
spring:
  cloud:
    config:
      server:
        git:
          uri: https://github.com/your-org/taskify-config.git
          default-label: main
          search-paths: /
```

## Important Notes

- Sensitive configuration like passwords and secrets should be externalized using environment variables or a secret management service in production.
- Local development can use the `native` profile to reference local files instead of Git.
