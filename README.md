# Spring Resilience Example

This is a simple mini-microservice example that showcases resilience capabilities by Spring, namely:

* Circuit Breaker (using Hystrix)

These will be used by `resilientApp` when interacting with `failingApp`.

## TBD

* Implement more resilience use cases

## ResilientApp

`resilientApp` gives callers recommendations on what to wear in a given Location. It accepts a location ID and returns an appropriate outfit. The appropriate outfit is decided upon according to the current temperature at the specified location. The most recent temperature reading is retrieved from `failingApp`, which is likely to fail.
In order to handle failing calls, Hystrix Circuit Breaker is used, defaulting to a fixed temperature value.

## FailingApp

`failingApp` gives callers the most recent temperature reading for a given location. It fails faily often, so callers should handle these failures accordingly.

## How to run

1. Clone this repository
2. Start `failingApp` (`cd failingApp && mvn spring-boot:run`)
3. Start `resilientApp` (`cd resilientApp && mvn spring-boot:run`)
4. Perform calls against `resilientApp` (`curl localhost:8080/recommender/outfit/123`)

