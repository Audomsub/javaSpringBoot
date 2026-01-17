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


------------------pom.yaml---------------------------------------
<dependencies>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter</artifactId>
		</dependency>

		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-web</artifactId>
		</dependency>

		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-data-jpa</artifactId>
		</dependency>

		<dependency>
			<groupId>org.postgresql</groupId>
			<artifactId>postgresql</artifactId>
			<scope>runtime</scope>
		</dependency>

		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-validation</artifactId>
		</dependency>

		<dependency>
			<groupId>jakarta.validation</groupId>
			<artifactId>jakarta.validation-api</artifactId>
		</dependency>

		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-test</artifactId>
			<scope>test</scope>
		</dependency>
	</dependencies>



--------------------sql----------------------

CREATE TABLE public.student (
 id BIGINT GENERATED ALWAYS AS IDENTITY NOT NULL,
 "name" varchar(255) NOT NULL,
 score int4 NOT NULL,
 student_id varchar(255) not null,
 grade varchar(255) not null,
 CONSTRAINT student_pkey PRIMARY KEY (id)
);
