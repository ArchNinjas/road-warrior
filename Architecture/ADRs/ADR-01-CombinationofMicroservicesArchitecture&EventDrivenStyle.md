## DR -01: Use combination of microservice architecture & event Driven
## Status: Accepted
## Context 
Road Warriors is a startup and the product need to upkeep the ever changing customer needs & market competition. The architecture should support evolving needs. A modular micro services architecture enables frequent changes & frequent rollouts. Additionally Different modules has different scalability needs. MSA enable to scale elsticaly and only those needed modules/components.

However Microservice Architecure will result in many inter service communication which will affect peromance.

Parts of the system may adopt Even driven architecure where the communicatoion can be asynchronous like Trip Synchronization, Data feeds from domain services into datalake.

Combination of microservice architecture & event Driven will help.

## Decision: 


## Consequencies
 Trade-off of performance due to inter service communication can be managed with dynamic pod scaling based on the runtime workload