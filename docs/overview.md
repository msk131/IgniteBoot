# IgniteBoot Overview

IgniteBoot is a lightweight Java framework designed for strictly regulated banking environments.

## Vision

- Minimal external dependencies
- Java 21 LTS with Virtual Threads
- Hardened HTTP layer, strong security defaults, and observability
- Designed for AOT/GraalVM compilation and zero-CVE posture

## Core Principles

- 100% proprietary runtime layer with optional minimal socket implementation
- Zero-dependency DI via annotation processing or `MethodHandles`
- TLS 1.3 enforced by default
- OAuth2/OIDC JWT validation using JCA/JCE only
- Structured JSON logging and Prometheus-friendly health endpoints

## Mandatory Core Features

The mandatory runtime features are:
- HTTP server and router with method-based handlers
- Security filter chain with OAuth2/JWT, CORS, CSP, secure headers
- Lightweight IoC/DI container with constructor/setter qualifiers and lifecycle callbacks
- Validation engine and request/response body mapping
- Database connection pooling and transaction management over JDBC/HikariCP
- Structured JSON logging, health endpoints, and metrics registry
- Global exception handling and safe error mapping
- Downstream REST client abstraction using `HttpClient`
- Configuration loading from properties and environment variables
