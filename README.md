# ArchNinjas
## Repository for Oreilly Arch Kata Competition -2023
<!-- https://github.com/ArchNinjas/road-warrior -->
About the team :
1. Karthik
2. Thahir Ahmed
3. Narendra Paladugu
4. Rahul
5. Ramkumar

# Contents 
- [Introduction](#introduction)  
- [Business Case](#business-case)
    - [Requirements](#requirements)
    - [Constraints](#technical-constraints)
- [Architecture Characteristics](#architecture-characteristics) 
    - [Driving Characteristics](#driving-characteristics)
    - [Implicit Characteristics](#implicit-characteristics)
    - [Others Considered](#others-considered)
- [Architecture Approach](#architecture-approach)
    - [Goals](#goals)
- [Context](#context)  
    - [Actors](#actors)
    - [Use Cases](#use-cases)
    - [Event Storming](#event-storming)
- [Containers](#containers)
    - [Modular Monolith](#modular-monolith)
    - [Service Containers](#service-containers)
    - [API Layer](#api-layer)
- [Components](#components)
    - [Identity and Access Manager](#identity-and-access-manager)
    - [Profile Manager](#profile-manager)
    - [Connections Manager](#connections-manager)
    - [Rewards Manager](#rewards-manager)
    - [ETL Manager](#etl-manager)
    - [Reporting and Analytics Manager](#reporting-and-analytics-manager)
    - [Social Media API Manager](#social-media-api-manager)
- [Deployment](#deployment)
- [Cost Analysis](#cost-analysis)
- [Evaluation, Risks and Architecture Fitness](#evaluation-risks-and-architecture-fitness)  
- [ADRs](#adrs)
- [References](#references)


## Introduction

Road Warrior is on a mission to transform the way you plan and enjoy travel. As a dynamic and innovative travel management startup, our vision is to rank among the top three travel aggregator apps, offering a comprehensive solution for all your travel requirements.

Road Warrior is meticulously crafted to simplify booking, itinerary planning, and on road support, all within a single, user-friendly interface on web & mobile. Whether you're pursuing wanderlust, relaxation, or business trip, we've got your travel needs covered.

## Business Case
### Requirements

### Constraints

As a start up, Road warrior wanted to start small be elastic and dynamic to rollour globally with continuous improvements. In thi journey platform stability, consist user experience on cross platforms and beating the competition with value added services are key all the wihile Road Warrior team also need to be mindful about technology investment yet be ready for elastic scale.

## Architecture Characteristics

The following section highlights important architecure characteristics for successful implementation of the product.

| Top 3 | Characteristics                   | Design Consideration                                                                                                                                     | Design Decisions                                                                                                                                                                                                                                                                                                                                                                                        |
|-------|-----------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| - [*] | Availability                      | <ol><li>Road Warrior be available 24/7 for users. </li> <li> Un interrupted Service avaiability even during deployement </li> <li> 5 min unplanned downtime per month may be allowed</li> </ol> | <ol> <li> System Availability <ul> <li> Multi availability zone (data center) across region </li> <li> Each availability zone has multiple subnets across layers (web, app, persistent) </li> </ul> </li> <li> Service Availability <ul> <li> Containerized platform with autoscaling</li> </ul> </li> <li> Network Availability <ul> <li> VPN over internet with failover channels </li> </ul> </li>  </ol> |
| - [*] | Elasticity                        | 2 million active user base                                                                                                                               | Containerized platform with autoscaling                                                                                                                                                                                                                                                                                                                                                                 |
| - []  | Performance                       | <ol> <li> Response time for web (800ms) </li> <li> First contentful paint of under 1.4sec </li> </ol>                                                    | System Design <ol> <li> Process real-time feed from external systems with Event driven patterns </li> </ol>                                                                                                                                                                                                                                                                                             |
| - [*] | Data consistency & Data Integrity | System to interface with the agencies existing airline, hotel, car rental systems to update travel details                                               | <ol> <li> System Design <ul> <li> Events from external systems are captured in database and retriggered during failure. </li> </ul></li> <li>  Network Design <ol> <li> VPN over internet with failover channels</li></ol> </li> <ol>                                                                                                                                                                   |
| - []  | Responsiveness                    | <ol> <li> Response time for web (800ms) </li> <li> First contentful paint of under 1.4sec </li> </ol>                                                    | <ol> <li> Lazy loading </li> <li> Edge location based CDN components across region. </li> </ol>                                                                                                                                                                                                                                                                                                         |
| - []  | Security                          | Implicit                                                                                                                                                 | <ol> <li> Access control for users </li> <li> Three tier architecture to split public and private subnets. </li> <li> Every interface with external system follows secure VPN design. </li><li> All network calls are SSL enabled. </li> <li> Payload sent/received from external system to be encrypted/decryted. </li> </ol>                                                                          |

## Architecture Approach

Before we take an approach, let's be reminded about the platform goals and constraints. Top 2 golas are 1. Start Small and scale as needed 2.Frequent and stable feature releases to be among top three travel apps. Limited funding is a constraint, the platform needs to generate revenue from the acumulated data, ethically and responsibly.

![Alt text](ArchitecturStyleSelection.PNG)


![cj](https://github.com/ArchNinjas/road-warrior/blob/main/Architecture/cj.svg)

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
Change data capture(CDC) empowers businesses to move at the speed of their data. CDC instantly and automatically syncs databases as soon as the source data changes.Change data capture enables faster, more accurate business decisions while minimizing resource expenditure. The technology’s instantaneous data updates, cost-effective incremental changes, and light IT footprint offers a win-win-win to businesses. With the right CDC technology, companies can leave the inefficiencies of bulk processing behind, forever.

ADR -04: Edge Cache Service for better response times

ADR -04: React JS for Web & React Native for Mobile
