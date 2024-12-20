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
    software-properties-common

RUN curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add - && \
    add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

RUN apt update && apt install -y docker-ce docker-ce-cli containerd.io && \
    systemctl enable docker

WORKDIR /app

RUN echo "<h1>Ubuntu VPS Simulation</h1>" > /app/index.html

CMD ["python3", "-m", "http.server", "8080", "--directory", "/app"]
