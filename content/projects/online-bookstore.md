---
title: "Online Bookstore"
description: "REST api representing an Online Bookstore built using Spring Boot."
dateString: August 2022
draft: false
tags: ["rest-architecture", "object-oriented-design", "spring-boot", "spring-mvc", "lombok", "mapstruct", "postgres", "liquibase", "openapi", "swagger", "json"]
weight: 201
cover:
    image: "/projects/heroku-bookstore.JPG"
---

## Intro
This project is a backend API of an Online Bookstore. I have built this project to demonstrate my knowledge of developing **REST APIs using Spring framework**. It supports the following the functionalities with a brief description:-
- Get All books - This can be used to view all the books that are stored in the bookstore database.
- Modify book - For updating details of a book.
- Add book - For adding a new book to the bookstore.
- Search Posts - For searching of media related to a book using book's isbn.

## Working
The project is built using **Spring Boot** as the application framework and **Postgres** as the database. The project has been deployed **Heroku** and is exposed as a **REST API**. It uses various design principles and libraries:-
- It uses **Swagger** to display the API and its contract. Swagger is an implementation of **open-api** specification.
- **Jackson** for serializing and de-serializing Java objects in JSON format.
- **Lombok** that eliminates writing lot of boilerplate code.
- **Mapstruct** for mapping objects and helps decoupling of layers within the spring application.

## Resources
- [Online Bookstore Heroku Instance](https://heroku-bookstore.herokuapp.com/swagger-ui/index.html#/)
- [Online Bookstore Source code](https://github.com/rohit23ahuja/bookstore-application)
- [Spring Boot](https://spring.io/projects/spring-boot)
- [Project Lombok](https://projectlombok.org/)