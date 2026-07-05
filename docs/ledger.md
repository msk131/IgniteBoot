# Ledger (High Level)

Micro-batch policy: flush a batch when either 50 transactions accumulate or 5ms elapse. Before committing to the database, append the batch to a WAL (fsync) for recovery and idempotent replay.

```mermaid
graph TD
	subgraph Data Ingestion
		A[Raw Input Data] --> B[Validation Engine]
	end
	subgraph Secure Interception Layer
		B --> C{Metadata Inspector}
		C -->|Has @EncryptedField| D[Hardware Crypto Manager]
		C -->|Standard Field| E[Plaintext Buffer]
	end
	subgraph Storage & Audit Block
		D --> F[Secure Transaction Assembler]
		E --> F
		F --> G[Cryptographic Audit Ledger]
		G --> H[Final JDBC / Outbound Sink]
	end
```
