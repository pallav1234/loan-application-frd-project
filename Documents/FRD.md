# Functional Requirements Document (FRD)

**Project:** Online Loan Application System  
**Version:** 1.0  
**Date:** YYYY-MM-DD  
**Author:** Pallav Daru  

---

## 1. Introduction
- **Purpose:** Translate business needs (from BRD) into detailed functional requirements.  
- **Scope:** This FRD defines system behavior, workflows, and rules for the Online Loan Application System.  
- **References:** BRD v1.0, Stakeholder interviews, Regulatory compliance documents.  

---

## 2. System Overview
The Online Loan Application System will allow customers to apply for loans online, upload required documents, track application status, and receive approvals digitally.  

---

## 3. Functional Requirements
### 3.1 User Roles
- **Customer:** Apply for loans, upload documents, track status.  
- **Loan Officer:** Review applications, verify documents, approve/reject.  
- **Admin:** Manage users, configure loan policies, generate reports.  

### 3.2 Core Functionalities
1. **User Registration & Login**  
   - Customers must register using email/mobile.  
   - Two-factor authentication for login.  

2. **Loan Application Form**  
   - Capture personal details, income, employment, loan amount.  
   - Real-time validation of mandatory fields.  

3. **Document Upload**  
   - Accept PDF/JPEG/PNG.  
   - OCR-enabled document verification (future scope).  

4. **Loan Processing Workflow**  
   - Automatic risk scoring based on inputs.  
   - Loan officer reviews & updates status.  
   - Notifications sent at each stage.  

5. **Dashboard & Reports**  
   - Customer: Track loan status.  
   - Admin: Generate approval/rejection/turnaround time reports.  

---

## 4. Non-Functional Requirements
- **Performance:** System should handle 500 concurrent users.  
- **Security:** Data encryption (AES-256), HTTPS, role-based access.  
- **Availability:** 99.9% uptime.  
- **Scalability:** Support future expansion to 5x users.  

---

## 5. Assumptions & Constraints
- Users must have internet access.  
- Loan processing depends on external credit bureau APIs.  

---

## 6. Use Case Diagram (Placeholder)
*(To be added in Diagrams/ folder as image — later we’ll link here)*  

---
---

## 7. User Story to Functional Requirement Mapping  

| User Story ID | User Story                                                                 | Mapped FRD Requirement(s) |
|---------------|-----------------------------------------------------------------------------|----------------------------|
| US-01         | As a customer, I want to register with my details so that I can apply...   | FR1                        |
| US-02         | As a customer, I want to log in securely so that my data is protected.     | FR2                        |
| US-03         | As a customer, I want to submit a loan application so that I can...        | FR3                        |
| US-04         | As a customer, I want to upload required documents so that my loan...      | FR4                        |
| US-05         | As a customer, I want to track my loan status so that I know progress.     | FR5                        |
| US-06         | As a customer, I want to receive notifications so that I stay updated.     | FR5 (extension)            |
| US-07         | As an admin, I want to log in securely so that only staff access system.   | FR2 (admin role)           |
| US-08         | As an admin, I want to review loan applications so that I can approve...   | FR6                        |
| US-09         | As an admin, I want to verify uploaded documents so that fraud is reduced. | FR4 (validation)           |
| US-10         | As an admin, I want to update application status so that customers know.   | FR5, FR6                   |
| US-11         | As an admin, I want to generate reports so that management has insights.   | FR6 (extension/reporting)  |

---


## 8. Glossary
- **KYC:** Know Your Customer  
- **TAT:** Turnaround Time  

---
