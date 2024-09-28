## Notification Quantum

![Image](/assets/C2_survey_quanta.jpg)

### Responsibilities

1. Creates and maintains survey for Candidates and Hiring Managers once the interview is done.
2. Triggers notification to the users once a survey is created (if configured).
3. Exposes survey related API endpoints.
4. Captures and stores survey response when a user completes a survey.
5. Publishes survey complete event to messaging queue/bus.
6. Allows platform admin to configure/update the survey format/template.

### Driving Architectural Characteristics

![Image](/assets/survey-arch-char-worksheet.jpg)

#### Top 3

##### Driving Architectural Characteristics

1. **Scalability** - The quantum should be scalable. It should be able to handle the large number of users in future.
2. **Configurability** - Should be able to change or update the survey format/template.
3. **Availability** - Should be available to serve the API endpoints.

### Architectural Style Preferred

Hybrid - Microservices + Event Driven

![Image](/assets/survey-arch-style-worksheet.jpg)
