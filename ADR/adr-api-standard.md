# API Standard
Date: 2024.09.24

## Status
Accepted

## Context

Frontend apps (web and mobile) of the clearview platform communicate with the platform services to fetch and mutate data. Service APIs determine the interoperability between services and the apps. So, it becomes essential to choose the right API standard to support the use-cases and provide better responsiveness and usability of the apps.

### Alternatives

- REST
- Graphql
- gRPC

### PrOACT

| Criteria             | REST                       | Graphql                           | gRPC                                      |
| -------------------- | -------------------------- | --------------------------------- | ----------------------------------------- |
| Feasibility          | high                       | high                              | low                                       |
| Latency              | higher                     | higher                            | lower                                     |
| Client/app friendly  | no                         | very much                         | no                                        |
| Maturity,Maintenance | matured                    | actively improving                | actively improving                        |
| Community            | Old and large market users | growing community                 | growing community                         |
| Adaptability         | easily adaptable           | slight friction for new consumers | less likely adaptable as it is fairly new |

## Decision

**Use REST, Graphql and gRPC**.

- Graphql APIs solve problems of over-fetching and under-fetching, making it extremely convenient, especially for mobile apps. This will optimize performance slightly due to a smaller payload over mobile networks. Further, since Graphql is schema-based, it can help achieve type-safety with service APIs.
- REST APIs are resource-oriented and have been around for decades. Third-party users or NGOs might feel it easy to integrate with the Spotlight platform using REST. REST should be standard for all public facing APIs and the APIs consumed by graphQL layer
- gRPC APIs are well designed for internal service to service communication and generally faster compared to other standards as it used http2.0 under the hood. Strongly typed protobufs are helpful in identifying breaking changes between internal APIs

## Tradeoffs - Mitigations

- Supporting multiple API standards will add an infrastructure overhead.
  - Mitigation - Initially, introduce Graphql on just the [backend-for-frontend(BFF)] service to support the Clearview web/mobile app. All the other platform services can start with supporting gRPC for internal communication and REST for external communication, and the BFF can talk to these services via gRPC. Long term, the platform services can support Graphql as well the existing infra can be migrated to a Graphql federation design.
