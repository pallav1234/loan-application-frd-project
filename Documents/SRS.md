# Software Requirements Specification (SRS)

**Project:** Online Loan Application System  
**Version:** 1.0  
**Date:** YYYY-MM-DD  
**Author:** Pallav Daru  

---

## 1. Introduction  
- **Purpose:** This document describes the software requirements for the Online Loan Application System, translating functional needs into technical specifications.  
- **Scope:** The system will allow customers to apply for loans online, track their application status, and upload necessary documents.  
- **Intended Audience:** Business Analysts, Developers, Testers, and Project Stakeholders.  

---

## 2. Overall Description  
- **System Perspective:** The system will be web-based and accessible via browser and mobile devices.  
- **System Features (high-level):**  
  - Customer Registration & Login  
  - Loan Application Submission  
  - Document Upload & Verification  
  - Application Tracking  
  - Admin Review & Approval/Rejection  

- **Assumptions and Dependencies:**  
  - Internet connectivity required.  
  - Customer identity verified via government ID.  
  - Integration with external credit score APIs.  

---

## 3. Functional Requirements  
- **FR1:** The system shall allow users to register with basic details (name, email, phone, password).  
- **FR2:** The system shall enable users to log in securely using credentials.  
- **FR3:** The system shall allow users to submit a loan application form.  
- **FR4:** The system shall enable document uploads in PDF/JPEG format.  
- **FR5:** The system shall display real-time status of loan applications.  
- **FR6:** The admin shall be able to review and approve/reject applications.  

---

## 4. Non-Functional Requirements  
- **Performance:** The system should handle 500 concurrent users.  
- **Security:** Data encryption (AES-256) for sensitive information.  
- **Availability:** 99.5% uptime.  
- **Usability:** Mobile responsive interface.  

---

## 5. User Interface Requirements  
- Loan application form (web/mobile) must be user-friendly.  
- Status dashboard should display application progress.  

---

## 6. Data Requirements  
- The system shall store customer and loan data in a relational database.  
- Data retention policy: 7 years.  

---

## 7. Appendices  
- **Glossary:**  
  - *Applicant* – End-user applying for loan.  
  - *Admin* – Bank officer reviewing applications.  
- **References:** BRD, FRD.  

---
