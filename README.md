# ai-agents-mcp

A demonstration project for using MCP (Modal Context Protocol) with AI agents, featuring both Python and Rust implementations of MCP servers and clients. This project showcases interoperability and best practices for building agent communication systems.

---

## Table of Contents
- [Overview](#overview)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
  - [Running Locally](#running-locally)
  - [Using Docker](#using-docker)
  - [Using Docker Compose](#using-docker-compose)
- [Examples](#examples)
- [Testing](#testing)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)
- [To Do](#to-do)

---

## Overview

This repository provides demos for using MCP to facilitate communication between AI agents. It includes:
- A Python-based MCP server and client (`mcp-python-server-client/`)
- A Rust-based MCP server (`mcp-rust-server/`)

---

## Project Structure

```
.
├── mcp-python-server-client/
│   ├── src/
│   │   ├── demo_client.py
│   │   ├── demo_server.py
│   │   ├── mcp_py_client_rust_server.py
│   │   └── ...
├── mcp-rust-server/
│   ├── src/
│   │   ├── handler.rs
│   │   ├── main.rs
│   │   ├── main_sse.rs
│   │   └── tools.rs
│   └── ...
├── docker-compose.yml
├── LICENSE
└── README.md
```

---

## Prerequisites
- [Python 3.11+](https://www.python.org/)
- [Rust](https://www.rust-lang.org/tools/install)
- [uv](https://github.com/astral-sh/uv) (Python dependency manager)
- [cargo](https://doc.rust-lang.org/cargo/) (Rust package manager)
- [Docker](https://www.docker.com/) (for containerization)

---

## Installation

### 1. Install System Dependencies
```sh
brew install uv
brew install rust
brew install docker
```

### 2. Set Up Python Environment
```sh
cd mcp-python-server-client
uv init
uv pip install -r requirements.txt  # If requirements.txt exists
uv add <pkg>  # Add any additional packages
uv sync       # Update project environment
```

### 3. Set Up Rust Server
```sh
cd mcp-rust-server
cargo build --release
```

---

## Usage

### Running Locally

#### Start the Python MCP Server
```sh
cd mcp-python-server-client
uv run python src/demo_server.py
```

#### Start the Rust MCP Server
```sh
cd mcp-rust-server
cargo run --release --bin mcp-sse
```

#### Run the Python Demo Client
```sh
cd mcp-python-server-client
uv run python src/mcp_py_client_rust_server.py
```

---

### Using Docker

#### Build the Rust Server Docker Image
```sh
cd mcp-rust-server
docker build -t mcp-sse-server-exp .
```

#### Run the Rust Server Container (map to a custom port, e.g., 8001)
```sh
docker run -p 8001:8000 mcp-sse-server-exp
```
- The server will be accessible at `http://127.0.0.1:8001/sse`.
- Update your Python client to use this URL if running locally.

---

### Using Docker Compose

#### Start the Rust Server with Docker Compose
```sh
docker compose up --build
```
- By default, this maps host port 8001 to container port 8000.
- You can access the server at `http://127.0.0.1:8001/sse`.

#### (Optional) Add the Python Client as a Service
- You can extend `docker-compose.yml` to add the Python client as a service for full containerized workflows.

---

## Examples

### Example: Start Python Server and Client Locally
1. In one terminal, start the server:
    ```sh
    uv run mcp dev src/demo_server.py
    ```
2. In another terminal, run the client:
    ```sh
    uv run python src/demo_client.py
    ```

### Example: Use Rust Server Locally
1. Build and run the Rust server:
    ```sh
    cd mcp-rust-server
    cargo build --release
    cargo run --release --bin mcp-sse
    ```
2. Use the Python client to connect to the Rust server:
    ```sh
    cd mcp-python-server-client
    uv run python src/mcp_py_client_rust_server.py
    ```

### Example: Use Rust Server with Docker
1. Build and run the Docker image:
    ```sh
    cd mcp-rust-server
    docker build -t mcp-sse-server-exp .
    docker run -p 8001:8000 mcp-sse-server-exp
    ```
2. Use the Python client (update the server URL to `http://127.0.0.1:8001/sse`):
    ```sh
    cd mcp-python-server-client
    uv run python src/mcp_py_client_rust_server.py
    ```

### Example: Use Docker Compose
1. From the project root, run:
    ```sh
    docker compose up --build
    ```
2. The Rust server will be available at `http://127.0.0.1:8001/sse`.

---

## Testing

### Python
```sh
cd mcp-python-server-client
uv pip install pytest
pytest
```

### Rust
```sh
cd mcp-rust-server
cargo test
```

---

## Contributing
Contributions are welcome! Please open issues or submit pull requests for improvements or bug fixes.

---

## License
This project is licensed under the [Apache License 2.0](LICENSE).

---

## Contact
For questions or support, please open an issue in this repository.

---

## To Do
- [ ] Add more comprehensive unit and integration tests for both Python and Rust implementations
- [ ] Implement authentication and authorization for MCP servers
- [ ] Provide Dockerfiles for easy deployment
- [ ] Add support for additional agent protocols
- [ ] Improve documentation with architecture diagrams
- [ ] Add CI/CD pipeline for automated testing and deployment
- [ ] Provide example agents with real-world tasks
