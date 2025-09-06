# Requirements Traceability Matrix (RTM)

**Project:** Online Loan Application System  
**Version:** 1.0  
**Date:** YYYY-MM-DD  
**Author:** Pallav Daru  

---

## Purpose
The RTM ensures that every **business requirement (BRD)** is traced to its corresponding **functional requirements (FRD)**, **user stories**, **screen specifications**, and can later be linked to **test cases**. This guarantees full coverage and reduces the risk of missing requirements.

---

## RTM Table

| BRD ID | Business Requirement                                       | FRD ID(s)      | User Story ID(s) | Screen Reference             | Test Case ID (future QA) |
|--------|-------------------------------------------------------------|----------------|------------------|------------------------------|---------------------------|
| BR-01  | Allow customers to register and create an account           | FR-01, FR-02   | US-01, US-02     | Registration, Login          | TC-01, TC-02              |
| BR-02  | Customers should be able to submit loan applications        | FR-03, FR-04   | US-03            | Loan Application Form        | TC-03, TC-04              |
| BR-03  | Customers must upload supporting documents                  | FR-05, FR-06   | US-04            | Document Upload              | TC-05, TC-06              |
| BR-04  | Customers should track their application status             | FR-10          | US-05            | Status Dashboard             | TC-07                     |
| BR-05  | Loan officers should review and process applications        | FR-09, FR-11   | US-06            | Application Review (Admin)   | TC-08, TC-09              |
| BR-06  | Admin should manage reports and loan statistics             | FR-12          | US-07            | Reports Screen (Admin)       | TC-10                     |
| BR-07  | System must ensure security and data privacy                | FR-NF-01–NF-03 | N/A              | All screens (login/session)  | TC-11, TC-12              |
| BR-08  | System should integrate with external credit score API      | FR-08          | US-03 extension  | Loan Application Form        | TC-13                     |

---

## Notes
- **Screen Reference** column points to `Screen_Specifications.md` sections.  
- **Test Case ID** column is placeholder for QA team (future phase).  
- This RTM will evolve as requirements are refined and new test cases are added.  

---
Traceability_Matrix.mdTraceability_Matrix.md
