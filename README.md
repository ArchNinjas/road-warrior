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

| Top 3 | Architectural Characteristic                   |  Considerations                                                                                                                                     | Design Decisions                                                                                                                                                                                                                                                                                                                                                                                        |
|-------|-----------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| - [*] | Availability                      | <ol><li>Road Warrior be available 24/7 for users. </li> <li> Un interrupted Service avaiability even during deployement </li> <li> ~5 min unplanned downtime per month may be allowed</li> </ol> | <ol> <li> System Availability <ul> <li> Multi availability zone (data center) across region </li> <li> Each availability zone has multiple subnets across layers (web, app, persistent) </li> </ul> </li> <li> Service Availability <ul> <li> Containerized platform with autoscaling</li> </ul> </li> <li> Network Availability <ul> <li> Different edge location and available zone to make sure the road warrior is avilable across the globe </li> </ul> </li>  </ol> |
| - [*] | Elasticity                        | 2 million active user base                                                                                                                               | Containerized platform with autoscaling                                                                                                                                                                                                                                                                                                                                                                 |
| - []  | Performance                       | <ol> <li> Response time for web (800ms) </li> <li> First contentful paint of under 1.4sec </li> </ol>                                                    | System Design <ol> <li> Process real-time feed from external systems with Event driven patterns </li> </ol>                                                                                                                                                                                                                                                                                             |
| - [*] | Data consistency & Data Integrity | System to interface with the agencies existing airline, hotel, car rental systems to update travel details                                               | <ol> <li> System Design <ul> <li> Events from external systems are captured in database and retriggered during failure. </li> </ul></li> <li>  Network Design <ol> <li>Different edge location and available zone to make sure the road warrior is avilable across the globe  </li></ol> </li> <ol>                                                                                                                                                                   |
| - []  | Responsiveness                    | <ol> <li> Response time for web (800ms) </li> <li> First contentful paint of under 1.4sec </li> </ol>                                                    | <ol> <li> Lazy loading </li> <li> Edge location based CDN components across region. </li> </ol>                                                                                                                                                                                                                                                                                                         |
| - []  | Security                          | Implicit                                                                                                                                                 | <ol> <li> Access control for users </li> <li> Three tier architecture to split public and private subnets. </li> <li> Every interface with external system follows secure VPN design. </li><li> All network calls are SSL enabled. </li> <li> Payload sent/received from external system to be encrypted/decryted. </li> </ol>                                                                          |

## Architecture Approach

Before we take an approach, let's be reminded about the platform goals and constraints. Top 2 golas are 1. Start small and scale as needed 2.Frequent and stable feature releases to be among top three travel apps. Limited funding is a constraint, the platform needs to generate revenue from the acumulated data, ethically and responsibly.

![Alt text](ArchitecturStyleSelection.PNG)

Considering the product goals & constraints, a combination of Microservices architecture & Even Driven Architecture style is considered. Performance may take hit due to inter service communication but it is manageble trade off. Event driven architecture paired with microservices architecture makes the product better performant & resilient. Pefrmance may be further managed by spinning off the additional runtime pods dynamically. See ADR-1 for further details.

![cj](https://github.com/ArchNinjas/road-warrior/blob/main/Architecture/cj.svg)

Logical Architecture

![Arch drawio](https://github.com/nkpaladugu/ArchNinjas/assets/1698474/3fd0004c-d154-4831-bb19-68015f3baad0)


Deployment Architecture

![DeployView](https://github.com/ArchNinjas/road-warrior/assets/145123235/afde4354-cae9-4f65-96a6-a3aeb6a63030)

Sequence Diagrams

## Components

## CHAT BOT  

Using a chatbot effectively involves careful planning, ongoing monitoring, and a commitment to improving the user experience. When executed well, chatbots can enhance customer service, streamline operations, and provide valuable insights into user behavior and preferences.
Protect user data and privacy by implementing security measures and complying with relevant data protection regulations like GDPR or HIPAA, depending on your industry.Incorporating a chatbot into our raod Warrior is a testament to our commitment to providing unparalleled service to our clients. We believe that this innovative addition will not only enhance experience but also make it more efficient, cost-effective, and enjoyable. 

Human Touch When Needed: While the chatbot handles most tasks, our human customer center are always available for complex queries or situations where a personal touch is required.

Cost Savings: By automating routine tasks and reducing the workload on our human travel agents, we can pass on cost savings to our clients. This allows us to offer competitive pricing and excellent value for money.

Data Insights: The chatbot collects valuable data on traveler preferences, trends, and common pain points. This data helps us continually improve our services and offerings.

![CB](https://github.com/ArchNinjas/road-warrior/blob/main/Architecture/chatbot.png)

ADRs

A

ADR -02: Gateway pattern
Deploy the services behind an API gateway for rate limiting & Security.


ADR -03: CDC to Datawarehouse.
Change data capture(CDC) empowers businesses to move at the speed of their data. CDC instantly and automatically syncs databases as soon as the source data changes.Change data capture enables faster, more accurate business decisions while minimizing resource expenditure. The technology’s instantaneous data updates, cost-effective incremental changes, and light IT footprint offers a win-win-win to businesses. With the right CDC technology, companies can leave the inefficiencies of bulk processing behind, forever.

ADR -04: Edge Cache Service for better response times

ADR -04: React JS for Web & React Native for Mobile
