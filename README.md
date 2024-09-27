# O'reilly Architectural Katas - Spring 2024 - ClearView Platform

## Update

Thank you judges for the valuable feedback and the entire O'reilly team for organizing the event. It was a great learning experience just to be part of the event and looking at the perspectives of all the participating teams.

## Final Presentation

TBD

## Table of Contents

- [O'reilly Architectural Katas - Spring 2024 - ClearView Platform](#oreilly-architectural-katas---spring-2024---clearview-platform)
  - [Update](#update)
  - [Final Presentation](#final-presentation)
  - [Table of Contents](#table-of-contents)
  - [About Team ArchZ](#about-team-archz)
  - [Glossary](#glossary)
  - [Prelude](#prelude)
    - [Goal of the platform](#goal-of-the-platform)
  - [Non-Functional Requirements](#non-functional-requirements)
  - [Overall Platform Context](#overall-platform-context)
  - [User experience](#user-experience)
    - [Candidate Golden Path](#candidate-golden-path)
    - [Employer Golden Path](#employer-golden-path)
    - [Platform Admin Golden Path](#platform-admin-golden-path)
    - [AI System Golden Path](#ai-system-golden-path)
  - [Assumptions](#assumptions)
    - [Capacity planning](#capacity-planning)
    - [Security / Availability](#security--availability)
  - [User Roles](#user-roles)
  - [Identifying Architectural Quanta](#identifying-architectural-quanta)
    - [Quanta](#quanta)
    - [Other Services](#other-services)
  - [Overall Architecture](#overall-architecture)
    - [Logical View](#logical-view)
    - [Physical View](#physical-view)
  - [Platform Roadmap](#platform-roadmap)
    - [MVP](#mvp)
    - [Long Term](#long-term)
  - [Engineering Practices](#engineering-practices)
  - [Resources](#resources)

<a name="about-the-team"></a>

## About Team ArchZ

We are a passionate group of software engineers & product managers from an innovation as a service organization [Zemoso](https://www.zemosolabs.com/).

<a name="glossary"></a>

## Glossary

- HR System
- NFR - Non-functional requirement
- MVP - Minimum Viable Product
- PII - Personal Identifiable Information
- UI - User Interface
- UX - User Experience
- HM - Hiring manager

<a name="prelude"></a>

## Prelude

ClearView is a supplemental HR platform that anonymizes candidate information while highlighting objective skills and qualifying experience to reduce bias in the hiring process. Clear View will also be service based, enabling DEI consultants to shadow employer interviews to rate the interviewer and report findings to executive management in an effort to proactively and strategically reduce bias in the interview process.

Diversity Cyber Council has come forward with a vision to enhance inclusion and representation in the tech industry through training, mentoring, networking, and visibility programs.

### Goal of the platform

To establish a sustainable and diverse talent pipeline that extends career equity to underrepresented demographics by providing access to competent training programs that lead to direct employment opportunities.

<a name="non-functional-requirements"></a>

## Non-Functional Requirements

After the **[detailed analysis of business requirements](/business-requirements/requirement-analysis.md)**, the team has come up with the below NFRs for the platform

- Security
- Availability
- Scalability
- Usability
- Data Integrity
- Extendability

Since the proposal is a platform, the platform could be composed of several architectural quanta, each with its own architectural style. So, we are not picking a style yet.

<a name="context-diagram"></a>

## Overall Platform Context

![Image](/assets/context.png)

[For better navigation on the content, use this miro frame](https://miro.com/app/board/uXjVOv-nlBo=/?moveToWidget=3458764528112682339&cot=14)

<a name="user-experience"></a>

## User experience

The team went through a design thinking exercise to understand the Candidate, Employer and platform admin  profiles, and empathize their needs and pain points. We also created AI system golden path The following golden paths were considered:

[Design artifacts](TBD)

<a name="candidate-flow"></a>

### Candidate Golden Path

![Image](/assets/candidate-golden-path.png)

<a name="employer-flow"></a>

### Employer Golden Path

![Image](/assets/employer-golden-path.png)

<a name="administrator-flow"></a>

### Platform Admin Golden Path

![Image](/assets/platform-admin-golden-path.png)

<a name="AI-system-flow"></a>

### AI System Golden Path

![Image](/assets/ai-system-golden-path.png)

https://www.loom.com/share/X

<a name="assumptions"></a>

## Assumptions

### Capacity planning

- TBD

### Security / Availability

- TBD

<a name="user-roles"></a>

## User Roles

- CANDIDATE
- EMPLOYER_ADMIN (associated with the respective Organisation)
- EMPLOYER_HM (associated with the respective Organisation)
- PLATFORM_ADMIN (associated with the ClearView Platform)

<a name="identifying-architectural-quanta"></a>

## Identifying Architectural Quanta

**Architecture quantum** - _An independently deployable artifact with high functional cohesion and synchronous connascence_

Quanta identification helps in defining different parts of the platform and the scope of architectural characteristics. We followed a mixture of event storming + actor-action approach to identify aggregates, components and quanta.

[Click here for more details on the exercise.](/assets/aggregate-quanta.png)

<a name="quanta"></a>

### Quanta

- [AI](/quanta/ai-quanta.md.md)
- [Invoice](./quanta/invoice-quanta.md.md)
- [Notification](./quanta/notification-quanta.md.md)
- [Integrations](./quanta/integration-quanta.md.md)
- [User](./quanta/user-quanta.md.md)
- TBD

<a name="other-services"></a>

### Other Services

- [Infrastructure Services](TBD)
- [Support](TBD)
- [BFF](TBD)

<a name="overall-architecture"></a>

## Overall Architecture

<a name="logical-view"></a>

### Logical View

![Image](/assets/logical-view.png)

<a name="component-view"></a>

### Physical View

![Image](TBD)

[For better navigation on the content, use this miro frame]

<a name="platform-roadmap"></a>

## Platform Roadmap

### MVP

The MVP is envisioned to bring out the unique value proposition of the platform and solve the key business problem / pain points. It should be sufficient for the business to get market feedback and pivot, if needed.

Areas to be addressed (In the order of priority):

- TBD

### Long Term

Areas to be addressed:

- TBD

<a name="engineering-practices"></a>

## Engineering Practices

- TBD

<a name="resources"></a>

## Resources

- TBD