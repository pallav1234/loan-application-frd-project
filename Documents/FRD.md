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

## 7. Glossary
- **KYC:** Know Your Customer  
- **TAT:** Turnaround Time  

---
