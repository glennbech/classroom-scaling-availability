# .devcontainer/Dockerfile
# Use a base image that includes Docker (Docker in Docker setup)
FROM mcr.microsoft.com/devcontainers/python:dev-3.9-bookworm

# Remove Yarn repository to fix GPG key issues
RUN rm -f /etc/apt/sources.list.d/yarn.list

# Install Terraform
RUN TERRAFORM_VERSION=1.7.5 \
    && curl -fsSL "https://releases.hashicorp.com/terraform/${TERRAFORM_VERSION}/terraform_${TERRAFORM_VERSION}_linux_amd64.zip" -o terraform.zip \
    && unzip terraform.zip \
    && mv terraform /usr/local/bin/ \
    && rm terraform.zip

# Install AWS CLI v2
RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" \
    && unzip awscliv2.zip \
    && ./aws/install \
    && rm -rf awscliv2.zip aws

# Clean up
RUN apt-get clean && rm -rf /var/lib/apt/lists/*
