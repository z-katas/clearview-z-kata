# Arch style for Matching Service
Date: 2024-09-29

## Status
Accepted

## Context
We are developing Matching services to run matching algorithm and find the matching job openings/resumes. This quanta is composed of the services that are responsible for performing the matching.

![image](https://github.com/user-attachments/assets/5e9da50f-8665-4217-a960-c1c2e06486e8)


### Alternatives
1. Event-driven
2. Modular Monlith

### PrOACT


| Factor | Modular Monolith | Event driven | Requirement |
|  | ----------- | ----------- | ---------- |
| Cost(time+money) | Low | High | Low
| Abstraction | Low | High | High
| Elasticity | Low        | High | High
| Scalability | Low        | High | High
| Performance | Medium | High | High

## Decision
The Matching quantum consists of Matching service and Matching Engine. The Match Engine is a batch app that triggers on a schedule to figure out the matches. The Matching Service is service that subscribes to events and performs CRUD operations on matches. Since the Matching engine needs to be highly scalable and highly performant, it would be prudent to separate it from Matching service.

## Tradeoffs - Mitigations
- **Cost**: Separating the services into different services might incur additional costs due to additional deployment and maintenance overhead 
  - *Mitigation*: We could initially implement it as event based micro kernel system and then scale it upto separate it into different services post MVP.
