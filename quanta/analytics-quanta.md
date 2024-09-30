## Analytics Quantum

![Image](/assets/C2_analytics_quanta.jpg)

### Responsibilities

1. This quanta is responsible for aggregating required data, computing relevant metrics and generating reports.
2. The report generation and metrics computation should happen at both periodic intervals and event based triggers.
3. Creates and maintains 'Report' and 'Metric' entities.
4. This quanta should not impact the core functionality of the platform. This is achieved by using analytics side cars that are deployed along with services. These side cars have read-only access to the data. They retrieve the relevant data and forward it to a data warehouse which is then accessed by the analytics data aggregation components.
5. Trigger notification alerts when a metric is found to be beyond a threshold. (if configured)

### Driving Architectural Characteristics

![Image](/assets/analytics-arch-char-worksheet.jpg)

#### Top 3

##### Driving Architectural Characteristics

1. **Elasticity** - During report generation that is done at periodic intervals large amounts of data should be processed in a short interval of time.
2. **Availability** - Should be available to trigger the alerts, periodic report generations and to serve the API endpoints.
3. **Performance** - Metrics computation and report generation are computationally intensive tasks thus performance becomes an important characteristic for this quanta.

### Architectural Style Preferred

![Image](/assets/analytics-arch-style-worksheet.jpg)

Hybrid - Event Driven + Microservices
