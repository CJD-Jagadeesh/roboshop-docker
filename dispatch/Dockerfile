# ---------- Build Stage ----------
FROM golang:1.22 AS builder

WORKDIR /app

# Copy application source code
COPY . .

# Download dependencies
RUN go mod tidy

# Build the application
RUN go build -o dispatch

# ---------- Runtime Stage ----------
FROM debian:bookworm-slim

WORKDIR /app

# Copy binary from builder
COPY --from=builder /app/dispatch .

# Environment Variables
ENV AMQP_HOST=rabbitmq
ENV AMQP_USER=roboshop
ENV AMQP_PASS=roboshop123

CMD ["./dispatch"]