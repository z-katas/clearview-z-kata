## Business Requirement Analysis

ClearView aligns with the Diversity Cyber Council’s mission by facilitating inclusive hiring processes through the reduction of bias. It provides both anonymized candidate information and consultancy services to improve fairness in interviews, thereby contributing to a more diverse and equitable talent pipeline in tech.

### Initial Thoughts

- **Anonymization**: The platform should anonymize personal data while preserving skills and qualifications to ensure fair candidate evaluations.
- **Bias Reduction Metrics**: Developing metrics to measure and reduce bias in interviews will be crucial to the platform's success.
- **ATS Improvement**: ClearView must offer a more effective alternative to traditional ATS by better matching candidates to job descriptions based on objective criteria.
-  **Consultant Services**: The platform will allow DEI consultants to monitor interviews, assess interviewer behavior, and generate reports for executive review.

#### Requirement Analysis

1. *The platform must leverage AI to re-construct job seeker resumes into a S.M.A.R.T goal format and quantifiably align their experience to open roles posted by hiring managers.*
   * Initial Thoughts: 
      * Employers’ hiring managers (HM) should be able to filter candidates by criteria like experience and skills. Without filtering, it will be challenging to create S.M.A.R.T goals for every resume.
      * The HM should be able to get a candidate's story in S.M.A.R.T goal format along with their experience and qualifications.
   * NFRs:
     * **Evolvability**
     * **Inspectability**
     * **Performance**

2. *Similarity Score/Match with job descriptions is a hard requirement.*
   * Initial Thoughts: 
      * HMs should see a candidate's similarity score as a percentage match. A higher percentage indicates a stronger match.
   * NFRs:
     * **Scalability**
     * **Data Integrity**
     * **Predictability**

3. *AI provided resume tips is a hard requirement.*
   * Initial Thoughts: 
      * AI should assist with grammar corrections and suggest missing information like contact details or GitHub links.
      * AI should help structure the resume in a concise manner, aiming to shorten long resumes to one page.
   * NFRs:
     * **Performance**
     * **Security**

4. *AI eliminating any potential racial, lifestyle, cultural, etc. indicators is a hard requirement.*
   * Initial Thoughts: 
      * The platform should have predefined identifiers for personally identifiable information (PII) like name, email, ethnicity, etc.
      * There should be a copy of anonymized resumes along with the original, with proper access controls.
   * NFRs:
     * **Availability**
     * **Recoverability**
     * **Confidentiality**
     * **Data Integrity**
     * **Security**

5. *Back-end process data aggregation is a hard requirement.*
   * Initial Thoughts:
      * The platform admin should be able to track metrics like the number of users, employers, and job postings.
      * Admins should also track third-party HR integrations, revenue, and hiring statistics.
   * NFRs:
     * **Observability**
     * **Data Integrity**
     * **Configurability**
     * **Auditability**

6. *Candidates should be able to track their own progress.*
   * Initial Thoughts:
      * Candidates should be able to view unlocked resumes, hired/rejected statuses, and match recommendations.
   * NFRs:
     * **Availability**
     * **Performance**

7. *Candidates should be able to view job offerings.*
   * Initial Thoughts: 
      * Candidates should have the ability to search for specific roles and filter results.
   * NFRs:
     * **Performance**
     * **Scalability**

8. *Candidates should be able to register into the platform.*
   * Initial Thoughts:
      * The candidate should add contact details, employment information, and set a password. Social login integrations (e.g., LinkedIn) could be offered for easier registration.
   * NFRs:
     * **Usability**
     * **Extensibility**
     * **Security**

9. *Candidates should be able to upload/update their resumes.*
   * Initial Thoughts:
      * Candidates should be able to manage their resumes, ensuring that only one is active at a time. Supported file formats include PDF, DOCX, and TXT.
   * NFRs:
     * **Durability**
     * **Availability**
     * **Recoverability**
     * **Security**

10. *Surveys should be conducted for candidates and employers.*
    * Initial Thoughts:
       * Platform admins should see survey results after an interview, gathering feedback from both parties via a five-question survey.
    * NFRs:
      * **Configurability**
      * **Security (Privacy)**

11. *Ease of use should be high.*
    * Initial Thoughts:
       * Accessibility and navigation should be simple for both candidates and employers.
    * NFRs:
      * **Usability**

12. *Employers should be able to register into the platform.*
    * Initial Thoughts:
       * Employers should provide company domain, website, and contact details. 
       * Able to log in via external identity providers (IDP) like LDAP or Google Workspace as long term approach.
    * NFRs:
      * **Usability**
      * **Extensibility**
      * **Security**

13. *Admin should validate the authenticity of the employer.*
    * Initial Thoughts:
       * Admin verification should be required before the employer is visible to candidates.
    * NFRs:
      * **Security**

14. *Employers’ HM should be able to post job offerings.*
    * Initial Thoughts:
       * HMs should specify required skills, salary expectations, and job descriptions, possibly with AI assistance.
    * NFRs:
      * **Data Integrity**
      * **Durability**

15. *Employer admins should be able to onboard hiring managers.*
    * Initial Thoughts:
       * HMs should receive a sign-up link and onboarding instructions.
    * NFRs:
      * **Security**

16. *Employer admins should be able to add external HR systems to the platform.*
    * Initial Thoughts:
       * Employer admins should view and configure external HR system integrations, including testing the connection and sending resumes to external systems.
    * NFRs:
      * **Interoperability**
      * **Configurability**
      * **Security**
      * **Extensibility**

17. *Employer HMs should be able to unlock a matched resume.*
    * Initial Thoughts:
       * HMs should have limits on daily unlocks and see the associated costs. They should also be able to forward resumes to external HR systems.
    * NFRs:
      * **Security**
      * **Data Integrity**
      * **Availability**
      * **Reliability**

18. *Employer admins should receive invoices for unlocks and process payments.*
    * Initial Thoughts:
       * Payment details should be securely handled, with integration to a payment service provider (PSP) for invoicing and payments.
    * NFRs:
      * **Data Integrity**
      * **Auditability**
      * **Reliability**
      * **Security**

19. *Employer HMs should see a dashboard with engagement stats.*
    * Initial Thoughts:
       * HMs should view metrics like unlocks, hires, and job posting performance, with detailed engagement statistics.
    * NFRs:
      * **Performance**
      * **Accuracy**

20. *Platform admins should be able to mark a candidate as hired.*
    * Initial Thoughts: TBD
    * NFRs: TBD

21. *Sensitive data stored in the system includes candidate career profiles and PII.*
    * Initial Thoughts:
       * As per GDPR, PII must be erasable upon request, with defined retention periods for active and inactive candidates.
    * NFRs:
      * **Security**

22. *No. of users and regions* 
    * Initial Thoughts:
       * The platform should support exponential growth in both users and employers. Multi-region support should be considered to ensure availability.
    * NFRs:
      * **Security**
      * **Availability**
      * **Scalability**


### Requirement Analysis Table

| Given Requirements | Analysis | NFRs |
| ------------------ | -------- | ---- |
| The platform must leverage AI to re-construct job seeker resumes into a S.M.A.R.T goal format and quantifiably align their experience to open roles posted by the hiring manager. | AI will generate resumes in a structured format that matches employer requirements. HMs should have access to filters like experience and skills to streamline the process. | Evolvability, Inspectability, Performance |
| Similarity Score/Match with job descriptions is a hard requirement | The platform must generate a similarity score between resumes and job descriptions, presented as a percentage. The higher the percentage, the stronger the match. | Scalability, Data Integrity, Predictability |
| AI provided resume tips is a hard requirement | AI must assist in improving grammar, suggesting missing information (e.g., contact details, GitHub links), and shortening lengthy resumes to fit the ideal format. | Performance, Security |
| AI eliminating any potential racial, lifestyle, cultural, etc. indicators is a hard requirement | The platform must anonymize PII (e.g., name, contact info, ethnicity) in resumes and maintain both anonymized and original versions with proper access controls. | Availability, Recoverability, Confidentiality, Data Integrity, Security |
| Back-end process data aggregation is a hard requirement | Admins should be able to track user activity, such as unlocks, hires, and integrations with external HR systems, and view financial metrics like invoicing and revenue generation. | Observability, Data Integrity, Configurability, Auditability |
| Candidate should be able to track their own progress | Candidates should be able to view their matches, rejections, unlocks, and set their availability status. | Availability, Performance |
| Candidate should be able to view offerings/openings | Candidates need search and filtering options to explore job openings, with the ability to mark themselves as uninterested for specific roles. | Performance, Scalability |
| Candidate should be able to register into the platform | Candidates must add their contact details, employment history, and set a password. Social logins (e.g., LinkedIn) should also be supported. | Usability, Extendability, Security |
| Candidate should be able to upload/update the resume in the platform | Candidates should be able to upload, update, remove, view, and submit their resumes, with constraints like file size (10MB) and supported formats (PDF, DOC, etc.). Long-term multi-language support may be considered. | Durability, Availability, Recoverability, Security |
| Survey should be conducted for candidates/employers | Surveys should be initiated post-hire or rejection, providing feedback on the hiring process for both employers and candidates. | Configurability, Security (privacy) |
| [Derived] Ease of use should be high | The platform must be highly accessible and easy to navigate for users. | Usability |
| Employer admin should be able to register into the platform | Employer admins should provide their company’s email domain, website, contact info, and logo, with external identity provider (IDP) integration. | Usability, Extendability, Security |
| Admin should validate the authenticity of the employer | Admins must verify employer authenticity based on the provided information, and the employer should remain under review until validated. | Security |
| Employer's hiring manager (HM) should be able to post job offerings | Employers must specify required tech stacks, expected salary, and job description, with optional AI assistance. | Data Integrity, Durability |
| Employer admin should be able to onboard hiring managers | Employer admins should send signup and verification links to HMs, enabling them to complete their profiles. | Security |
| Employer admin should be able to add external HR systems into the platform | Employer admins should be able to configure and test integrations with external HR systems, ensuring smooth data exchange and error handling. | Interoperability, Configurability, Security, Extensibility |
| Employer's HM should be able to unlock a matched resume | Employer admins should define daily resume unlock limits, with cost prompts for unlocking. Resumes should be forwardable to external HR systems after unlocking. | Security, Data Integrity, Availability, Reliability |
| Employer admin should get the invoice for unlocks and make the payment | Employer admins should provide payment details, and the platform must securely interface with payment service providers (PSPs) for invoicing and payments. | Data Integrity, Auditability, Reliability, Security |
| Employer's HM should be able to see the dashboard which contains stats on engagement, matches, etc. | Employers should have access to engagement metrics, such as unlocks, matches, hires, and job posting duration. | Performance, Accuracy |
| Platform admin can mark candidates as hired | Platform admins should be able to update the status of a candidate’s hiring. | Data Integrity, Reliability |
| [Derived] Sensitive data stored in the system includes - Candidate career profiles, PII (email, phone, address, ethnicity, SSN, etc.). | As per GDPR, the system should erase PII upon user request, with a 5-year retention period for active candidates and 30 days for inactive ones. | Security |
| [Derived] No. of users | The platform must scale to support significant growth in candidates and employers as the service gains traction. | Scalability |
| [Derived] Multi-region support | The platform should support multi-region deployments for improved availability and performance across geographical locations. | Availability |

---

### Further Analysis and Considerations

This project is to enhance diversity, equity, and inclusion (DEI) in the hiring process by creating a supplemental HR platform that anonymizes candidate information and highlights objective skills and qualifications. This will help reduce bias in hiring decisions. Additionally, ClearView aims to provide DEI consultants with tools to monitor and report on interviews, offering feedback to executive management to further reduce bias in hiring.

This will be achieved by leveraging AI to assist in writing anonymized resumes that focus on skills and qualifications, ensuring candidates are matched more accurately with job opportunities based solely on merit.

### Security Considerations

As the platform will handle sensitive personal data (e.g., PII such as email, phone numbers, employment history, and potentially racial or ethnic identifiers), robust security measures must be implemented from the beginning. Compliance with data protection regulations like GDPR is paramount. Below are key security aspects:

- **Data Encryption**: Apply end-to-end encryption for both data in transit and at rest.
- **Regulatory Compliance**: Ensure compliance with data privacy regulations such as GDPR and CCPA.
- **Access Control**: Implement role-based access control to limit data visibility and manipulation to authorized personnel.
- **Audit Trail**: Maintain a detailed audit trail to track access to candidate data and consultant reports for accountability and transparency.

---
