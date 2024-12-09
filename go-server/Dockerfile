FROM golang:1.23.0 AS builder
WORKDIR /app
COPY . .
RUN CGO_ENABLED=0 GOARCH=amd64 GOOS=linux go build -o main

FROM alpine:3.18
RUN apk --no-cache add ca-certificates
WORKDIR /root/
COPY --from=builder /app/main .
CMD ["./main"]