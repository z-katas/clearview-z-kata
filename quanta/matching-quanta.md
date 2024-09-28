## Matching / Computation Quantum

![Image](/assets/C2_matching_quanta.jpg)

### Responsibilities

1. Using an elaborate matching algorithm identifies relevant pairs of anonymized resumes and open job postings, and computes a matching score to quantifiably assess their compatibility.
2. Creates and maintains 'Match' entities, that represent highly compatible pair of anon resume story and open job postings.
3. Exposes Match related API endpoints.
4. Handles the business logic related to 'Unlock' Match flow.
5. Triggers Invoice creation and Forward full resume to external HR integration during the unlock flow.
6. Updates Hired/Passed status and publishes relevant events for a Unlocked Match once the interview completion is reported either through API or external HR event.

### Driving Architectural Characteristics

![Image](/assets/matching-arch-char-worksheet.jpg)

#### Top 3

##### Driving Architectural Characteristics

1. **Performance** - This quantum is responsible for the most computationally intensive tasks in the platform. Thus performance becomes an important characteristic to consider here.
2. **Scalability** - The quantum should be scalable. It should be able to handle the large number of resumes and jobs in future.
3. **Evolvability** - The matching algorithm would require incremental changes and fine tuning to meet the desired accuracy for all types of resumes and job postings.

### Architectural Style Preferred

Hybrid - Event Driven + Microservices

![Image](/assets/matching-arch-style-worksheet.jpg)
