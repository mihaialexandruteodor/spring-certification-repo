# Spring Certification
https://spring.academy/paths

## LABS

- [x] lab 1: https://spring.academy/courses/building-a-rest-api-with-spring-boot/lessons/bootstrap-lab/lab
- [x] lab 2: https://spring.academy/courses/building-a-rest-api-with-spring-boot/lessons/test-first-lab/lab
- [x] lab 3: https://spring.academy/courses/building-a-rest-api-with-spring-boot/lessons/first-rest-endpoint-lab/lab
- [x] lab 4: https://spring.academy/courses/building-a-rest-api-with-spring-boot/lessons/spring-data-lab
- [x] lab 5: https://spring.academy/courses/building-a-rest-api-with-spring-boot/lessons/create-post-lab/lab
- [x] lab 6: https://spring.academy/courses/building-a-rest-api-with-spring-boot/lessons/get-list-lab/lab
- [x] lab 7: https://spring.academy/courses/building-a-rest-api-with-spring-boot/lessons/simple-spring-security-lab/lab

## IMPORTANT COURSES
[REST API concepts & Implementing GET](https://spring.academy/courses/building-a-rest-api-with-spring-boot/lessons/implementing-get)

[Implementing POST and Idempotency](https://spring.academy/courses/building-a-rest-api-with-spring-boot/lessons/implementing-post)

[GET for a list, Pagination](https://spring.academy/courses/building-a-rest-api-with-spring-boot/lessons/get-list)

[Spring Security](https://spring.academy/courses/building-a-rest-api-with-spring-boot/lessons/simple-spring-security)
---
## COMMANDS
```
cd cashcard
./gradlew build
```

## NOTES

### LAB 5

- [x] Supplying an id tells Spring Data JDBC that we're asking it to update an existing CashCard, not create a new one. Since no CashCard with id of 44 exists yet, that "update" matches zero rows in the database. `cashCardRepository.save()` doesn't treat this as an error: no row is written, but no exception is thrown either. The controller has no way of knowing anything went wrong, so it still returns 201 CREATED with a Location header pointing at /cashcards/44.

### LAB 7

- [x] A user of an API can actually be a person or another program, so often we’ll use the term Principal as a synonym for “user”. Authentication is the act of a Principal proving its identity to the system. One way to do this is to provide credentials (e.g. a username and password using Basic Authentication). We say that once the proper credentials have been presented, the Principal is authenticated, or in other words, the user has successfully logged in.

- [x] HTTP is a stateless protocol, so each request must contain data that proves it’s from an authenticated Principal. Although it’s possible to present the credentials on every request, doing so is inefficient because it requires more processing on the server. Instead, an Authentication Session (or Auth Session, or just Session) is created when a user gets authenticated. Sessions can be implemented in many ways. We’ll use a common mechanism: A Session Token (a string of random characters) that is generated, and placed in a Cookie. A Cookie is a set of data stored in a web client (such as a browser), and associated with a specific URI.

- [x] The most basic mechanism of protection relies on HTTP clients and servers implementing the Same Origin Policy (SOP). This policy states that only scripts which are contained in a web page are allowed to send requests to the origin (URI) of the web page.

- [x] Sometimes a system consists of services running on several machines with different URIs (i.e. Microservices). Cross-Origin Resource Sharing (CORS) is a way that browsers and servers can cooperate to relax the SOP. A server can explicitly allow a list of “allowed origins” of requests coming from an origin outside the server’s.
