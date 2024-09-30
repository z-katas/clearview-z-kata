# Arch style for Matching Service

Date: 2024-09-29

## Status

Accepted

## Context

We are developing Matching services to run matching algorithm and find the matching job openings/resumes. This quanta is composed of the services that are responsible for performing the matching.

### Alternatives

1. Event-driven
2. Modular Monolith
3. Micro Services

### PrOACT

| Factor           | Modular Monolith | Event driven | Micro Services | Requirement |
| ---------------- | ---------------- | ------------ | -------------- | ----------- |
| Cost(time+money) | Low              | High         | High           | Low         |
| Abstraction      | Low              | High         | Low            | High        |
| Elasticity       | Low              | High         | High           | High        |
| Scalability      | Low              | High         | High           | High        |
| Performance      | Medium           | High         | Low            | High        |

## Decision

The Matching quantum consists of Matching service and Matching Engine. The Match Engine is a batch app that triggers on a schedule to figure out the matches. The Matching Service is service that subscribes to events and performs CRUD operations on matches. Since the Matching engine needs to be highly scalable and highly performant, it would be prudent to separate it from Matching service.

## Tradeoffs - Mitigations

- **Cost**: Separating the services into different services might incur additional costs due to additional deployment and maintenance overhead
  - _Mitigation_: We could initially implement it as event based modular monolith system and then scale it upto separate it into micro services post MVP.
