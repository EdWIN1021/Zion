# Spring Data Rest

## dependency

```xml
<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-data-rest</artifactId>
</dependency>
```

---

## application.properties

```
spring.data.rest.base-path=/magic-api
spring.data.rest.default-page-size=3
```

---

## pagination

```
http://localhost:8080/magic-api/employees?page=1&size=2
```

---

## sort

```
http://localhost:8080/magic-api/employees?sort=lastName,desc
```