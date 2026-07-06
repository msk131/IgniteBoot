# Overview

IgniteBoot is a contract-first developer platform for building lightweight, secure REST APIs without Spring Boot–style runtime magic.

The platform is organized around three clear boundaries:
- design boundary: declarative API and policy definitions
- transformer boundary: ahead-of-time generation of explicit Java source
- runtime boundary: a lean execution process with no framework runtime overhead

```mermaid
graph LR
	subgraph 1. Define Phase
		A[Developer API Spec] --> B[Security & Compliance Rules]
	end
	subgraph 2. Generate Phase
		B --> C[Platform Transformer]
		C --> D[Ready-to-Compile Codebase]
	end
	subgraph 3. Execute Phase
		D --> E[Ultra-Lightweight Binary]
		E --> F[Air-Gapped Cloud/K8s]
	end
```

```mermaid
sequenceDiagram
	actor Dev as Bank Developer
	participant Transformer as Platform Transformer
	participant Spec as API & Compliance Spec
	participant App as Generated Project Layout

	Dev->>Spec: 1. Define REST API paths and compliance rules
	Dev->>Transformer: 2. Run generation pipeline
	Transformer->>App: 3. Emit explicit routes, DTOs, and validators
	Dev->>App: 4. Implement business logic only where needed
	Dev->>App: 5. Compile directly to a native machine binary
```
