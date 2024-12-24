FROM ubuntu:latest

RUN apt update && apt install -y \
    git \
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
    sudo \
    && rm -rf /var/lib/apt/lists/*

RUN curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add - && \
    add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" && \
    apt update && apt install -y docker-ce docker-ce-cli containerd.io

RUN useradd -m dockeruser && echo "dockeruser:dockeruser" | chpasswd && adduser dockeruser sudo

USER dockeruser

WORKDIR /app

RUN echo "<h1>Ubuntu VPS Simulation with Docker</h1>" > /app/index.html

CMD /usr/bin/dockerd --host=fd:// & python3 -m http.server 8080 --directory /app

