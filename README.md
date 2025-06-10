# ai-agents-mcp

A demonstration project for using MCP (Modal Context Protocol) with AI agents, featuring both Python and Rust implementations of MCP servers and clients.

---

## Table of Contents

- [Overview](#overview)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
  - [Running the Python MCP Server](#running-the-python-mcp-server)
  - [Running the Rust MCP Server](#running-the-rust-mcp-server)
  - [Running the Python Demo Client](#running-the-python-demo-client)
- [Examples](#examples)
- [Testing](#testing)
- [License](#license)
- [Contributing](#contributing)

---

## Overview

This repository provides demos for using MCP to facilitate communication between AI agents. It includes:

- A Python-based MCP server and client ([mcp-python-client/src/](mcp-python-client/src/))
- A Rust-based MCP server ([mcp-rust-server/src/](mcp-rust-server/src/))

The goal is to showcase interoperability and best practices for building agent communication systems.

---

## Project Structure

```
.
├── mcp-python-client/
│   ├── src/
│   │   ├── demo_client.py
│   │   ├── demo_server.py
│   │   └── mcp_py_client_rust_server.py
│   └── ...
├── mcp-rust-server/
│   ├── src/
│   │   ├── handler.rs
│   │   ├── main.rs
│   │   └── tools.rs
│   └── ...
├── LICENSE
└── README.md
```

---

## Prerequisites

- [Python 3.11+](https://www.python.org/)
- [Rust](https://www.rust-lang.org/tools/install)
- [uv](https://github.com/astral-sh/uv) (Python package/dependency manager)
- [cargo](https://doc.rust-lang.org/cargo/) (Rust package manager)

---

## Installation

### 1. Install System Dependencies

```sh
brew install uv
brew install rust
```

### 2. Set Up Python Environment

```sh
cd mcp-python-client
uv init
uv pip install -r requirements.txt  # If requirements.txt exists
uv add pkg # add pkg
uv install     # install dpendencies 
```

### 3. Set Up Rust Server

```sh
cd mcp-rust-server
cargo build --release
```

---

## Usage

### Running the Python MCP Server

```sh
cd mcp-python-client
uv run mcp dev src/demo_server.py
```

### Running the Rust MCP Server

```sh
cd mcp-rust-server
cargo run
```

### Running the Python Demo Client

```sh
cd mcp-python-client
uv run python src/mcp_py_client_rust_server.py
```

---

## Examples

### Example: Start Python Server and Client

1. In one terminal, start the server:
    ```sh
    uv run mcp dev src/demo_server.py
    ```
2. In another terminal, run the client:
    ```sh
    uv run python src/demo_client.py
    ```

### Example: Use Rust Server

1. Build and run the Rust server:
    ```sh
    cd mcp-rust-server
    cargo build --release
    cargo run
    ```
2. Use the Python client to connect to the Rust server:
    ```sh
    cd mcp-python-client
    uv run python src/mcp_py_client_rust_server.py
    ```

---

## Testing (Coming)

### Python
```sh
cd mcp-python-client
uv pip install pytest
pytest
```

### Rust

```sh
cd mcp-rust-server
cargo test
```

---

## License

This project is licensed under the [Apache License 2.0](LICENSE).

---

## Contributing

Contributions are welcome! Please open issues or submit pull requests for improvements or bug fixes.

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