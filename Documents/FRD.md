# Functional Requirements Document (FRD)

**Project:** Online Loan Application System  
**Version:** 1.0  
**Date:** YYYY-MM-DD  
**Author:** Pallav Daru

---

## 1. Introduction
- **Purpose:** Translate business needs (from BRD) into detailed functional requirements, workflows, and rules for the Online Loan Application System.
- **Scope:** The system will allow customers to apply for loans online, upload supporting documents, track application status, and receive approvals digitally. Loan officers/admins will review, approve/reject, and manage policies.
- **References:** BRD v1.0, Stakeholder Interviews, Regulatory Compliance Documents.

---

## 2. System Overview
The Online Loan Application System is a web-based platform where:
- Customers can register, log in, apply for loans, upload documents, and track progress.
- Loan officers verify applications and documents, perform credit checks and make decisions.
- Admins configure policies, manage users, and generate reports.
- System integrates with external Credit Bureau and Notification Services.

---

## 3. Actors and Roles

<table>
  <thead>
    <tr>
      <th>Actor</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>Customer</strong></td>
      <td>End-user applying for loans, uploads documents, tracks status, views offers.</td>
    </tr>
    <tr>
      <td><strong>Loan Officer</strong></td>
      <td>Reviews applications, verifies documents, approves/rejects, requests clarifications.</td>
    </tr>
    <tr>
      <td><strong>Admin</strong></td>
      <td>Configures loan policies, manages users/roles, generates reports and dashboards.</td>
    </tr>
    <tr>
      <td><strong>External System (Credit Bureau)</strong></td>
      <td>Provides credit score & risk profile via API.</td>
    </tr>
    <tr>
      <td><strong>Notification Service</strong></td>
      <td>Sends SMS / Email notifications to customers and staff.</td>
    </tr>
    <tr>
      <td><strong>OCR / Document Service (future)</strong></td>
      <td>Optional automated document parsing & verification.</td>
    </tr>
  </tbody>
</table>

---

## 4. Functional Requirements (detailed table)
> The table below lists the primary functional requirements. Each FR will be expanded in the **Detailed Use Cases** section.

<table>
  <thead>
    <tr>
      <th>ID</th>
      <th>Requirement (high-level)</th>
      <th>Priority</th>
      <th>Notes / Negative Scenarios</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>FR1</td>
      <td>Customer registration: system shall allow new users to register (Name, Email, Mobile, Password).</td>
      <td>High</td>
      <td>Duplicate email/mobile prevented; invalid format rejected.</td>
    </tr>
    <tr>
      <td>FR2</td>
      <td>Authentication: secure login with password + OTP (2FA) and account lockout after repeated failures.</td>
      <td>High</td>
      <td>Lock account after 5 failed attempts; expired OTP; password reset flow required.</td>
    </tr>
    <tr>
      <td>FR3</td>
      <td>Loan application creation: customers can create & submit loan applications (personal, financial data).</td>
      <td>High</td>
      <td>Mandatory fields validated; underage (<18) prevented; invalid PAN format rejected.</td>
    </tr>
    <tr>
      <td>FR4</td>
      <td>Save as draft: customer can save unfinished applications and resume later.</td>
      <td>Medium</td>
      <td>Drafts expire after X days (configurable).</td>
    </tr>
    <tr>
      <td>FR5</td>
      <td>Document upload: allow upload of KYC & income docs (PDF/JPEG/PNG), size limit 10MB.</td>
      <td>High</td>
      <td>Reject unsupported type, large files, corrupted files; show error and retry option.</td>
    </tr>
    <tr>
      <td>FR6</td>
      <td>Document verification: manual (Loan Officer) and optional OCR-assisted verification.</td>
      <td>High</td>
      <td>OCR false positives flagged for manual review.</td>
    </tr>
    <tr>
      <td>FR7</td>
      <td>Credit check integration: fetch credit score & bureau report via API after submission.</td>
      <td>High</td>
      <td>Retry logic (3x) on API failure; fallback to manual review if service unavailable.</td>
    </tr>
    <tr>
      <td>FR8</td>
      <td>Eligibility calculation: auto-calc eligibility using salary, existing EMIs, and rules (e.g., max EMI ≤ 40% salary).</td>
      <td>High</td>
      <td>Rules configurable; log rule version for audit.</td>
    </tr>
    <tr>
      <td>FR9</td>
      <td>Application review: loan officers can view, comment, request docs, approve or reject applications.</td>
      <td>High</td>
      <td>Support reassign, escalate, bulk actions; session timeout handling.</td>
    </tr>
    <tr>
      <td>FR10</td>
      <td>Status tracking & notifications: customers view status and receive SMS/email on key events.</td>
      <td>High</td>
      <td>Notification failures retried once; all notifications logged.</td>
    </tr>
    <tr>
      <td>FR11</td>
      <td>Admin reporting & management: generate standard MIS reports and manage users/roles.</td>
      <td>High</td>
      <td>Export to CSV/PDF; pagination for large datasets.</td>
    </tr>
    <tr>
      <td>FR12</td>
      <td>Audit & logs: every critical action is logged with user, timestamp, and reason.</td>
      <td>High</td>
      <td>Logs stored for 7–10 years (configurable).</td>
    </tr>
    <tr>
      <td>FR13</td>
      <td>Security & compliance: role-based access, data encryption at rest/in transit, GDPR/KYC/AML compliance controls.</td>
      <td>High</td>
      <td>Encryption keys rotated per policy; PII masking in reports.</td>
    </tr>
  </tbody>
</table>

---

## 5. Non-Functional Requirements (NFRs)

<table>
  <thead>
    <tr>
      <th>Category</th>
      <th>Requirement</th>
      <th>Acceptance Criteria</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Performance</td>
      <td>Support 500 concurrent users initially; scale to 5,000 with horizontal scaling.</td>
      <td>Response time &lt; 3s for main flows under specified load.</td>
    </tr>
    <tr>
      <td>Security</td>
      <td>AES-256 at rest, TLS 1.2+ in transit, RBAC, 2FA, audit logs.</td>
      <td>Security scans show no critical vulnerabilities; compliance checklist passed.</td>
    </tr>
    <tr>
      <td>Availability</td>
      <td>99.5% uptime SLA.</td>
      <td>Downtime &lt; X hours/month; failover documented.</td>
    </tr>
    <tr>
      <td>Usability</td>
      <td>Mobile-first responsive UI; average new user can submit application within 8 minutes.</td>
      <td>Usability test > 90% success rate for core flow.</td>
    </tr>
    <tr>
      <td>Scalability</td>
      <td>Service-oriented architecture with autoscaling for peak loads.</td>
      <td>System scales linearly up to target load with acceptable performance.</td>
    </tr>
    <tr>
      <td>Data retention</td>
      <td>Customer & application data retained 7 years; audit logs 10 years.</td>
      <td>Retention policy enforced automatically.</td>
    </tr>
  </tbody>
</table>

---

## 6. Detailed Use Cases (expanded — required for FRD)

> For each use case below we give: Actor, Preconditions, Steps (main flow), Exceptions / Negative scenarios, Postconditions.
> See [Use Case Diagram](use_case_diagram.png).  

### Use Case UC-01: User Registration
**Actor:** Customer  
**Preconditions:** None (new user)  
**Main Steps:**
1. Customer selects "Register".
2. System displays registration form (Name, Email, Mobile, DOB, Password).
3. Customer completes fields and submits.
4. System validates formats and uniqueness of email/mobile.
5. System sends OTP to mobile/email.
6. Customer enters OTP; system verifies OTP.
7. Account created; user redirected to dashboard.

**Exceptions / Negative Scenarios:**
- Duplicate email/mobile → show "Account exists".
- OTP expires → allow resend (max 3 times).
- Weak password → show password requirements.

**Postconditions:** Account active, user logged in (or prompted to login).

---

### Use Case UC-02: User Login & Forgot Password
**Actor:** Customer  
**Preconditions:** Account exists  
**Main Steps:**
1. Customer enters email/mobile + password.
2. System validates credentials.
3. If 2FA enabled, system prompts for OTP and verifies.
4. On success, user redirected to dashboard.

**Exceptions:**
- 5 failed attempts → account locked for configurable period.
- Expired 2FA OTP → prompt to resend.
- Forgot password → send password reset link (expires in X minutes).

**Postconditions:** User authenticated and session created.

---

### Use Case UC-03: Create / Save / Submit Loan Application
**Actor:** Customer  
**Preconditions:** Logged in and KYC not-deferred (or flagged to complete later)  
**Main Steps:**
1. Customer selects "Apply for Loan".
2. System displays loan form (Personal, Employment, Financial, Loan details).
3. Customer can **Save Draft** or **Submit**.
4. On Submit, system validates mandatory fields and business rules (age ≥ 18, PAN format).
5. System calculates preliminary eligibility.
6. System stores application and assigns Application ID.
7. System triggers Credit Bureau API (async or sync as per config).
8. Status = "Submitted" (then "In Review" once officer picks).

**Exceptions / Negative Scenarios:**
- Missing mandatory fields → block submission with field-level error messages.
- Invalid PAN/Aadhaar formats → field error.
- File upload failure → provide retry and save partial state.
- Credit Bureau API unavailable → set status "Pending Credit Check" and notify admin.

**Postconditions:** Application recorded; next steps for document upload/review.

---

### Use Case UC-04: Document Upload & Validation
**Actor:** Customer / Loan Officer (verification)  
**Preconditions:** Application exists (submitted or draft)  
**Main Steps (Customer):**
1. Customer navigates to Documents section of application.
2. Uploads files (ID, Address Proof, Income Proof). Each must be PDF/JPEG/PNG and ≤ 10MB.
3. System stores file meta and content (object store with secure links).
4. Optional: OCR service attempts data extraction and flags anomalies.

**Main Steps (Loan Officer):**
1. Loan Officer views uploaded documents.
2. Marks each as Verified / Rejected with comments.

**Exceptions:**
- Unsupported file type → reject upload.
- Corrupted file → show error and request re-upload.
- Virus detected → quarantine file and alert security.

**Postconditions:** Documents stored and verification status updated.

---

### Use Case UC-05: Credit Check (External Integration)
**Actor:** System / Credit Bureau API  
**Preconditions:** Application submitted and consent provided for credit check  
**Main Steps:**
1. System requests credit report using customer identifiers.
2. Credit Bureau returns score and report (or error).
3. System stores result and updates eligibility calculation.

**Exceptions:**
- API failure → retry 3 times with exponential backoff, then mark "Credit Check Failed".
- Invalid identifiers → report error to user and admin.

**Postconditions:** Credit score stored; used for decision rules.

---

### Use Case UC-06: Review, Approve, Reject, Request More Info
**Actor:** Loan Officer / Admin  
**Preconditions:** Application submitted and documents uploaded  
**Main Steps:**
1. Officer opens application, reviews fields, documents, credit report.
2. Officer may request additional documentation (request logged & customer notified).
3. Officer may Approve or Reject; enters remarks and changes status.
4. On Approve → system triggers disbursement workflow (if configured).
5. On Reject → system notifies customer with reason codes.

**Exceptions:**
- Officer session timeout during approval → save draft and prompt to re-login.
- Conflicting changes by multiple officers → lock record during edit.

**Postconditions:** Status updated; notifications sent; audit logged.

---

### Use Case UC-07: Admin — Policy & User Management, Reports
**Actor:** Admin  
**Main Steps:**
1. Admin configures loan policy (max loan multiplier, min credit score, EMI percentage).
2. Admin creates/removes users and roles; resets passwords.
3. Admin runs reports (daily approvals, avg TAT, rejection reasons) and exports results.

**Exceptions:**
- Unauthorized action blocked by RBAC.
- Report generation failure → show "No records" or log error.

**Postconditions:** Admin changes applied; audit recorded.

---

### Use Case UC-08: Notifications & Tracking
**Actor:** System / Notification Service  
**Main Steps:**
1. On key events (Submitted, In Review, Approved, Rejected), system sends SMS/Email.
2. Customers view status in dashboard; timeline shows all events.

**Exceptions:**
- Notification service failure → retry once, log failure, show indicator in admin dashboard.

---

### Use Case UC-09: Audit & Logging
**Actor:** System / Admin  
**Main Steps:**
1. All critical actions (approve/reject, data changes) logged with user, timestamp, and reason.
2. Admin can view audit trail for compliance.

---

## 7. Field-level / Screen-level Specifications (sample – expandable)
> This is where FRD is most detailed: field names, types, mandatory flag, validation rules, error messages.

<table>
  <thead>
    <tr>
      <th>Screen / Form</th>
      <th>Field</th>
      <th>Type</th>
      <th>Required?</th>
      <th>Validation</th>
      <th>Error Message</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td rowspan="5">Loan Application Form</td>
      <td>Full Name</td>
      <td>String</td>
      <td>Yes</td>
      <td>Max 100 chars</td>
      <td>"Please enter your full name."</td>
    </tr>
    <tr>
      <td>Date of Birth</td>
      <td>Date</td>
      <td>Yes</td>
      <td>Age ≥ 18</td>
      <td>"Applicant must be 18 years or older."</td>
    </tr>
    <tr>
      <td>PAN</td>
      <td>String</td>
      <td>Yes</td>
      <td>Regex: 5 letters + 4 digits + 1 letter (length 10)</td>
      <td>"Invalid PAN format."</td>
    </tr>
    <tr>
      <td>Loan Amount</td>
      <td>Numeric</td>
      <td>Yes</td>
      <td>Min 50,000; Max depend on eligibility calc</td>
      <td>"Requested amount exceeds eligibility."</td>
    </tr>
    <tr>
      <td>Email</td>
      <td>String</td>
      <td>Yes</td>
      <td>Valid email format</td>
      <td>"Please enter a valid email."</td>
    </tr>
  </tbody>
</table>

> Expand this table for all screens (Login, Forgot Password, Documents, Admin console).

For detailed screen-level specifications, refer to [Screen Specifications](Screen_Specifications.md).

---

## 8. Integration Points (APIs and External Systems)

<table>
  <thead>
    <tr>
      <th>Integration</th>
      <th>Purpose</th>
      <th>Protocol / Notes</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Credit Bureau API</td>
      <td>Fetch credit score & report</td>
      <td>HTTPS REST; OAuth 2.0; retry policy 3 attempts</td>
    </tr>
    <tr>
      <td>Notification Service</td>
      <td>Send SMS / Email</td>
      <td>HTTPS REST; idempotency keys for retries</td>
    </tr>
    <tr>
      <td>Payment Gateway</td>
      <td>Repayment & disbursement (optional)</td>
      <td>HTTPS REST; PCI-DSS compliance</td>
    </tr>
    <tr>
      <td>OCR / Document Service</td>
      <td>Extract data from uploaded docs (future)</td>
      <td>Async processing; queue-based architecture</td>
    </tr>
  </tbody>
</table>

---

## 9. Error Handling & Negative Scenarios (summary)
- **Authentication:** Lock after 5 failed attempts; notify user and admin.
- **File Upload:** Reject >10MB, unsupported types, or corrupted files; offer retry.
- **External API Failures:** Retry with exponential backoff (3 times), then mark stacked state and notify admin.
- **Business Rule Violations:** Show explicit error messages (e.g., "Exceeds allowed amount", "Age below threshold").
- **Concurrency:** Lock application record during officer edit to prevent conflicting updates.
- **Data Validation:** All incoming data validated server-side; client-side validation only for UX.

---

## 10. Reports & Dashboards

<table>
  <thead>
    <tr>
      <th>Report / Dashboard</th>
      <th>Description</th>
      <th>Export</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Daily Approvals</td>
      <td>Number & value of loans approved per day</td>
      <td>CSV / PDF</td>
    </tr>
    <tr>
      <td>Rejection Reasons</td>
      <td>Aggregate reasons and counts for rejections</td>
      <td>CSV / PDF</td>
    </tr>
    <tr>
      <td>Average TAT</td>
      <td>Average time from submission to decision</td>
      <td>CSV / PDF</td>
    </tr>
  </tbody>
</table>

---

## 11. Data Requirements (detailed)

<table>
  <thead>
    <tr>
      <th>Data Entity</th>
      <th>Storage</th>
      <th>Retention</th>
      <th>Notes</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Customer</td>
      <td>Relational DB (Postgres/MySQL)</td>
      <td>7 years</td>
      <td>PII encrypted at rest</td>
    </tr>
    <tr>
      <td>Application</td>
      <td>Relational DB</td>
      <td>7 years</td>
      <td>Application history & versions stored</td>
    </tr>
    <tr>
      <td>Documents</td>
      <td>Object store (S3) + metadata in DB</td>
      <td>7 years</td>
      <td>Secure links, virus-scan on upload</td>
    </tr>
    <tr>
      <td>Audit Logs</td>
      <td>DB + long-term cloud archive</td>
      <td>10 years</td>
      <td>Immutable logs for compliance</td>
    </tr>
  </tbody>
</table>

---

## 12. Assumptions & Constraints
- Users have internet-enabled devices and valid Govt IDs.
- Third-party Credit Bureau APIs are available and provide required data.
- OCR & advanced automation are future scope (may be phased).
- System will comply with KYC/AML and applicable regional data privacy laws (GDPR where relevant).

---

## 13. Traceability: User Stories → FR mapping

<table>
  <thead>
    <tr>
      <th>User Story ID</th>
      <th>User Story</th>
      <th>Mapped FR(s)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>US-01</td>
      <td>As a customer, I want to register so that I can apply for a loan online.</td>
      <td>FR1–FR2</td>
    </tr>
    <tr>
      <td>US-02</td>
      <td>As a customer, I want to log in securely so that my personal and financial data is protected.</td>
      <td>FR2</td>
    </tr>
    <tr>
      <td>US-03</td>
      <td>As a customer, I want to submit a loan application so that I can apply for financing digitally without visiting a branch.</td>
      <td>FR3–FR8</td>
    </tr>
    <tr>
      <td>US-04</td>
      <td>As a customer, I want to upload supporting documents so that my loan application can be verified quickly.</td>
      <td>FR5–FR6</td>
    </tr>
    <tr>
      <td>US-05</td>
      <td>As a customer, I want to track my application status so that I stay informed about progress and next steps.</td>
      <td>FR10</td>
    </tr>
    <tr>
      <td>US-06</td>
      <td>As a loan officer, I want to review loan applications so that I can approve or reject them based on eligibility.</td>
      <td>FR9–FR11</td>
    </tr>
    <tr>
      <td>US-07</td>
      <td>As an admin, I want to generate reports so that I can monitor overall loan processing efficiency and compliance.</td>
      <td>FR11</td>
    </tr>
  </tbody>
</table>

---

## 14. Glossary
<table>
  <thead>
    <tr>
      <th>Term</th>
      <th>Definition</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>KYC</td>
      <td>Know Your Customer - identity verification process</td>
    </tr>
    <tr>
      <td>TAT</td>
      <td>Turnaround Time</td>
    </tr>
    <tr>
      <td>OCR</td>
      <td>Optical Character Recognition</td>
    </tr>
  </tbody>
</table>

---


