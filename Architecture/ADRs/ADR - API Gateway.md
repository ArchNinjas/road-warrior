# API Gateway

## Status - Accepted

## Context - 
RoadWarrior will provide their service using the Web and Mobile channels. The implementation will separate UI components from data exchange by implementing APIs for data access. These APIs need to be protected from malicious and unauthorized access, denial of service attacks, and in the case of partners ensure an agreed level of service.

An API Gateway can be deployed to solve these concerns. It can enable authenticated access to APIs, provide protection against a list of threats typically listed as OWASP Top 10, allow controlled access by partners, provide ability to segregate capacity by partner.


## Decision
Since the implication of a security breach has implications not just for level of service, but more importantly on reputation, RoadWarrior has decided to put in an API Gateway in all availability zones for redundancy.


## Consequences
Procuring and implementing an API gateway is additional cost and there will be additional steps required to be considered when rollout out new APIs or newer versions of APIs.

