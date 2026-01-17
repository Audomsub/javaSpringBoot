website form caombodia this is cambodian


docker-compose----
services:
  ## POSTGRESQL
  postgresql:
    image: postgres:latest
    restart: always
    shm_size: 128mb
    ports:
      - 5432:5432
    environment:
      POSTGRES_PASSWORD: P@ssw0rd
      POSTGRES_USER: appusr
    volumes:
      # - ./volume/postgresql:/var/lib/postgresql/data
      - ./script:/docker-entrypoint-initdb.d
    networks:
      - local-network


------------------------------------------------
spring:
  application:
    name: demo
  datasource:
    url: jdbc:postgresql://localhost:5432/postgres
    username: appusr
    password: P@ssw0rd
    driver-class-name: org.postgresql.Driver
  jpa:
    hibernate:
      ddl-auto: validate
    show-sql: true
    properties:
      hibernate:
        dialect: org.hibernate.dialect.PostgreSQLDialect
        format_sql: true
