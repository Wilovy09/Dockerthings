FROM ubuntu:latest

RUN apt update && apt install -y \
    curl \
    vim \
    net-tools \
    iputils-ping \
    openssh-server \
    python3 \
    lsof \
    apt-transport-https \
    ca-certificates \
    software-properties-common \
    docker.io \
    sudo \
    && rm -rf /var/lib/apt/lists/*

RUN curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add - && \
    add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" && \
    apt update && apt install -y docker-ce docker-ce-cli containerd.io

RUN usermod -aG docker root

WORKDIR /app

RUN echo "<h1>Ubuntu VPS Simulation with Docker</h1>" > /app/index.html

CMD /usr/bin/dockerd & python3 -m http.server 8080 --directory /app
