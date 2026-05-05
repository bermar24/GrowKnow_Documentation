# Test Plan Template
## Table of contents
- [1. Introduction](#1-introduction)
  * [1.1 Purpose](#11-purpose)
  * [1.2 Scope](#12-scope)
  * [1.3 Intended Audience](#13-intended-audience)
  * [1.4 Document Terminology and Acronyms](#14-document-terminology-and-acronyms)
  * [1.5  References](#15--references)
  * [1.6 Document Structure](#16-document-structure)
- [2. Evaluation Mission and Test Motivation](#2-evaluation-mission-and-test-motivation)
  * [2.1 Background](#21-background)
  * [2.2 Evaluation Mission](#22-evaluation-mission)
  * [2.3 Test Motivators](#23-test-motivators)
- [3. Target Test Items](#3-target-test-items)
- [4. Outline of Planned Tests](#4-outline-of-planned-tests)
  * [4.1 Outline of Test Inclusions](#41-outline-of-test-inclusions)
  * [4.2 Outline of Other Candidates for Potential Inclusion](#42-outline-of-other-candidates-for-potential-inclusion)
  * [4.3 Outline of Test Exclusions](#43-outline-of-test-exclusions)
- [5. Test Approach](#5-test-approach)
  * [5.1 Initial Test-Idea Catalogs and Other Reference Sources](#51-initial-test-idea-catalogs-and-other-reference-sources)
  * [5.2 Testing Techniques and Types](#52-testing-techniques-and-types)
    + [5.2.1 Data and Database Integrity Testing](#521-data-and-database-integrity-testing)
    + [5.2.2 Functional Testing](#522-functional-testing)
    + [5.2.3 Business Cycle Testing](#523-business-cycle-testing)
    + [5.2.4 User Interface Testing](#524-user-interface-testing)
    + [5.2.5 Performance Profiling](#525-performance-profiling)
    + [5.2.6 Load Testing](#526-load-testing)
    + [5.2.7 Stress Testing](#527-stress-testing)
    + [5.2.8 Volume Testing](#528-volume-testing)
    + [5.2.9 Security and Access Control Testing](#529-security-and-access-control-testing)
    + [5.2.10 Failover and Recovery Testing](#5210-failover-and-recovery-testing)
    + [5.2.11 Configuration Testing](#5211-configuration-testing)
    + [5.2.12 Installation Testing](#5212-installation-testing)
- [6. Entry and Exit Criteria](#6-entry-and-exit-criteria)
  * [6.1 Test Plan](#61-test-plan)
    + [6.1.1 Test Plan Entry Criteria](#611-test-plan-entry-criteria)
    + [6.1.2 Test Plan Exit Criteria](#612-test-plan-exit-criteria)
    + [6.1.3 Suspension and Resumption Criteria](#613-suspension-and-resumption-criteria)
  * [6.2 Test Cycles](#62-test-cycles)
      - [6.2.1 Test Cycle Entry Criteria](#621-test-cycle-entry-criteria)
      - [6.2.2 Test Cycle Exit Criteria](#622-test-cycle-exit-criteria)
      - [6.2.3 Test Cycle Abnormal Termination](#623-test-cycle-abnormal-termination)
- [7. Deliverables](#7-deliverables)
- [7.1 Test Evaluation Summaries](#71-test-evaluation-summaries)
- [7.2 Reporting on Test Coverage](#72-reporting-on-test-coverage)
- [7.3 Perceived Quality Reports](#73-perceived-quality-reports)
- [7.4 Incident Logs and Change Requests](#74-incident-logs-and-change-requests)
- [7.5 Smoke Test Suite and Supporting Test Scripts](#75-smoke-test-suite-and-supporting-test-scripts)
- [7.6      Additional Work Products](#76------additional-work-products)
  * [7.6.1     Detailed Test Results](#761-----detailed-test-results)
  * [7.6.2     Additional Automated Functional Test Scripts](#762-----additional-automated-functional-test-scripts)
  * [7.6.3     Test Guidelines](#763-----test-guidelines)
  * [7.6.4     Traceability Matrices](#764-----traceability-matrices)
- [8. Testing Workflow](#8-testing-workflow)
- [9. Environmental Needs](#9-environmental-needs)
  * [9.1 Base System Hardware](#91-base-system-hardware)
  * [9.2 Base Software Elements in the Test Environment](#92-base-software-elements-in-the-test-environment)
  * [9.3 Productivity and Support Tools](#93-productivity-and-support-tools)
  * [9.4 Test Environment Configurations](#94-test-environment-configurations)
- [10. Responsibilities, Staffing, and Training Needs](#10-responsibilities-staffing-and-training-needs)
  * [10.1 People and Roles](#101-people-and-roles)
  * [10.2 Staffing and Training Needs](#102-staffing-and-training-needs)
- [11. Iteration Milestones](#11-iteration-milestones)
- [12. Risks, Dependencies, Assumptions, and Constraints](#12-risks-dependencies-assumptions-and-constraints)
- [13. Management Process and Procedures](#13-management-process-and-procedures)
## 1. Introduction
### 1.1 Purpose
The purpose of this Iteration Test Plan is to define how GrowKnow will be tested during the current iteration and how test execution will be controlled through the pull-request workflow.
This Test Plan supports the following objectives:
- identify the items that should be targeted by the tests,
- identify the motivation for the test areas to be covered,
- outline the testing approach that will be used,
- identify the required resources and estimate the test effort,
- ensure that PRs are blocked until BDD tests and the SonarQube Cloud quality gate pass.
### 1.2 Scope
This Test Plan covers the current documented GrowKnow scope:
- React/Vite frontend browsing and navigation,
- Django REST backend API behavior,
- BDD scenarios in `.features` files and step definitions,
- GitHub Actions validation for pull requests,
- SonarQube Cloud quality gate checks,
- smoke-level regression tests for the supported core flows.
The following areas are excluded or deferred unless they become explicitly required:
- performance, load, stress, and volume testing,
- failover and recovery testing,
- installation testing,
- advanced accessibility certification,
- production monitoring and operations testing.
### 1.3 Intended Audience
This document is intended for the project team, reviewers, and anyone responsible for validating or maintaining GrowKnow.
Primary readers include developers who write or update tests, reviewers who approve pull requests, and maintainers who monitor GitHub Actions and SonarQube Cloud results.
The document is also useful for stakeholders who need a concise view of what is tested, what is excluded, and what gates must pass before merge.
### 1.4 Document Terminology and Acronyms
| Abbr | Abbreviation                        |
|------|-------------------------------------|
| API  | Application Programming Interface   |
| BDD  | Behavior-Driven Development         |
| CI   | Continuous Integration              |
| CD   | Continuous Delivery/Deployment      |
| DRF  | Django REST Framework               |
| PR   | Pull Request                        |
| QA   | Quality Assurance                   |
| SRS  | Software Requirements Specification |
| SAD  | Software Architecture Document      |
| UI   | User Interface                      |
| n8n  | Workflow automation platform        |
| n/a  | not applicable                      |
| tbd  | to be determined                    |
| VC   | Version Control                     |
### 1.5  References
| Title | Date | Publishing organization |
| --- | :---: | --- |
| [GrowKnow README](README.md) | n/a | GrowKnow Documentation |
| [Software Requirements Specification](Software_Requirements_Specification.md) | n/a | GrowKnow Documentation |
| [Software Architecture Document](Software_Architecture_Document.md) | n/a | GrowKnow Documentation |
| [Artifact and Contributors Table](Artifact_Contributors_Table.md) | n/a | GrowKnow Documentation |
| [Browse AI News Use Case](UCs/3.1.1_Browse_AI_News.md) | n/a | GrowKnow Documentation |
| [Admin Panel Use Case](UCs/3.1.2_AdminPanel.md) | n/a | GrowKnow Documentation |
| [Manage Database & Pipelines Use Case](UCs/3.1.3_Manage_Database_&_Pipelines.md) | n/a | GrowKnow Documentation |
| [Search & Filter Tools Use Case](UCs/3.1.4_Search_&_Filter_Tools.md) | n/a | GrowKnow Documentation |
| [Trigger Newsletter Run Use Case](UCs/3.1.5_TriggerNewsletterRun.md) | n/a | GrowKnow Documentation |
| GitHub Actions workflow | n/a | GrowKnow Repository |
| SonarQube Cloud project | n/a | SonarSource |
### 1.6 Document Structure
Section 1 describes the purpose, scope, audience, terminology, and references.
Section 2 explains why testing is needed and what motivates the current iteration.
Section 3 lists the items targeted for testing.
Section 4 summarizes included, possible, and excluded test areas.
Section 5 describes the test approach and techniques.
Sections 6 through 13 cover entry/exit criteria, deliverables, workflow, environment, roles, milestones, risks, and management procedures.
## 2. Evaluation Mission and Test Motivation
### 2.1 Background
GrowKnow is a modular documentation-backed project for AI news browsing, AI tool discovery, and structured learning paths.
The current implementation combines a React/Vite frontend, a Django REST backend, and n8n-driven ingestion workflows.
Testing is required to ensure that the documented core flows still work as the project evolves.
In particular, the team needs to protect the accepted feature scenarios, prevent regressions in API behavior, and keep the PR workflow trustworthy.
Automated BDD scenarios are already used as a gate in GitHub Actions, and SonarQube Cloud is used to block pull requests until the quality gate passes.
### 2.2 Evaluation Mission
The mission of this test effort is to verify the documented GrowKnow requirements, catch regressions before merge, and provide confidence that pull requests are safe to integrate.
The test effort should:
- find important bugs and regressions early,
- verify the implemented behavior against the `.features` files,
- confirm that CI checks are reliable,
- support maintainable code through quality-gate enforcement.
### 2.3 Test Motivators
The main motivators for testing are:
- use-case coverage for the documented core flows,
- correctness of API responses and data handling,
- confidence in the BDD acceptance scenarios,
- protection against broken pull requests,
- SonarQube Cloud quality gate compliance,
- stable behavior of the frontend pages used for browsing and filtering.
## 3. Target Test Items
The primary test items are:
- React/Vite frontend pages and shared components,
- Django REST API endpoints and serializers,
- backend models and database interactions,
- BDD `.features` files and step definitions,
- GitHub Actions workflow that runs the BDD tests,
- SonarQube Cloud analysis configuration and quality gate behavior,
- core documentation-driven use cases in `UCs/`,
- smoke checks for the AI News, search/filter, admin, and pipeline-related flows.
## 4. Outline of Planned Tests
### 4.1 Outline of Test Inclusions
Planned testing includes:
- unit tests for backend logic where available,
- API-level tests for Django REST endpoints,
- BDD acceptance tests driven by `.features` files,
- UI smoke tests for the documented browser flows,
- database integrity checks for stored content and relationships,
- GitHub Actions validation for every pull request,
- SonarQube Cloud quality gate enforcement before merge.
### 4.2 Outline of Other Candidates for Potential Inclusion
Potential future candidates include:
- accessibility checks,
- end-to-end browser automation beyond the current BDD coverage,
- performance profiling,
- load and resilience tests,
- installer validation on supported platforms.
### 4.3 Outline of Test Exclusions
The following are excluded from the current test plan unless they become explicitly required:
- load testing,
- stress testing,
- volume testing,
- failover and recovery testing,
- installation testing,
- production monitoring validation.
These tests are not part of the current documented CI-driven acceptance workflow.
## 5. Test Approach
### 5.1 Initial Test-Idea Catalogs and Other Reference Sources
The main sources for test ideas are:
- the SRS,
- the Software Architecture Document,
- the use-case documents in `UCs/`,
- the existing `.features` files and step definitions,
- GitHub Actions workflow definitions,
- SonarQube Cloud quality rules and gate results.
### 5.2 Testing Techniques and Types
#### 5.2.1 Data and Database Integrity Testing
|                       | Description |
|-----------------------|-------------|
| Technique Objective    | Verify that stored news, tools, and related records are created, updated, and read correctly. |
| Technique              | Use Django test cases and API-level checks to validate model persistence, serializer output, and relationship integrity with valid and invalid data. |
| Oracles                | Expected HTTP responses, database assertions, and fixture comparisons. |
| Required Tools         | Django test runner, pytest, database fixtures, and test database. |
| Success Criteria       | All critical model and persistence checks pass without data corruption. |
| Special Considerations | n/a |
#### 5.2.2 Functional Testing
|                       | Description |
|-----------------------|-------------|
| Technique Objective    | Verify the documented use cases and user-visible behavior. |
| Technique              | Execute the current BDD scenarios and targeted API checks for AI News browsing, filtering, admin actions, and newsletter triggering. |
| Oracles                | Feature file expectations, API response codes, and visible UI results. |
| Required Tools         | Behave, behave-django, Django REST test client, frontend test helpers. |
| Success Criteria       | All prioritized BDD scenarios and related functional checks pass. |
| Special Considerations | The `.features` files are treated as the acceptance baseline. |
#### 5.2.3 Business Cycle Testing
n/a
#### 5.2.4 User Interface Testing
|                       | Description |
|-----------------------|-------------|
| Technique Objective    | Verify that the browser UI is usable, consistent, and correctly wired to the backend. |
| Technique              | Check the main screens, navigation, list rendering, empty states, and error states in the frontend. |
| Oracles                | Manual review, browser assertions, and snapshot or smoke checks where available. |
| Required Tools         | Browser, frontend test helpers, and the running frontend app. |
| Success Criteria       | Core screens render and navigate as expected. |
| Special Considerations | n/a |
#### 5.2.5 Performance Profiling
n/a
#### 5.2.6 Load Testing
n/a
#### 5.2.7 Stress Testing
n/a
#### 5.2.8 Volume Testing
n/a
#### 5.2.9 Security and Access Control Testing
|                       | Description |
|-----------------------|-------------|
| Technique Objective    | Verify that protected actions and administrative paths are only available to the appropriate roles. |
| Technique              | Check role-based access for admin features and confirm that public/read-only paths stay restricted to their expected level. |
| Oracles                | HTTP status codes, denied-access responses, and role-based UI behavior. |
| Required Tools         | Django test client, role fixtures, and BDD scenarios where relevant. |
| Success Criteria       | Unauthorized access is blocked and authorized access works as expected. |
| Special Considerations | n/a |
#### 5.2.10 Failover and Recovery Testing
n/a
#### 5.2.11 Configuration Testing
|                       | Description |
|-----------------------|-------------|
| Technique Objective    | Verify that the documented development and CI configurations can run the tests successfully. |
| Technique              | Run the test suite on the supported Linux-based setup and in GitHub Actions. |
| Oracles                | Successful pipeline completion and reproducible local execution. |
| Required Tools         | Linux environment, Python, Node.js, npm, browser, GitHub Actions. |
| Success Criteria       | Tests can be reproduced locally and in CI. |
| Special Considerations | Windows users should use WSL2 when following the Linux-based setup. |
#### 5.2.12 Installation Testing
n/a
## 6. Entry and Exit Criteria
### 6.1 Test Plan
#### 6.1.1 Test Plan Entry Criteria
- the current requirements and use cases are available,
- the feature files and step definitions are present,
- the CI workflow and SonarQube Cloud project are configured,
- the test environment can run the required tools.
#### 6.1.2 Test Plan Exit Criteria
- the planned BDD and functional tests have been executed,
- the GitHub Actions workflow passes on the PR,
- the SonarQube Cloud quality gate passes,
- any critical defects have been addressed or deferred with approval.
#### 6.1.3 Suspension and Resumption Criteria
Testing may be suspended if the environment is unavailable, the CI pipeline is broken, or prerequisite test data is missing.
Testing may resume once the blocking issue is fixed and the affected checks can run again.
### 6.2 Test Cycles
#### 6.2.1 Test Cycle Entry Criteria
- a pull request has been opened or updated,
- the relevant tests are ready,
- the branch can run the project checks locally or in CI.
#### 6.2.2 Test Cycle Exit Criteria
- all required BDD tests pass,
- the SonarQube Cloud quality gate passes,
- no open critical or blocker issues remain for the PR.
#### 6.2.3 Test Cycle Abnormal Termination
A test cycle is considered abnormally terminated if the workflow fails for environmental reasons, required services are unavailable, or a blocker prevents completion of the CI gate.
## 7. Deliverables
### 7.1 Test Evaluation Summaries
n/a
### 7.2 Reporting on Test Coverage
Coverage is reported through the CI workflow output, test logs, and SonarQube Cloud dashboards.
The team should review coverage results for each pull request and summarize meaningful changes when releasing a new iteration.
### 7.3 Perceived Quality Reports
n/a
### 7.4 Incident Logs and Change Requests
Test incidents and change requests are recorded in the repository issue tracker or in pull-request comments, depending on the nature of the issue.
### 7.5 Smoke Test Suite and Supporting Test Scripts
The smoke suite consists of the most important BDD feature files and any minimal scripts needed to verify the core application flow.
### 7.6      Additional Work Products
n/a
#### 7.6.1     Detailed Test Results
n/a
#### 7.6.2     Additional Automated Functional Test Scripts
The automated functional tests are maintained as `.features` files and step definitions in the project repository.
#### 7.6.3     Test Guidelines
n/a
#### 7.6.4     Traceability Matrices
n/a
## 8. Testing Workflow
The testing workflow is:
1. update the feature or code change,
2. run the relevant local checks,
3. commit and open a pull request,
4. let GitHub Actions run the BDD test suite,
5. review the SonarQube Cloud quality gate,
6. fix failures and re-run until both gates pass,
7. merge only after review and green checks.
## 9. Environmental Needs
### 9.1 Base System Hardware
A developer machine or CI runner capable of running the GrowKnow tests is required.
Exact server sizing is n/a for this plan.
### 9.2 Base Software Elements in the Test Environment
| Software Element Name | Type and Other Notes |
|-----------------------|----------------------|
| Python | Runtime for backend tests and step definitions |
| Node.js / npm | Frontend tooling and workflow support |
| Django | Backend framework |
| Django REST Framework | API testing support |
| Behave / behave-django | BDD test execution |
| pytest / pytest-django | Unit and integration testing |
| GitHub Actions | PR automation |
| SonarQube Cloud | Quality gate enforcement |
| Browser | Frontend verification |
| n/a | Other items not currently required |
### 9.3 Productivity and Support Tools
| Tool Category or Type             | Tool Brand Name | Vendor or In-house | Version |
|-----------------------------------|-----------------|--------------------|---------|
| Test Management                   | GitHub Issues / PRs | In-house | n/a |
| Defect Tracking                   | GitHub Issues | In-house | n/a |
| ASQ Tool for functional testing   | Behave | Open source | n/a |
| ASQ Tool for performance testing  | n/a | n/a | n/a |
| Test Coverate Monitor or Profiler | SonarQube Cloud | SonarSource | n/a |
| Project Management                | GitHub | GitHub | n/a |
| DBMS tools                        | Django test DB / SQLite / Supabase tools | In-house | n/a |
### 9.4 Test Environment Configurations
| Configuration Name                | Description | Implemented in Physical Configuration |
|-----------------------------------|-------------|---------------------------------------|
| Average user configuration        | Standard developer laptop or CI runner | Yes |
| Minimal configuration supported   | n/a | n/a |
| Visually and mobility challenged  | n/a | n/a |
| International Double Byte OS      | n/a | n/a |
| Network installation (not client) | CI execution through GitHub Actions | Yes |
## 10. Responsibilities, Staffing, and Training Needs
### 10.1 People and Roles
| Human Resources |  |  |
|---|---:|---|
| Role | Minimum Resources Recommended (number of full-time roles allocated) | Specific Responsbilities or Comments |
| Test Manager | 1 | Coordinates the test plan, checks status, and ensures the gates are enforced. |
| Test Analyst | 1 | Translates SRS and use cases into test ideas and BDD scenarios. |
| Test Designer | 1 | Defines the structure of feature coverage and test automation. |
| Tester | 1 | Runs and maintains the BDD suite, smoke checks, and regression checks. |
| Test System Administrator | n/a | n/a |
| Database Administrator, Database Manager | n/a | n/a |
| Designer | n/a | n/a |
| Implementer | n/a | n/a |
### 10.2 Staffing and Training Needs
The team needs working knowledge of Behave, Django test tooling, GitHub Actions, and SonarQube Cloud.
Training is mostly just-in-time and should happen when a new workflow, test pattern, or quality rule is introduced.
## 11. Iteration Milestones
- BDD scenarios updated for the current iteration.
- Pull request workflow runs successfully in GitHub Actions.
- SonarQube Cloud quality gate passes before merge.
- Target code coverage for the exercised test areas should stay above 80% *to review*.
## 12. Risks, Dependencies, Assumptions, and Constraints
| Risk | Mitigation Strategy | Contingency (Risk is realized) |
|---|---|---|
| External dependencies change or become unavailable. | Keep CI checks focused on controllable project-owned tests. | Mark affected scenarios blocked and restore once the dependency is available again. |
| BDD scenarios become stale versus implementation. | Review feature files together with code changes. | Update the scenarios and rerun the PR checks. |
| GitHub Actions fails due to environment drift. | Keep workflow steps explicit and reproducible. | Fix the workflow or runner configuration before merge. |
| SonarQube Cloud quality gate blocks the PR. | Address code smells and coverage gaps early. | Refactor or defer the change with documented approval. |
| Test data is insufficient or inconsistent. | Use fixtures and controlled test data. | Recreate the data set and rerun the tests. |
## 13. Management Process and Procedures
The test process follows the same PR-based workflow as development.
Changes are reviewed through pull requests, automated tests run in GitHub Actions, and merge is blocked until the required checks pass.
If a test failure is found, the issue is logged, the relevant scenario or code is updated, and the pipeline is rerun before approval.
