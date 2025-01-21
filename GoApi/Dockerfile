FROM golang:1.20-alpine AS build

RUN apk add --no-cache git

WORKDIR /app
COPY . .

RUN go build -o /http-server main.go

FROM alpine:3.18

RUN addgroup -S appgroup && adduser -S appuser -G appgroup

COPY --from=build /http-server /sbin/http-server

USER appuser

EXPOSE 8080
CMD ["/sbin/http-server"]
