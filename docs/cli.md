# CLI (High Level)

Workflow: author OpenAPI (or protobuf) → run the transformer pipeline → the build-time module emits DTOs, validators, handler stubs, and a static routing registry. Developers implement business logic in handwritten files; generated files remain separate from editable code.
