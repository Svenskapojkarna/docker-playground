FROM ubuntu:latest

ARG DEBIAN_FRONTEND=noninteractive

# Install utility tools
RUN apt-get update && apt-get install -y \
    wget \
    vim \
    iputils-ping \
    netcat \
    libgdiplus \
    apt-utils \
    libc6-dev

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

# Install dependencies required for .NET6 installation
RUN echo "deb http://security.ubuntu.com/ubuntu focal-security main" | tee /etc/apt/sources.list.d/focal-security.list && \
    apt-get update && \
    apt-get install -y libssl1.1

# Install .NET6
RUN apt-get update && apt-get install -y \
    dotnet-runtime-3.1 \
    dotnet-sdk-6.0

# Fix .NET6 installation
RUN apt remove -y 'dotnet*' && \
    apt remove -y 'aspnetcore*' && \
    rm /etc/apt/sources.list.d/microsoft-prod.list && \
    apt update && \
    apt install -y dotnet-sdk-6.0

# Keep the container running
ENTRYPOINT ["tail", "-f", "/dev/null"]
