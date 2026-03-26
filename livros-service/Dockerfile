# Dockerfile.dev
FROM eclipse-temurin:21-jdk-alpine

WORKDIR /app

# Instalar ferramentas
RUN apk add --no-cache curl bash

# Copiar arquivos do Maven
COPY mvnw .
COPY .mvn .mvn
COPY pom.xml .

RUN chmod +x mvnw && ./mvnw dependency:go-offline -B

# Copiar código fonte
COPY src ./src

# Expor portas
EXPOSE 9013 5005

# Spring Boot dev tools com debug
ENV JAVA_OPTS="\
    -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=*:5005 \
    -Dspring.devtools.restart.enabled=true"

CMD ["./mvnw", "spring-boot:run", "-Dspring-boot.run.jvmArguments=\"$JAVA_OPTS\""]