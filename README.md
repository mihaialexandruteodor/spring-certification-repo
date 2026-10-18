# Spring Certification
https://spring.academy/paths

## LABS

- [x] lab 1: https://spring.academy/courses/building-a-rest-api-with-spring-boot/lessons/bootstrap-lab/lab
- [x] lab 2: https://spring.academy/courses/building-a-rest-api-with-spring-boot/lessons/test-first-lab/lab
- [x] lab 3: https://spring.academy/courses/building-a-rest-api-with-spring-boot/lessons/first-rest-endpoint-lab/lab
- [x] lab 4: https://spring.academy/courses/building-a-rest-api-with-spring-boot/lessons/spring-data-lab
- [x] lab 5: https://spring.academy/courses/building-a-rest-api-with-spring-boot/lessons/create-post-lab/lab
- [x] lab 6: https://spring.academy/courses/building-a-rest-api-with-spring-boot/lessons/get-list-lab/lab

## IMPORTANT COURSES
[REST API concepts & Implementing GET](https://spring.academy/courses/building-a-rest-api-with-spring-boot/lessons/implementing-get)

[Implementing POST and Idempotency](https://spring.academy/courses/building-a-rest-api-with-spring-boot/lessons/implementing-post)

[GET for a list, Pagination](https://spring.academy/courses/building-a-rest-api-with-spring-boot/lessons/get-list)


---
## COMMANDS
```
cd cashcard
./gradlew build
```

## NOTES

### LAB 5

- [x] Supplying an id tells Spring Data JDBC that we're asking it to update an existing CashCard, not create a new one. Since no CashCard with id of 44 exists yet, that "update" matches zero rows in the database. `cashCardRepository.save()` doesn't treat this as an error: no row is written, but no exception is thrown either. The controller has no way of knowing anything went wrong, so it still returns 201 CREATED with a Location header pointing at /cashcards/44.
