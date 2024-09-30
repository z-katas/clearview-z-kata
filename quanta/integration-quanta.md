## Integration Quantum

![Image](/assets/C2_integration_quanta.jpg)

### Requirements

Some of the requirements for the Integration:

- External HR Systems should be able to provide their API details (endpoints, credentials, etc.) to the ClearView platform.
- Should be able to introduce new HR integrations without affecting the existing ones.
- The platform should be able to reliably transfer the data from the HR System's API to the ClearView platform.

### Components and Responsibilities

- **Integration Service**:

  - Manages configurations for external HR systems to integrate with the platform.
  - Ease of usability for Platform admin to manage External HR Systems.
  - Ease of usability for Employer admins to manage their HR System.

- **Workflow Service**:
  - Syncs the data between external HR systems and clearview platform periodically

### Driving Architectural Characteristics

![Image](/assets/integrations-arch-char-worksheet.png)

#### Top 3

- **Configurability**: Integration of the platform with a new HR System should not warrant a redeployment of the entire quantum.
- **Feasibility**: The architecture should support quick integration with a new HR System.
- **Workflow**: Workflow is core to the integration quantum to enable reliable ingestion into Clearview platform.

#### Other Driving Characteristics

- **Scalability**: Should support the increase in no. of external HR System wanting to integrate with the platform.
- **Testability**: Since this system needs to be highly configurable, a supporting framework should be bug-free.

### Architectural Style Preferred

![Image](/assets/integrations-arch-style-worksheet.png)

- _Event-driven_ for enabling workflow in data ingestion into the clearview platform and pushing data to user profile APIs
- _Micro kernel_ for introducing new HR system integrations without affecting the existing ones.

### Tradeoffs - Mitigation Strategies

- Please refer to the [ADR](/ADR/005.adr-integrations-architecture-style.md)
