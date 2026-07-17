FROM maven:3.9.16-ibmjava
WORKDIR /opt/shipping
COPY pom.xml .
RUN mvn dependency:go-offline
COPY . .
RUN mvn clean package && \
    mv target/shipping-1.0.jar shipping.jar
ENV CART_ENDPOINT=http://cart:8080 \
    CATALOGUE_ENDPOINT=http://catalogue:8080 \
    MYSQL_HOST=mysql \
    MYSQL_PORT=3306 \
    MYSQL_USER=root \
    MYSQL_PASSWORD=root \
    MYSQL_DB=roboshop
CMD ["java", "-jar", "shipping.jar"]
