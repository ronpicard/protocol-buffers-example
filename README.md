# Protocol Buffers Loopback Example

This project shows how to define a Protocol Buffers message, generate Python code from it, and send/receive it over a TCP loopback connection (`127.0.0.1`).

## Running the Example

### 1. Build the Dev Container
- Open this repo in **Visual Studio Code**.
- Make sure you have the **Dev Containers** extension installed.
- Press **F1** → **Dev Containers: Rebuild and Reopen in Container**.

The container comes pre-installed with:
- Ubuntu 22.04
- Python 3.x
- Latest `protoc` compiler
- Python `protobuf` runtime

### 2. Compile the `.proto` file
protoc --python_out=. protos/example.proto

### 3. Run the example
python3 protobuf_loopback_demo.py