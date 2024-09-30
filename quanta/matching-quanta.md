## Matching / Computation Quantum

![Image](/assets/C2_matching_quanta.jpg)

### Responsibilities

1. Using a hybrid (LLM + traditional) matching algorithm identifies relevant pairs of anonymized resumes and open job postings, and computes a matching score to quantifiable assess their compatibility.
2. Creates and maintains 'Match' entities, that represent highly compatible pair of anon resume story and open job postings.
3. Batches the match operations to do the computation using the compute resources efficiently and optimally.
4. Exposes Match related API endpoints through 'Match service' component.
5. Handles the business logic related to 'Unlock' Match flow.
6. Triggers Invoice creation and Forward full resume to external HR integration during the unlock flow.
7. Updates Hired/Passed status and publishes relevant events for a Unlocked Match once the interview completion is reported either through API or external HR event.

### Driving Architectural Characteristics

![Image](/assets/matching-arch-char-worksheet.jpg)

#### Top 3

##### Driving Architectural Characteristics

1. **Performance** - This quantum is responsible for the most computationally intensive tasks in the platform. Thus performance becomes an important characteristic to consider here.
2. **Scalability** - The quantum should be scalable. It should be able to handle the large number of resumes and jobs in future.
3. **Evolvability** - The matching algorithm would require incremental changes and fine tuning to meet the desired accuracy for all types of resumes and job postings.

Elasticity and Cost are also important characteristics for this quanta

### Architectural Style Preferred

![Image](/assets/matching-arch-style-worksheet.jpg)

Hybrid - Event Driven + Microservices

During the MVP stage to save cost the components in this quanta could be built developed as modular monolith and then evolved over a period of time as the platform grows in size are revenue.

### Tradeoffs - Mitigation Strategies

- Please refer to the [ADR-3](/ADR/003.adr-matching-algorithm.md)
- Please refer to the [ADR-4](/ADR/004.adr-matching-quantum-arch-style.md)
