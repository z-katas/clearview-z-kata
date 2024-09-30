# Matching Algorithm

Date: 28.09.2024

## Status

Accepted

## Context

ClearView aims to provide a transparent and unbiased platform for job-resume matching. An essential part of this platform is the matching algorithm that ensures accurate, fair, and unbiased result. The algorithm must efficiently pair anonymized resume stories with relevant job postings.

### Alternatives

1. **Purely Traditional Matching Approach**: Using keyword-based matching and Boolean searches.
2. **Purely LLM-Based Matching Approach**: Using advanced LLMs to assess semantic similarity between resumes and job postings.
3. **Hybrid Matching Approach**: Combining traditional methods with LLM-based techniques to leverage the strengths of both.

### PrOACT

- **Problems**:
  - Eliminating bias while maintaining accurate matching.
  - Ensuring the scalability and performance of the matching algorithm.
  - Handling the diversity and variability in resume content and job descriptions.
- **Objectives**:
  - Accurate and unbiased matching of candidates to job postings.
  - Scalability to handle large numbers of resumes and job postings.
  - Flexibility to adapt to different industries and job roles.
- **Alternatives**:
  - Traditional Matching
  - LLM-Based Matching
  - Hybrid Matching
- **Consequences**:
  - Traditional Matching: Faster implementation but potential for less accurate matches.
  - LLM-Based Matching: More accurate but computationally intensive and may suffer from explainability issues.
  - Hybrid Matching: Balances accuracy and performance but increases system complexity.
- **Trade-offs**:
  - Complexity vs. Performance: A more complex system might offer better accuracy but at the cost of higher computational requirements.
  - Explainability vs. Accuracy: Traditional methods are easier to explain, whereas LLMs provide better accuracy but are often seen as a "black box."

## Decision

Given the complexity and diversity of resumes and job descriptions, ClearView will need a hybrid matching algorithm that leverages both traditional methods (e.g., keyword matching, Boolean search) and advanced LLM techniques (e.g., semantic similarity, embeddings).

We will implement a Hybrid Matching Approach that combines traditional keyword and Boolean searches with advanced LLM-based semantic similarity techniques to match anonymized resumes with job postings.

### Implementation Steps:

1. **Resume Anonymization and Story Generation**:
   - Use traditional methods to strip/mask identifying information.
   - Use LLMs to create anonymized resume stories.
2. **Initial Filtering Using Traditional Methods**:
   - Perform initial candidate-job matching using keyword-based and Boolean techniques to filter out obviously irrelevant resumes.
3. **Advanced Matching Using LLMs**:
   - Apply LLM-based embeddings and semantic similarity measures to further refine the matching process, ensuring high relevance and accuracy.
4. **Feedback Loop for Continuous Improvement**:
   - Implement a feedback mechanism where previous matching outcomes are analyzed to continuously improve the algorithm.

## Tradeoffs - Mitigations

1. **Computational Overhead**:
   - **Mitigation**: Use a tiered approach where computationally light traditional methods are applied first, followed by the more intensive LLM-based techniques on the filtered results.
2. **System Complexity**:
   - **Mitigation**: Modular design to separate traditional and LLM-based components for easier maintenance and updates.
3. **Explainability**:
   - **Mitigation**: Provide a transparent mechanism to explain initial traditional matching and use human-readable insights alongside LLM outputs to make results more interpretable.
4. **Bias in LLMs**:
   - **Mitigation**: Regularly audit and fine-tune LLMs to ensure they align with unbiased matching principles.
