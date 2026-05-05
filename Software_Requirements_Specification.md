# GrowKnow - Software Requirements Specification 

## Table of contents
- [Table of contents](#table-of-contents)
- [Introduction](#1-introduction)
    - [Purpose](#11-purpose)
    - [Scope](#12-scope)
    - [Definitions, Acronyms and Abbreviations](#13-definitions-acronyms-and-abbreviations)
    - [References](#14-references)
    - [Overview](#15-overview)
- [Overall Description](#2-overall-description)
    - [Vision](#21-vision)
    - [Use Case Diagram](#22-use-case-diagram)
	- [Technology Stack](#23-technology-stack)
- [Specific Requirements](#3-specific-requirements)
    - [Functionality](#31-functionality)
    - [Usability](#32-usability)
    - [Reliability](#33-reliability)
    - [Performance](#performance)
    - [Supportability](#35-supportability)
    - [Design Constraints](#36-design-constraints)
    - [Online User Documentation and Help System Requirements](#37-on-line-user-documentation-and-help-system-requirements)
    - [Purchased Components](#purchased-components)
    - [Interfaces](#39-interfaces)
    - [Licensing Requirements](#310-licensing-requirements)
    - [Legal, Copyright And Other Notices](#311-legal-copyright-and-other-notices)
    - [Applicable Standards](#312-applicable-standards)
- [Supporting Information](#4-supporting-information)

## 1. Introduction

### 1.1 Purpose
This Software Requirements Specification (SRS) describes the current GrowKnow documentation scope, including the project vision, key use cases, technology stack, and the boundary conditions for development and deployment.


### 1.2 Scope
GrowKnow is a modular web platform for **AI news**, **AI tool discovery**, and **structured learning paths** for IT professionals.

The current documented scope covers these high-level areas:

* **AI News Feed & Newsletter:** automated collection of AI-related news, deduplication, summarization, tagging, and newsletter generation.
* **AI Tool Directory:** curated AI tools organized by task, use case, and filtering metadata.
* **Role-Based Learning Roadmaps:** structured learning paths for IT roles such as Data Engineer, ML Engineer, DevOps, Backend Engineer, and Security Engineer.
* **Account & Feedback System:** user subscriptions, suggestions, and corrections *to review* if not yet implemented in the current release.
* **Administration & Data Pipelines:** admin review, content management, and n8n-driven ingestion workflows.

The documented actors are **Visitors**, **Registered Users**, **Admins**, and the **Automation Orchestrator (n8n)**.
  
### 1.3 Definitions, Acronyms and Abbreviations
| Abbrevation | Explanation                         |
|-------------|-------------------------------------|
| SRS         | Software Requirements Specification |
| UC          | Use Case                            |
| n/a         | not applicable                      |
| tbd         | to be determined                    |
| UCD         | overall Use Case Diagram            |
| FAQ         | Frequently asked Questions          |
| DRF         | Django REST Framework               |
| SPA         | Single-Page Application             |
| n8n         | Workflow automation platform        |
| RUP         | Rational Unified Process            |

### 1.4 References

| References                                                                                                                                                          |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [GrowKnow Documentation – Software Requirements Specification](https://github.com/bermar24/GrowKnow_Documentation/blob/main/Software_Requirements_Specification.md) |
| [GrowKnow Documentation – Software Architecture Document](https://github.com/bermar24/GrowKnow_Documentation/blob/main/Software_Architecture_Document.md)           |
| [GrowKnow Documentation – Artifact and Contributors Table](https://github.com/bermar24/GrowKnow_Documentation/blob/main/Artifact_Contributors_Table.md)             |
| [GrowKnow Documentation – Test Plan](https://github.com/bermar24/GrowKnow_Documentation/blob/main/Test_Plan.md)                                                     |
| [GrowKnow Blog](https://knowgrow7.wordpress.com/)                                                                                                                   |
| [GrowKnow Repository](https://github.com/bermar24/GrowKnow)                                                                                                         |


### 1.5 Overview
The following chapter provides an overview of this project with the vision and overall use case diagram. The third chapter (Requirements Specification) delivers more detail about functionality, usability, and design parameters. Finally, there is a chapter with supporting information.
    
## 2. Overall Description

### 2.1 Vision
We aim to build a central hub for AI professionals. The platform consolidates AI news, organizes tools by utility, and offers structured learning roadmaps. The goals are:
* Provide orientation without noise.
* Support faster and more confident technology decisions.
* Enable measurable progress in AI/IT learning paths.

The system is intended to evolve iteratively:
1. **Current documented MVP:** AI news browsing, search and filtering and newsletter triggering through n8n.
2. **Next phase:** expansion of the tool directory and roadmap coverage.
3. **Later:** more advanced feedback loops, contributor workflows, and extended automation.

### 2.2 Use Case Diagram

![OUCD](Diagrams/GrowKnow_Overal_UML_color.png)

- Yellow: Planned MVP 

### 2.3 Technology Stack
The technology stack used in the current documentation is:

**Frontend**
* React
* Vite
* TypeScript
* React Router

**Backend**
* Django
* Django REST Framework
* Python

**Automation**
* n8n
* Ollama
* Docker Compose

**Data Storage**

* SQLite for local development
* Supabase / PostgreSQL for hosted or production usage

**Search & Data Processing**

* OpenSearch / Elasticsearch when required

**Project Management**

* GitHub
* Rational Unified Process (RUP) iteration planning - YouTrack

**Testing**

* Behave / behave-django
* pytest / pytest-django
* Manual and automated checks for the news and filtering workflows

## 3. Specific Requirements

### 3.1 Functionality
This section explains the different use cases shown in the Use Case Diagram and their functionality.

Until the current documented MVP, we plan to implement:
- 3.1.1 Browse AI News
- 3.1.2 Admin Panel
- 3.1.3 Manage Database & Pipelines
- 3.1.4 Search & Filter Tools
- 3.1.5 Trigger Newsletter Run (via n8n)


For later releases we plan to implement:
- 3.1.6 Subscribe to Newsletter
- 3.1.7 Receive Weekly Newsletter
- 3.1.8 Suggest New Tools/Sources
- 3.1.9 Provide Feedback / Corrections
- 3.1.10 Manage Users & Roles
- 3.1.11 Explore Learning Roadmaps
- 3.1.12 Review/Edit/Publish Articles
- 3.1.13 Unsubscribe from Newsletter

#### 3.1.1 Browse AI News
Users can read and navigate through the latest AI news, which are automatically collected, summarized, and tagged.

This Use Case is specified in a [seperate document](UCs/3.1.1_Browse_AI_News.md).

#### 3.1.2 Admin Panel
Admins access a dashboard for managing users, roles, and platform-wide settings.

This Use Case is specified in a [seperate document](UCs/3.1.2_AdminPanel.md).

#### 3.1.3 Manage Database & Pipelines
Admins ensure the consistency and quality of stored news, tools, and roadmaps while managing automation pipelines.

This Use Case is specified in a [seperate document](UCs/3.1.3_Manage_Database_&_Pipelines.md).

#### 3.1.4 Search & Filter Tools
Users can search and filter through the AI tool directory using categories, domains, and budget.

This Use Case is specified in a [seperate document](UCs/3.1.4_Search_&_Filter_Tools.md).

#### 3.1.5 Trigger Newsletter Run
The automation orchestrator (n8n) can initiate newsletter generation and delivery.

This Use Case is specified in a [seperate document](UCs/3.1.5_TriggerNewsletterRun.md).

#### 3.1.6 Subscribe to Newsletter
Users can subscribe to receive the weekly newsletter.

#### 3.1.7 Receive Weekly Newsletter
Registered Users receive a curated newsletter summarizing the most relevant AI updates with source transparency.

#### 3.1.8 Suggest New Tools/Sources
Users can propose new tools or sources to be added to the directory.


#### 3.1.9 Provide Feedback / Corrections
Users can suggest corrections or improvements to existing content.


#### 3.1.10 Manage Users & Roles
Admins manage user accounts and assign or revoke roles.

#### 3.1.11 Explore Learning Roadmaps
Users can navigate role-based roadmaps (e.g., Data Engineer, ML Engineer) with structured paths and linked resources.

#### 3.1.12 Review/Edit/Publish Articles
Admins review automatically ingested articles before publishing them.

#### 3.1.13 Unsubscribe to Newsletter
Registered users can unsubscribe from the weekly newsletter.

### 3.2 Usability
We aim to design the GrowKnow platform with a clean, intuitive, and responsive interface. The user experience should feel natural, requiring no special training.

#### 3.2.1 No Training Time Needed
Users should be able to navigate the platform easily, discover tools, and subscribe without needing documentation.

#### 3.2.2 Familiar Feeling
By using standard UI/UX patterns, GrowKnow feels familiar to users accustomed to modern platforms, reducing friction in adoption.

### 3.3 Reliability

#### 3.3.1 Availability
The server shall be available 99% of the time. This also means we have to figure out the "rush hours" of our app because the downtime of the server is only tolerable when as few as possible players want to use the app.

#### 3.3.2 Defect Rate
Our goal is that we have no loss of any data.
 
### 3.4 Perfomance

#### 3.4.1 Capacity
The system should scale to handle thousands of concurrent visitors, with newsletter delivery supporting large mailing lists.

#### 3.4.2 Storage 
Stored data (tools, articles, feedback) should be optimized for efficiency without sacrificing accessibility.

#### 3.4.3 Response time
Pages and search queries should load within 1–2 seconds under normal load.

### 3.5 Supportability

#### 3.5.1 Coding Standards
We will follow industry best practices and clean code principles for both backend (Django) and frontend (React/Vite).

#### 3.5.2 Testing Strategy
The system will use automated testing for core functionalities such as news browsing, newsletter triggering, and search/filter behavior. Unit, integration, and pipeline tests should be used where applicable.

### 3.6 Design Constraints
* Modular architecture (frontend, backend, automation orchestrator).
* RESTful APIs for data exchange.
* Tech stack: React, Vite, Django, Django REST Framework, Supabase, n8n, and Ollama.
* Hosted on scalable cloud infrastructure or equivalent deployment targets *to review*.

### 3.7 On-line User Documentation and Help System Requirements
GrowKnow will provide contact forms or equivalent documentation routes. Most features are designed to be self-explanatory.

### 3.8 Purchased Components
We don't have any purchased components yet. If there will be purchased components in the future we will list them here.

### 3.9 Interfaces

#### 3.9.1 User Interfaces
The user interfaces that will be implemented are:
- Dashboard: lists AI news and tools with filters.
- Roadmap Page: displays curated learning roadmaps.
- Newsletter: subscription form and archive.
- Admin Panel: content, users, and pipeline management.
- Profile Page: user account management.

#### 3.9.2 Hardware Interfaces
(n/a)

#### 3.9.3 Software Interfaces
- Browser-based frontend.
- RESTful APIs for backend.
- Automation workflows via n8n.
- Optional Supabase client access when configured.

#### 3.9.4 Communication Interfaces
HTTP/HTTPS protocols for all interactions.

### 3.10 Licensing Requirements
All open-source components used will comply with MIT, Apache, or similar permissive licenses.

### 3.11 Legal, Copyright, and Other Notices
The GrowKnow logo and brand are reserved for this project. Third-party content remains subject to the original source terms.

### 3.12 Applicable Standards
The development will follow common clean code standards, naming conventions, and the documented API contracts. Additional project-specific standards are *to review*.

## 4. Supporting Information
For any further information you can contact the project team or check our [GrowKnow Blog](https://knowgrow7.wordpress.com/).  
The Team Members are:
- Joaquin Berriel Martins
- Emin Sengül *(left the project at the beginning of December 2025)*
- Roic *(left the project at the beginning of December 2025)*

<!-- Picture-Link definitions: -->
[OUCD]: https://github.com/bermar24/GrowKnow/Diagrams/GrowKnow_Overal_UML_color.png "Overall Use Case Diagram"
