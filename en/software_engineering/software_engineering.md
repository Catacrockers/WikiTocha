[Go to Index page](https://github.com/Catacrockers/WikiTocha/blob/master/en/INDEX.md)

# Software Engineering

This sections lists a set of techniques (including theories, methods, processes, tools and languages) for developing and operating production software-intensive systems meeting defined standards of quality.

## Software Engineering
A good definition of software enginnering:

> The application of a systematic, disciplined, quantifiable approach to the development, operation, and maintenance of software"—IEEE Standard Glossary of Software Engineering Terminology

The need of software engineering appears to solve the issues of low quality software proyects. Software engineering defines software development lifecycle of a project, which can be sumarized in the following steps:

1. Communication of the project to the team
2. Requirement Gathering: Software Requirements Specification (SRS)
3. System Analysis 
4. Software Design: Architecture Description (AD)
5. Coding 
6. Testing (Idealy testing will be done at the same time as coding, TDD) 
7. Integration 
8. Deployment 
9. Operations and maintenance 

A powerful tool for generating those diagrams is [**plantuml**](http://plantuml.com/). 

## Software Requirements Specification (SRS)

A software requirements specification is a description of a software system to be developed. The software requirements specification lays out functional and non-functional requirements, and it may include a set of use cases that describe user interactions that the software must provide.

[IEEE 380](http://www.cse.msu.edu/~cse870/IEEEXplore-SRS-template.pdf) provides a standard for SRS. It is important that the first part of the SRS refelcts the business language and goals, and the business managers must agree with the requirements. 

The SRS is a **living document** that must reflect the current state of the project, and must be updated if requirements change during the project.

A common way of writing requirements is using **use cases**, because use cases also define a way to test the system later.

### Use cases

In software engineering, a use case is a list of actions or event steps typically defining the interactions between an actor and a system to achieve a goal. The actor can be a human or other external system. Use case analysis is a valuable requirement analysis technique that is often used in SRS and test plans. 

Some interesting books on use cases are
+ **Writing Effective Use Cases** - Alistair Cockburn
+ **USE-CASE 2.0** - Dr. Ivar Jacobson, Ian Spence, Kurt Bittner

Once the SRS is approved, it is time to start with **architecture description** and design.


## Architecture Description: Stakeholders and concerns

Architecture description defines the practices, techniques and types of representations used by software architects to record a software architecture. The [**ISO/IEC/IEEE 42010**](http://www.iso-architecture.org/ieee-1471/cm/) standard defines how to write an architecture description document.

Architecture models can take various forms, including text, informal drawings, diagrams or other formalisms. An architecture description will often employ several different **model kinds** to effectively address a variety of audiences, the **stakeholders** (such as end users, system owners, software developers, system engineers, program managers) and a variety of **architectural concerns** (such as functionality, safety, delivery, reliability, scalability).

ADs need to address concerns of relevance to many stakeholders. Some issues may be technical but many issues are not.

### Stakeholder's concerns, viewpoints and views

Stakeholders are individual, team, organizations, having an interest in a system. Stakeholders have **concerns** or interest in a system relevant to one or more of its stakeholders. A **concern** pertains to any influence on a system in its environment, including developmental, technological, business, operational, organizational, political, economic, legal, regulatory, ecological and social influences.

The models of an architecture description are organized into multiple **views** of the architecture such that "each view addresses specific concerns of interest to different stakeholders of the system". An **architecture viewpoint** frames one or more concerns and governs one architecture view. Each viewpoint is composed by one or more **model kinds**, notations and modeling conventions it utilizes.

## Architecture Description: model kinds

A **model kind** is a group of conventions for a type of modeling. An architecture view consists of multiple models, each following one model kind (diagrams, repositories, APIs, pictures, ). 

Some useful abd common models are:
- raml API
- JSON schema
- sequence diagram
- use case diagram
- state machine diagram
- activity diagram
- component diagram

## Architecture Decision Records

An architectural decision record (ADR) is a document that captures an important architectural decision made along with its context and consequences. The decision will have a status (proposed, accepted, denied). 

A modern version of ADR are [Lightweight Architecture Decision Records](https://www.thoughtworks.com/radar/techniques/lightweight-architecture-decision-records), which is a reduced and readable version of the decision records that is stored alongside source control for the sake of synchronicity with the code itself. 

## Verification & Validation: testing, test plan

## Monitoring: structured logging, centralized logs

