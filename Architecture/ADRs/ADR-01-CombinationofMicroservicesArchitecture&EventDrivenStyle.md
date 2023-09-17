## DR -01: Use combination of microservice architecture & event Driven
## Status: Accepted
## Context 
Road Warriors is a startup and the product need to upkeep the ever changing customer needs & market competition. The architecture should support evolving needs. A modular microservices architecture enables efficient change management & frequent rollouts. Additionally Different modules have different scalability needs. Microservices architecture enable to scale elstically and only those needed modules/components.

However Microservice Architecure will result in increased inter service communication which will affect peformance, whihc can be taken care by caching, replication & running additional service instances(pods).

Parts of the system may adopt Even driven architecure where the communicatoion can be asynchronous like Trip Synchronization, Data feeds from domain services into datalake.

Combination of microservice architecture & event Driven will make the system resilient and helps in business agility.

## Decision: 
Use combination of microservice architecture & Event driven architecture. Both the architecture styles can eo-exist in system.

## Consequencies
 Trade-off of performance due to Microservices increased inter service communication can be managed with dynamic service instances(pod) & scaling based on the runtime load. It will be additional cost but may be optimized.
