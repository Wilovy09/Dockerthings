FROM ubuntu:latest

RUN apt update && apt install -y \
    wget \
    curl \
    vim \
    net-tools \
    iputils-ping \
    openssh-server \
    python3 \
    lsof \
    && apt clean

WORKDIR /app

RUN echo "<h1>TEST</h1>" > /app/index.html

CMD ["python3", "-m", "http.server", "8080", "--directory", "/app"]
