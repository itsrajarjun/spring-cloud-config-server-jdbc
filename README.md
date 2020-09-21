# Spring Cloud Config Server DataBase: JDBC Backend

- Db Environment Repository using JDBC

# Dependencies
- java: 1.8
- spring-boot: 2.3.3.RELEASE
- spring-cloud: Greenwich.RELEASE
- spring-boot-starter-jdbc
- ojdbc8

# DB Script
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
