# Aggregation Metrics

Date: 2024.09.28

## Status

Accepted

## Context

ClearView Platform needs to aggregate data points, compute metrics and generate reports at periodic intervals. These metrics and reports help in monitoring the system and evaluating how close to the actual requirements is the system performing. We need to identify a reliable approach to gather and aggregate data without impacting core the business functionality. We need to choose few metrics that can qualitatively measure if the 'Transparent Decision Making' process enabled by the platform is without any bias.

### Alternatives

#### Analytics aggregation approach

1. **Batch Processing**:
   - _Pros_: Reduced immediate load on the system, suitable for processing large volumes of data at regular intervals.
   - _Cons_: Metrics and reports are only as current as the last batch, possible delays in identifying issues.

2. **Real-Time Processing**:
   - _Pros_: Immediate availability of metrics and reports, allowing for quick identification and response to issues.
   - _Cons_: Increased load on the system, potential for impacting core business functionality.

3. **Hybrid Approach**:
   - _Pros_: Balances the load on the system with the need for timely data, critical metrics can be updated in real-time while others can be batched.
   - _Cons_: Increased complexity in implementation and maintenance.

#### Metrics Selection

For effective monitoring and evaluation, the platform could track the following key metrics:

1. **Bias Reduction Metrics**:
   - **Resume Selection Disparity Index (RSDI)**: Measures the disparity in resume selection rates before and after anonymization.
   - **Applicant Diversity Ratio (ADR)**: Evaluates the diversity of successful applicants compared to the initial applicant pool.

2. **System Performance Metrics**:
   - **Matching Accuracy (MA)**: Percentage of matches with high matching score that lead to successful hires.
   - **Mean Anonymized Resume Story (MARS) Generation Time**: Average time taken to process, anonymize resumes and generate story with SMART goals and other details.

3. **User Engagement Metrics**:
   - **User Retention Rate (URR)**: Percentage of users (both job seekers and employers) returning to use the platform.
   - **User Satisfaction Score (USS)**: Aggregate score from user feedback surveys.

### PrOACT

#### Analytics aggregation approach

- **Problem**: Determine how to efficiently gather and process data for generating necessary metrics and reports to ensure the 'Transparent Decision Making' process is unbiased.
- **Objectives**:
  - Ensure unbiased resume selection.
  - Provide timely and reliable metrics and reports.
  - Maintain overall system performance and user satisfaction.
- **Alternatives**:
  - Batch Processing
  - Real-Time Processing
  - Hybrid Approach
- **Consequences**:
  - Batch Processing may delay issue identification.
  - Real-Time Processing may impact system performance.
  - Hybrid Approach is more complex but balances load and timeliness.
- **Trade-offs**: Prioritize unbiased processing without compromising system performance and user experience.

## Decision

#### Analytics aggregation approach

- Choose Hybrid Approach.
  - Do real time metrics computation for few key events.
  - - Eg : Job Posting is removed after selecting required candidates. This should trigger computation of Bias Reduction Metrics for that Job Posting.
  - Do batched computation for periodic reports generation.
  - Use side cars with read only data access to achieve this without impacting the core functionality.

#### Metrics Selection

- System should compute the two identified Bias Reduction Metrics for each Job Posting. The computation should happen once the job posting is removed after selecting required candidates.
  -- Resume Selection Disparity Index (RSDI) could be computed by comparing ClearView data with benchmarks obtained from other solutions that do resume-job matching without any special attention for bias.
  -- Applicant Diversity Ratio (ADR) should be monitored and the instances where the values crosses a threshold should trigger an alert.
- System Performance Metrics and User Engagement Metrics could be computed on periodic intervals as part of a report.

## Tradeoffs - Mitigations

**Tradeoffs**:
- **Complexity**: The hybrid approach will introduce complexity in systems design and maintenance.
- **Resource Utilization**: Balancing real-time and batch processing will require careful allocation of computing resources.

**Mitigations**:
- **Scalability**: Utilize cloud-based scalable infrastructure to dynamically allocate resources based on workload demands.
- **Monitoring**: Implement robust monitoring tools to track the performance of both real-time and batch processes.
- **Regular Reviews**: Periodically review and adjust the balance between real-time and batch processing based on the system's performance and user feedback.
