# Business Requirements Document (BRD)  
**Project:** Online Loan Application System  
**Version:** 1.0  
**Date:** YYYY-MM-DD  
**Author:** Pallav Daru  

---

## 1. Document Control  

| Version | Date       | Author       | Description              | Approved By |
|---------|------------|--------------|--------------------------|-------------|
| 1.0     | YYYY-MM-DD | Pallav Daru  | Initial Draft            | TBD         |
| 1.1     | TBD        | Pallav Daru  | Updated with RTM mapping | TBD         |

**Distribution List:** Project Sponsor, Business Team, IT Team, QA Team, Compliance  

---

## 2. Executive Summary  
The purpose of this BRD is to define the business needs and objectives for implementing an **Online Loan Application System**.  
- **Background:** Customers face delays due to manual, branch-based loan applications.  
- **Business Problem:** Current process lacks transparency, is paper-heavy, and increases turnaround time (TAT).  
- **Proposed Solution:** A digital platform enabling customers to apply, upload documents, and track loan status online, while enabling loan officers to review applications efficiently.  

---

## 3. Current State (As-Is)  

- Customers must physically visit branches.  
- Manual KYC/document verification leads to delays (avg TAT = 10–15 days).  
- No real-time tracking of application status.  
- High risk of errors, fraud, and duplicate submissions.  

---

## 4. Future State (To-Be)  

- Fully online application submission & document upload.  
- Automated validation against government APIs (PAN, Aadhaar).  
- Real-time dashboards for customers and loan officers.  
- Faster approvals with integrated risk scoring.  
- Compliance-ready audit trail.  

---

## 5. Business Objectives & Goals  

| Objective | KPI / Metric | Target |
|-----------|--------------|--------|
| Reduce loan processing time | Avg TAT (days) | Reduce from 10–15 days → < 5 days |
| Improve customer satisfaction | Survey-based CSAT | +30% increase |
| Digitize process | Paper-based applications | -90% within 6 months |
| Ensure compliance | Regulatory breaches | Zero tolerance |

---

## 6. Project Scope  

**In Scope:**  
- Online loan application submission  
- Document upload & validation (PAN, Aadhaar, Income Proof)  
- Loan eligibility calculator  
- Customer status tracking (Submitted, In Review, Approved, Rejected)  
- Admin dashboards & reporting  

**Out of Scope:**  
- Loan disbursement process  
- Third-party credit score integration (beyond PAN/Aadhaar)  
- Mobile app (Phase 2)  

**Dependencies:**  
- Government APIs (Aadhaar, PAN)  
- Secure payment gateway (if future installments)  

---

## 7. Stakeholders & Roles  

| Stakeholder       | Role / Responsibility |
|-------------------|------------------------|
| Customers         | Apply for loans, upload documents, track status |
| Loan Officers     | Review applications, approve/reject, assign risk scores |
| Admin Team        | Generate reports, monitor performance |
| Compliance Team   | Ensure RBI & regulatory adherence |
| IT / Dev Team     | Develop and maintain system |
| QA Team           | Validate against requirements (linked to SRS & FRD) |

---

## 8. High-Level Business Requirements  

| ID   | Requirement | Source | Mapped To |
|------|-------------|--------|-----------|
| BR-1 | Customers must create an account & log in securely | Business | FR-1, SRS §4.1 |
| BR-2 | Customers can submit loan applications online | Business | FR-3, SRS §4.2 |
| BR-3 | System validates customer details via APIs | Business | FR-4, SRS §4.3 |
| BR-4 | Customers can upload required documents | Business | FR-5, Screen Specs §1.4 |
| BR-5 | Customers can track application status online | Business | FR-10, Screen Specs §1.5 |
| BR-6 | Loan officers can review applications & make decisions | Business | FR-9, Screen Specs §2.2 |
| BR-7 | Admin can generate reports | Business | FR-12, Screen Specs §2.3 |

---

## 9. Functional Requirements (Business View)  

High-level functional requirements (detailed breakdown is in FRD):  
- Registration & Login (Customer/Admin)  
- Loan Application (personal, employment, loan details)  
- Document Upload & OCR validation  
- Application Review (Loan Officer)  
- Status Dashboard (Customer view)  
- Reporting (Admin view)  

---

## 10. Non-Functional Requirements  

| Category     | Requirement |
|--------------|-------------|
| Performance  | System should support 500 concurrent users |
| Usability    | Mobile-responsive web design |
| Security     | Role-based access, 2FA for login |
| Compliance   | RBI, GDPR, PCI DSS |
| Availability | 99.5% uptime |
| Scalability  | Support 5x load in next 2 years |

---

## 11. Assumptions  

- Customers have Aadhaar and PAN ready.  
- Loan officers are trained on digital workflow.  
- Internet access is available to customers.  

---

## 12. Constraints  

- API response time ≤ 10 seconds.  
- Budget and timeline fixed by management.  
- Limited integration in Phase 1 (PAN & Aadhaar only).  

---

## 13. Risk Analysis & Mitigation  

| Risk | Impact | Likelihood | Mitigation |
|------|--------|------------|------------|
| API downtime (PAN/Aadhaar) | High | Medium | Cache requests, retry logic |
| Data breach | Critical | Low | Encryption, penetration testing |
| User resistance | Medium | Medium | Training, communication plan |
| Regulatory changes | High | Low | Compliance monitoring |

---

## 14. Success Metrics / KPIs  

- 90% paperless applications within 6 months.  
- TAT reduced by 60%.  
- 95% positive customer satisfaction.  
- Zero regulatory non-compliance incidents.  

---

## 15. Reporting & Analytics Needs  

- Loan application volume (daily/weekly/monthly).  
- Approval vs. rejection rates.  
- Officer productivity metrics.  
- Risk scoring patterns.  

---

## 16. Glossary  

- **TAT** – Turnaround Time  
- **CSAT** – Customer Satisfaction Score  
- **OCR** – Optical Character Recognition  
- **FRD** – Functional Requirements Document  
- **SRS** – Software Requirements Specification  

---

## 17. Appendices  

- **Linked Documents:**  
  - [FRD.md](./FRD.md)  
  - [SRS.md](./SRS.md)  
  - [Screen_Specifications.md](./Screen_Specifications.md)  
  - [UserStories.md](./UserStories.md)  
  - [System_Diagrams.md](./System_Diagrams.md)  

- **References:**  
  - RBI Loan Guidelines  
  - UIDAI Aadhaar API Docs  

---
