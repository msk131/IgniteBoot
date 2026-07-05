# CLI (High Level)

Workflow: author OpenAPI (or protobuf) → run `ignite-cli gen` → CLI emits DTOs, validators, handler stubs, and a static routing registry. Developers implement business logic in handwritten files; generated files are separated from editable code.
