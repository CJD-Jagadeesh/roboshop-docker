FROM python:3.11-slim

# Install required packages
RUN apt-get update && \
    apt-get install -y curl unzip gcc build-essential && \
    rm -rf /var/lib/apt/lists/*

# Set working directory
WORKDIR /app

# Download application
RUN curl -L -o /tmp/payment.zip https://roboshop-artifacts.s3.amazonaws.com/payment-v3.zip && \
    unzip /tmp/payment.zip -d /app && \
    rm -f /tmp/payment.zip

# Install Python dependencies
RUN pip3 install --no-cache-dir -r requirements.txt

# Environment Variables
ENV CART_HOST=cart
ENV CART_PORT=8080
ENV USER_HOST=user
ENV USER_PORT=8080
ENV AMQP_HOST=rabbitmq
ENV AMQP_USER=roboshop
ENV AMQP_PASS=roboshop123

# Expose port
EXPOSE 8080

# Start the application
CMD ["uwsgi", "--ini", "payment.ini"]