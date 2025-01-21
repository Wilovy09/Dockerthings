FROM rust:alpine3.19 AS builder

RUN apk add --no-cache musl-dev openssl-dev

WORKDIR /usr/src/app

COPY Cargo.toml Cargo.lock ./
COPY src ./src

RUN cargo build --release

FROM alpine:3.19

RUN apk add --no-cache ca-certificates

WORKDIR /usr/local/bin

COPY --from=builder /usr/src/app/target/release/DockerAPI .

EXPOSE 8080

CMD ["./DockerAPI"]
