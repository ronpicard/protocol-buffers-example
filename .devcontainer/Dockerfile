FROM ubuntu:22.04

# Avoid interactive prompts
ENV DEBIAN_FRONTEND=noninteractive

# Install dependencies for Python, pip, curl, unzip, and bash
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    python3 python3-pip python3-venv \
    curl unzip sudo bash \
    && rm -rf /var/lib/apt/lists/*

# Install latest protoc (25.3)
RUN PROTOC_ZIP=protoc-25.3-linux-x86_64.zip && \
    curl -OL https://github.com/protocolbuffers/protobuf/releases/download/v25.3/$PROTOC_ZIP && \
    sudo unzip -o $PROTOC_ZIP -d /usr/local bin/protoc && \
    sudo unzip -o $PROTOC_ZIP -d /usr/local 'include/*' && \
    rm -f $PROTOC_ZIP

# Install Python protobuf runtime
RUN pip3 install --no-cache-dir protobuf==5.*

# Create non-root user 'vscode' with sudo privileges
RUN useradd -m vscode && \
    echo "vscode ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers && \
    chsh -s /bin/bash vscode

# Switch shell to bash for container build
SHELL ["/bin/bash", "-c"]

# Switch to 'vscode' user
USER vscode

# Set workspace directory to repo root (so .devcontainer is visible)
WORKDIR /workspaces/protocol-buffers-example
