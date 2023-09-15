# ArchNinjas
Repository for Oreilly Arch Kata Competition -2023

About the team :
M1:
M2:
M3:
M4:
M5:

Diagrams:

User journey
![All-In-One-User Journey View drawio](https://github.com/nkpaladugu/ArchNinjas/assets/1698474/8e1cd38e-cd3d-4711-ae1b-f5ccededb8c3)

https://github.com/ArchNinjas/road-warrior/blob/main/Architecture/cj.svg

Logical Architecture

![Arch drawio](https://github.com/nkpaladugu/ArchNinjas/assets/1698474/3fd0004c-d154-4831-bb19-68015f3baad0)


Deployment Architecture

![DeployView](https://github.com/ArchNinjas/road-warrior/assets/145123235/afde4354-cae9-4f65-96a6-a3aeb6a63030)

Sequence Diagrams


ADRs

ADR -01: Use combination of microservice architecture & event Driven
Road Warriors is a startup and the product need to upkeep the ever changing customer needs & market competition. The architecture should support evolving needs. A modular micro services & even driven architecure gives the team flexibility to manage the change, automate testing & deploy frequently. Additionally Different modules has different scalability needs. MSA enable to scale elsticaly and only those needed modules/components. The inter service communication is event driven for resilincy and to contain the cascadong failures that may arise due to sync communication

Decision: We will use mix of MSA & EDA

Status:
Consequencies

ADR -02: Gateway pattern
Deploy the services behind an API gateway for rate limiting & Security.


ADR -03: CDC to Datawarehouse.

ADR -04: Edge Cache Service for better response times

ADR -04: React JS for Web & React Native for Mobile
