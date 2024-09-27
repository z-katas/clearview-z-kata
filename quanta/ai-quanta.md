## AI Quantum

![Image](/assets/C2_AI_quanta.jpg)

### Components and Responsibilities

- **Model Service**
    - Serve as a facade to interact with external LLM models, handling API calls and model interaction efficiently.
    - Manage request pre-processing and response post-processing, ensuring seamless integration of the external model with internal services.

- **Model Workflow**
    - Consume events from other services (like user actions or AI service requests) and trigger the creation of embeddings.
    -   Generate and store embeddings for various operations such as candidate matching, resume processing, and bias detection.

---

### Driving Architectural Characteristics

![Image](/assets/ai-arch-char-worksheet.png)

#### Top 3

- **Evolvability**: The AI Quantum must be capable of evolving to incorporate future AI models and adapt to new advancements in machine learning, ensuring continuous improvements without disrupting existing services.

- **Workflow**: A robust, configurable workflow is crucial to manage the ingestion of large datasets and training models efficiently. An error-free workflow ensures reliable model updates and embedding generation for various services.

- **Configurability**: The system should be configurable to allow new AI models or workflows to be added without redeployment, ensuring that AI Quantum can scale as more services integrate with the model and require personalized embeddings.

#### Other Driving Characteristics

- **Cost**: The AI Quantum must balance computational costs with scalability, especially when dealing with large LLMs and embeddings, ensuring cost-effective performance as model usage increases.

- **Privacy**: Given the sensitive nature of candidate data, the system must implement anonymization and secure storage of embeddings, adhering to strict privacy regulations while processing and generating insights.

- **Testability**: The system should be easily testable to verify the accuracy and effectiveness of the AI models and embeddings, ensuring model outputs are unbiased and reliable.

### Architectural Style Preferred

![Image](/assets/ai-arch-style-worksheet.png)

- Event-driven for enabling workflow.

### Tradeoffs - Mitigation Strategies

- TBD
