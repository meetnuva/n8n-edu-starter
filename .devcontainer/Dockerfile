FROM mcr.microsoft.com/devcontainers/base:ubuntu

# Install Node.js 20 safely (no nodesource, no feature)
RUN apt-get update \
    && apt-get install -y curl ca-certificates gnupg \
    && curl -fsSL https://deb.nodesource.com/gpgkey/nodesource-repo.gpg.key | gpg --dearmor -o /usr/share/keyrings/nodesource.gpg \
    && echo "deb [signed-by=/usr/share/keyrings/nodesource.gpg] https://deb.nodesource.com/node_20.x nodistro main" > /etc/apt/sources.list.d/nodesource.list \
    && apt-get update \
    && apt-get install -y nodejs

# Install n8n locally inside container
RUN npm install -g n8n

# Make n8n config directory writable
RUN mkdir -p /home/vscode/.n8n && chown -R vscode:vscode /home/vscode/.n8n

USER vscode
WORKDIR /workspaces
