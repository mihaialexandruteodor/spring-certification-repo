# Spring Certification
https://spring.academy/paths

# LABS

## Building a REST API with Spring Boot

- [x] lab 1: https://spring.academy/courses/building-a-rest-api-with-spring-boot/lessons/bootstrap-lab/lab
- [x] lab 2: https://spring.academy/courses/building-a-rest-api-with-spring-boot/lessons/test-first-lab/lab
- [x] lab 3: https://spring.academy/courses/building-a-rest-api-with-spring-boot/lessons/first-rest-endpoint-lab/lab
- [x] lab 4: https://spring.academy/courses/building-a-rest-api-with-spring-boot/lessons/spring-data-lab
- [x] lab 5: https://spring.academy/courses/building-a-rest-api-with-spring-boot/lessons/create-post-lab/lab
- [x] lab 6: https://spring.academy/courses/building-a-rest-api-with-spring-boot/lessons/get-list-lab/lab
- [x] lab 7: https://spring.academy/courses/building-a-rest-api-with-spring-boot/lessons/simple-spring-security-lab/lab
- [x] lab 8: https://spring.academy/courses/building-a-rest-api-with-spring-boot/lessons/implementing-put-lab/lab
- [x] lab 9: https://spring.academy/courses/building-a-rest-api-with-spring-boot/lessons/implementing-delete-lab/lab

## Spring Framework Essentials

- [x] lab 1: https://spring.academy/courses/spring-framework-essentials/lessons/spring-essentials-overview-lab
- [x] lab 1 demo: https://spring.academy/courses/spring-framework-essentials/lessons/spring-essentials-overview-lab-demo

# IMPORTANT COURSES

## Building a REST API with Spring Boot

[REST API concepts & Implementing GET](https://spring.academy/courses/building-a-rest-api-with-spring-boot/lessons/implementing-get)

[Implementing POST and Idempotency](https://spring.academy/courses/building-a-rest-api-with-spring-boot/lessons/implementing-post)

[GET for a list, Pagination](https://spring.academy/courses/building-a-rest-api-with-spring-boot/lessons/get-list)

[Spring Security](https://spring.academy/courses/building-a-rest-api-with-spring-boot/lessons/simple-spring-security)

[PUT, PATCH and POST](https://spring.academy/courses/building-a-rest-api-with-spring-boot/lessons/implementing-put)

[DELETE](https://spring.academy/courses/building-a-rest-api-with-spring-boot/lessons/implementing-delete)

## Introduction to the Spring Professional Learning Path

[Rewards Reference Domain](https://spring.academy/courses/spring-introduction/lessons/spring-introduction-rewards-reference-domain)

## Spring Framework Essentials

[Agenda](https://spring.academy/courses/spring-framework-essentials/lessons/agenda)
[The Dependency Injection (DI) Container](https://spring.academy/courses/spring-framework-essentials/lessons/container)
[Spring Framework History](https://spring.academy/courses/spring-framework-essentials/lessons/spring-essentials-overview-history)

# COMMANDS
```
cd cashcard
./gradlew build
```

# NOTES

## Building a REST API with Spring Boot

### LAB 5

- [x] Supplying an id tells Spring Data JDBC that we're asking it to update an existing CashCard, not create a new one. Since no CashCard with id of 44 exists yet, that "update" matches zero rows in the database. `cashCardRepository.save()` doesn't treat this as an error: no row is written, but no exception is thrown either. The controller has no way of knowing anything went wrong, so it still returns 201 CREATED with a Location header pointing at /cashcards/44.

### LAB 7

- [x] A user of an API can actually be a person or another program, so often we’ll use the term Principal as a synonym for “user”. Authentication is the act of a Principal proving its identity to the system. One way to do this is to provide credentials (e.g. a username and password using Basic Authentication). We say that once the proper credentials have been presented, the Principal is authenticated, or in other words, the user has successfully logged in.

- [x] HTTP is a stateless protocol, so each request must contain data that proves it’s from an authenticated Principal. Although it’s possible to present the credentials on every request, doing so is inefficient because it requires more processing on the server. Instead, an Authentication Session (or Auth Session, or just Session) is created when a user gets authenticated. Sessions can be implemented in many ways. We’ll use a common mechanism: A Session Token (a string of random characters) that is generated, and placed in a Cookie. A Cookie is a set of data stored in a web client (such as a browser), and associated with a specific URI.

- [x] The most basic mechanism of protection relies on HTTP clients and servers implementing the Same Origin Policy (SOP). This policy states that only scripts which are contained in a web page are allowed to send requests to the origin (URI) of the web page.

- [x] Sometimes a system consists of services running on several machines with different URIs (i.e. Microservices). Cross-Origin Resource Sharing (CORS) is a way that browsers and servers can cooperate to relax the SOP. A server can explicitly allow a list of “allowed origins” of requests coming from an origin outside the server’s.


### LAB 8

- [x] If you need the server to return the URI of the created resource (or the data you use to construct the URI), then you must use **POST**. Alternatively, when the resource URI is known at creation time (as is the case in our example Invoice API), you can use **PUT**.
- [x] POST creates a sub-resource (child resource) under (after), or within the request URI. This is what the Cash Card API does: The client calls the Create endpoint at `POST /cashcards`, but the actual URI of the created resource contains a generated ID at the end: `/cashcards/101`
- [x] PUT creates or replaces (updates) a resource at a specific request URI. For the  `/invoice`  example above, the Create endpoint would be  PUT `/invoice/1234-567`  , and the URI of the created resource would be the same as the URI sent in the  PUT  request.
- [x] 204 no content should be returned for DELETE and PUT: [developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Status/204](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Status/204)

### LAB 9
- [x] A simple option, called **hard delete**, is to delete the record from the database. With a hard delete, it’s gone forever. So, what can we do if we need data that existed prior to its deletion? An alternative is soft delete which works by marking records as "deleted" in the database (so that they're retained, but marked as deleted). For example, we can introduce an `IS_DELETED` boolean or a  `DELETED_DATE` timestamp column and then set that value-instead of fully removing the record by deleting the database row(s). With a soft delete, we also need to change how Repositories interact with the database. For example, a repository needs to respect the “deleted” column and exclude records marked deleted from Read requests.

## Spring Framework Essentials

### LAB 1
- [x] **POJO** comes from Plain Old Java Objects.