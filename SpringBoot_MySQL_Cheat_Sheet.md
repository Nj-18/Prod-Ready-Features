# Spring Boot + MySQL Connection Cheat Sheet

## 1. Add Dependencies (pom.xml)

``` xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-jpa</artifactId>
</dependency>

<dependency>
    <groupId>com.mysql</groupId>
    <artifactId>mysql-connector-j</artifactId>
    <scope>runtime</scope>
</dependency>
```

**Remember** - JPA Starter = Hibernate + JPA - MySQL Connector = JDBC
Driver

------------------------------------------------------------------------

## 2. Configure application.properties

``` properties
spring.datasource.url=jdbc:mysql://localhost:3306/testDB
spring.datasource.username=root
spring.datasource.password=YOUR_PASSWORD

# Optional
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true
```

`ddl-auto` - create → Drops & recreates tables every run - update →
Updates schema (recommended for development) - validate → Only validates
schema - create-drop → Creates on startup, drops on shutdown

------------------------------------------------------------------------

## 3. Create Database

``` sql
CREATE DATABASE testDB;
SHOW DATABASES;
```

------------------------------------------------------------------------

## 4. Create Entity

``` java
@Entity
public class Student {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;
}
```

------------------------------------------------------------------------

## 5. Create Repository

``` java
public interface StudentRepository extends JpaRepository<Student, Long> {
}
```

------------------------------------------------------------------------

## 6. Run Application

``` java
@SpringBootApplication
public class DemoApplication {
    public static void main(String[] args) {
        SpringApplication.run(DemoApplication.class, args);
    }
}
```

------------------------------------------------------------------------

## Flow to Remember

Spring Boot → application.properties → JDBC URL → MySQL Driver → MySQL
Server → Database → Hibernate → Entity → Table

------------------------------------------------------------------------

## Common Errors

### Cannot load driver class

-   Missing mysql-connector-j dependency
-   Maven not refreshed
-   Wrong driver class name

### Access denied

-   Wrong username/password

### Unknown database

``` sql
CREATE DATABASE testDB;
```

### Communications link failure

-   MySQL service not running

### Table not found

-   Missing @Entity
-   Wrong ddl-auto

------------------------------------------------------------------------

## Interview Answer (30 Seconds)

1.  Add JPA and MySQL dependencies.
2.  Configure datasource properties.
3.  Create the database.
4.  Create Entity and Repository.
5.  Run the project.
6.  Hibernate connects using the MySQL JDBC Driver and creates/updates
    tables based on ddl-auto.
