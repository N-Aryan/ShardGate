# ShardGate

**A PostgreSQL proxy for SQL routing, query analysis, and database traffic management, written in Go.**

ShardGate is an infrastructure engineering project based on the open-source [pgproxy](https://github.com/wgliang/pgproxy). It explores how a proxy layer can sit between applications and PostgreSQL to manage database requests, inspect SQL statements, and apply routing and filtering policies.

> **Project status:** Work in progress. The codebase is derived from pgproxy and has not yet been independently validated in the current development environment.

## Overview

Applications communicating directly with database servers can become difficult to manage as traffic and infrastructure grow.

ShardGate explores a centralized proxy layer responsible for:

- Forwarding client connections to PostgreSQL backends
- Analyzing SQL requests before forwarding
- Applying query filtering and rewriting policies
- Supporting read/write traffic separation
- Providing a foundation for monitoring and traffic management

The current codebase inherits functionality from the upstream pgproxy project. Individual capabilities require testing before they are treated as validated ShardGate features.

## Architecture

```text
                  Application / Client
                           |
                           v
                    +-------------+
                    |  ShardGate  |
                    |  Go Proxy   |
                    +-------------+
                           |
                 +---------+---------+
                 |                   |
                 v                   v
           SQL Analysis       Request Routing
           and Filtering       and Forwarding
                 |                   |
                 +---------+---------+
                           |
                           v
                       PostgreSQL
```

## Technology Stack

| Technology | Purpose |
|---|---|
| Go | Proxy server implementation |
| PostgreSQL | Target database |
| SQL Parser | Query analysis and transformation |
| Git | Version control |

## Existing Codebase

The upstream pgproxy project describes support for:

- PostgreSQL connection proxying
- SQL statement inspection and filtering
- SQL rewriting
- Read/write separation
- Database operation monitoring
- Request limiting
- Database service recovery features

These capabilities are inherited from the upstream source and are not presented as independently implemented features.

## Getting Started

### Prerequisites

- Go development environment
- PostgreSQL server
- Git

### Clone the repository

```bash
git clone https://github.com/N-Aryan/ShardGate.git
cd ShardGate
```

### Inspect the configuration

The upstream project includes a `pgproxy.conf` configuration file.

Review the database connection settings before attempting to run the proxy.

### Build and test

The current codebase comes from an older Go project and may require dependency or module compatibility updates.

```bash
go version
go test ./...
```

A successful build and test run has not yet been verified. Setup instructions will be updated after the development environment and dependencies have been validated.

## Development Roadmap

- [ ] Establish a reproducible build environment
- [ ] Validate existing PostgreSQL proxy functionality
- [ ] Add connection and request timeout handling
- [ ] Improve backend health monitoring
- [ ] Introduce integration tests for database routing
- [ ] Add load-testing benchmarks
- [ ] Document performance and failure-handling behavior

## Project Structure

```text
ShardGate/
├── cli/              # Command-line functionality
├── parser/           # SQL parsing and analysis
├── proxy/            # Proxy implementation
├── examples/         # Example integrations
├── pgproxy.conf      # Proxy configuration
├── main.go           # Application entry point
├── LICENSE
└── README.md
```

## Attribution and License

ShardGate is derived from **[wgliang/pgproxy](https://github.com/wgliang/pgproxy)**, originally developed by its respective contributors.

The upstream project is distributed under the **Apache License 2.0**. Its original license and copyright notices are retained.

The SQL parser also incorporates code based on [sqlparser](https://github.com/xwb1989/sqlparser), as acknowledged by the upstream project.

This repository is an independent learning and development effort. It is not affiliated with or endorsed by the original pgproxy maintainers.

## Author

**Aryan Narang**

[GitHub](https://github.com/N-Aryan)


