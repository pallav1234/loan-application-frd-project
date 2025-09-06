Software Requirements Specification (SRS)

Project: Online Loan Application System
Version: 1.0
Date: YYYY-MM-DD
Author: Pallav Daru

1. Introduction
Section	Description
Purpose	Defines the requirements for the Online Loan Application System. Converts business needs into technical specifications.
Scope	Customers apply for loans online, upload documents, and track status. Admins review, approve, or reject applications.
Audience	Business Analysts, Developers, QA Testers, Architects, and Stakeholders.

2. Overall Description
 | Aspect                           | Details                                                                                                          |
| -------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| **System Perspective**           | Web & mobile responsive system, integrated with external credit score APIs.                                      |
| **System Features (High-Level)** | Registration/Login, Loan Application Submission, Document Upload, Application Tracking, Admin Review & Decision. |
| **Assumptions**                  | Internet required, Govt. ID for KYC, external APIs available.                                                    |
| **Dependencies**                 | Browser compatibility, API integrations, database availability.                                                  |

3. Functional Requirements
   | ID  | Requirement                                                                 | Priority |
| --- | --------------------------------------------------------------------------- | -------- |
| FR1 | System shall allow users to register with Name, Email, Phone, and Password. | High     |
| FR2 | System shall allow users to log in securely with credentials.               | High     |
| FR3 | System shall allow users to submit a loan application form.                 | High     |
| FR4 | System shall allow users to upload documents (PDF/JPEG).                    | High     |
| FR5 | System shall display real-time loan application status.                     | Medium   |
| FR6 | System shall allow admins to review and approve/reject applications.        | High     |

4. Non-Functional Requirements
| Category         | Requirement                                             |
| ---------------- | ------------------------------------------------------- |
| **Performance**  | Support 500+ concurrent users.                          |
| **Security**     | Encrypt sensitive data (AES-256), enable 2FA for login. |
| **Availability** | 99.5% uptime SLA.                                       |
| **Usability**    | Mobile responsive, intuitive navigation.                |
| **Scalability**  | Expandable to 5,000+ users without major rework.        |

5. User Interface Requirements
   | Interface     | Description                                                    |
| ------------- | -------------------------------------------------------------- |
| Loan Form     | User-friendly form with validation and progress indicator.     |
| Dashboard     | Displays loan application status, notifications, and timeline. |
| Admin Console | Enables loan review, approval/rejection, and comments.         |

  6. Data Requirements
     | Data Type        | Storage                          | Retention |
| ---------------- | -------------------------------- | --------- |
| Customer Data    | Relational DB (PostgreSQL/MySQL) | 7 years   |
| Loan Application | Relational DB                    | 7 years   |
| Audit Logs       | Database + Cloud Backup          | 10 years  |

7. Appendices
   | Term          | Definition                                    |
| ------------- | --------------------------------------------- |
| **Applicant** | End-user applying for a loan.                 |
| **Admin**     | Bank officer reviewing applications.          |
| **KYC**       | Know Your Customer verification via Govt. ID. |

   
