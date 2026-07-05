# IgniteBoot Deployment

## Server Deployment

- Run on an internal, hardened JVM host or container with Java 21 LTS.
- Prefer a minimal dedicated server image: custom JRE or GraalVM native image.
- Use a frontend load balancer or API gateway for edge concerns.
- The framework itself can run on:
  - `com.sun.net.httpserver.HttpServer` for simplest deployment,
  - or a minimal custom socket-based HTTP server for stricter control.
- Keep the runtime inside the bank’s trusted compute zone.

## Container / Image Scanning

- Design images with minimal base layers and only required runtime artifacts.
- Use a reproducible build image and separate runtime image.
- Scan built images with tools such as Trivy, Clair, Docker Scan, Anchore, Snyk, Prisma Cloud.
- Keep runtime images lean: explicit entrypoint, non-root user, no build tools.
- Treat image scanning as a CI gate; optionally use live container integrity checks for runtime drift.
- Recommended pattern:
  1. scan the built image in CI,
  2. deploy only verified images,
  3. optionally run periodic live checks on active containers.
