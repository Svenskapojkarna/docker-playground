FROM ubuntu:latest

ARG DEBIAN_FRONTEND=noninteractive

# Install utility tools
RUN apt-get update && apt-get install -y \
    wget \
    vim \
    iputils-ping \
    netcat

# Install mono
RUN apt install -y gnupg ca-certificates && \
    apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 3FA7E0328081BFF6A14DA29AA6A19B38D3D831EF && \
    echo "deb https://download.mono-project.com/repo/ubuntu stable-focal main" | tee /etc/apt/sources.list.d/mono-official-stable.list && \
    apt update && \
    apt install -y mono-devel

# Fetch dotnet packages
RUN wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb && \
    dpkg -i packages-microsoft-prod.deb && \
    rm packages-microsoft-prod.deb

# Install .NET6
RUN apt-get update && apt-get install -y \
    apt-transport-https \
    dotnet-runtime-3.1 \
    dotnet-sdk-6.0

# Keep the container running
ENTRYPOINT ["tail", "-f", "/dev/null"]
