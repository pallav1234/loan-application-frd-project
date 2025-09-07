# Use Case Diagram – Online Loan Application System

## Overview
This diagram represents the key actors and their interactions with the Online Loan Application System.  
The **system boundary** groups all capabilities offered by the system, while actors outside the box represent external users.  
Dashed arrows show dependencies between use cases (e.g., applying requires document upload).

---

## Actors

- **Customer** – external user who registers, logs in, submits loan applications, uploads documents, tracks status, and receives notifications.  
- **Loan Officer** – internal user who reviews applications, verifies documents, requests clarifications, and makes approval or rejection decisions.  
- **Admin** – system administrator who manages users/roles, configures loan policies, and generates reports for compliance and analytics.  

---

## Major Use Cases

- **Register** – create an account with OTP verification (FR1).  
- **Login / Authenticate** – secure access with credentials and optional 2FA (FR2).  
- **Submit Loan Application** – enter personal, employment, and loan details; creates an application record (FR3, FR6).  
- **Upload Documents** – upload PAN, Aadhaar, and income proof with validation (FR7).  
- **Track Application Status** – view progress through statuses such as Submitted, In Review, Approved/Rejected (FR10).  
- **Receive Notifications** – email/SMS alerts for status changes (FR22).  
- **Review Application** – loan officer reviews submitted details and attached documents (FR9).  
- **Verify Documents** – loan officer verifies authenticity of uploaded documents (FR6).  
- **Approve / Reject Application** – loan officer provides decision; rejection requires mandatory reason (FR11).  
- **Request More Information** – loan officer requests clarifications or additional documents, triggering customer action (FR21).  
- **Manage Users / Roles** – admin manages user lifecycle and access permissions (FR12).  
- **Configure Loan Policies** – admin defines eligibility rules, interest rates, and thresholds (FR8).  
- **Generate Reports & MIS** – admin generates operational and compliance reports (FR26).  

---

## Relationships
- **Solid lines** – actor performs the use case.  
- **Dashed arrows** – dependency between use cases (e.g., *Submit Loan Application → Upload Documents*).  

---

## Diagram Files
- `LoanSystem_UseCaseDiagram.xml` – editable Draw.io source file.  
- `LoanSystem_UseCaseDiagram.png` – exported image for quick reference.  
