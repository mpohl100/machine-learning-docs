FROM python:3.13-slim

# Install required tools
RUN apt-get update && apt-get install -y \
    git \
    curl \
    vim \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

# Create a non-root user
RUN useradd -ms /bin/bash vscode
USER vscode
WORKDIR /workspace

# Set default shell
SHELL ["/bin/bash", "-c"]

# Install MkDocs
COPY requirements.txt /tmp/
RUN pip install --no-cache-dir -r /tmp/requirements.txt
