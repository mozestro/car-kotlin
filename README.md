# car-kotlin

A car directory REST API in Kotlin + Spring Boot 3 with stateless JWT auth and role-based access.

## What's inside

- **CRUD for cars** — `make`, `model`, `year`, `price` and a unique 17-character `vin`; the database checks
  the year range and that the price is positive.
- **Auth** — `/auth/register` creates a user, `/auth/login` returns a JWT; a filter before `UsernamePasswordAuthenticationFilter`
  puts the user into the security context.
- **Roles** — `USER` can read cars, `ADMIN` can create, update and delete them.
- **Schema** — Flyway migrations with seed data.

## Stack

Kotlin · Spring Boot 3.4 (Web, Security, Data JPA, Validation) · jjwt · PostgreSQL · Flyway

## Run

Start PostgreSQL with a `car_directory` database on port `5445` (user and password `postgres`), then:

```bash
./gradlew bootRun
```

## API

| Method | Path | Role |
|---|---|---|
| POST | `/auth/register` | — |
| POST | `/auth/login` | — |
| GET | `/cars`, `/cars/{id}` | USER |
| POST | `/cars` | ADMIN |
| PUT | `/cars/{id}` | ADMIN |
| DELETE | `/cars/{id}` | ADMIN |
