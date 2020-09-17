# Spring Cloud Config Server DataBase: JDBC Backend

- Db Environment Repository using JDBC

# Dependencies
- java: 1.8
- spring-boot: 2.3.3.RELEASE
- spring-cloud: Greenwich.RELEASE
- spring-boot-starter-jdbc
- ojdbc8

#Usage


- properties
#spring.cloud.config.server.git.uri=
spring.profiles.active=jdbc
spring.datasource.hikari.connection-timeout=5000
spring.datasource.hikari.maximum-pool-size=10
spring.datasource.driver-class-name=oracle.jdbc.OracleDriver
spring.cloud.config.server.jdbc.sql= SELECT PROP_KEY, VALUE from PROPERTIES where APPLICATION=? and PROFILE=? and LABEL=?
spring.cloud.config.server.jdbc.order=1
spring.datasource.url=jdbc:oracle:thin:@localhost:1521:ORCL
spring.datasource.username=raj
spring.datasource.password=raj

- Oracle Script
create table PROPERTIES
(
    id          number,
    CREATED_ON  date,
    APPLICATION varchar(255),
    PROFILE     varchar(255),
    LABEL       varchar(255),
    PROP_KEY    varchar(255),
    VALUE       varchar(255),
    primary key (id)
);

INSERT INTO properties (id, CREATED_ON, APPLICATION, PROFILE, LABEL, PROP_KEY, VALUE)
VALUES (1, NULL, 'raj', 'dev', 'latest', 'test-prop-key', 'test-value');

- Execute
http://localhost:8080/raj/dev/latest to get the properties from the table