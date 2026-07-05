# Overview

IgniteBoot is a contract-first developer platform for building lightweight, secure REST APIs without Spring Boot–style runtime magic.

Topology: CLI (AOT codegen) → Toolkits (small libraries) → Runtime (explicit bootstrap and interceptor chain).

```mermaid
graph LR
	subgraph 1. Define Phase
		A[Developer API Spec] --> B[Security & Compliance Rules]
	end
	subgraph 2. Generate Phase
		B --> C[Platform CLI Core Engine]
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
	participant CLI as Platform CLI Tool
	participant Spec as API & Compliance Spec
	participant App as Generated Project Layout

	Dev->>CLI: 1. Run 'ignite init' to scaffold project
	CLI->>App: 2. Create foundational structure (No framework dependencies)
	Dev->>Spec: 3. Define REST API paths & Security Clearance levels
	Dev->>CLI: 4. Run 'ignite generate'
	Note over CLI: Validates spec against banking compliance rules
	CLI->>App: 5. Generate explicit Java source code (Routes, DTOs, Validations)
	Dev->>App: 6. Implement purely the business logic interfaces
	Dev->>App: 7. Compile directly to native machine binary
```
