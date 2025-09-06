# Screen-Level Specifications – Online Loan Application System

This document expands Section 7 of the FRD with detailed **field-level and screen-level requirements** for both Customer and Admin views.  

---

## 1. Customer Screens  

### 1.1 Registration Screen  

| Field Name        | Type        | Validation Rules                            | Mandatory | Notes |
|-------------------|------------|---------------------------------------------|-----------|-------|
| Full Name         | Text       | Alphabets only, min 3 chars                 | Yes       |       |
| Email             | Text       | Must be valid email format                  | Yes       | Unique |
| Mobile Number     | Numeric    | 10 digits only                              | Yes       | OTP sent |
| Password          | Password   | Min 8 chars, 1 upper, 1 lower, 1 number     | Yes       |       |
| Confirm Password  | Password   | Must match Password                         | Yes       |       |

**Error Handling:**  
- Show inline validation messages (e.g., *“Email already exists”*).  
- If OTP not verified, registration cannot proceed.  

---

### 1.2 Login Screen  

| Field Name   | Type      | Validation Rules               | Mandatory | Notes |
|--------------|----------|--------------------------------|-----------|-------|
| Email/Mobile | Text     | Must exist in database          | Yes       |       |
| Password     | Password | Must match registered password | Yes       |       |

**Error Handling:**  
- Show error: *“Invalid credentials”*.  
- Account lockout after 5 failed attempts.  

---

### 1.3 Loan Application Form  

| Section            | Field Name         | Type        | Validation Rules                        | Mandatory | Notes |
|--------------------|-------------------|------------|-----------------------------------------|-----------|-------|
| Personal Details   | Full Name          | Text       | Alphabets only                          | Yes       | Pre-filled if registered |
|                    | Date of Birth      | Date       | Age must be >= 21                       | Yes       |       |
|                    | PAN Number         | Text       | 10-digit alphanumeric                   | Yes       | Unique |
| Employment Details | Employer Name      | Text       |                                         | Yes       |       |
|                    | Income             | Numeric    | Must be > 0                             | Yes       |       |
| Loan Details       | Loan Amount        | Numeric    | Between ₹50,000 – ₹50,00,000            | Yes       |       |
|                    | Tenure             | Dropdown   | 12/24/36/48/60 months                   | Yes       |       |

**Error Handling:**  
- If PAN already in system → reject duplicate.  
- Loan amount > income × 20 → show error.  

---

### 1.4 Document Upload Screen  

| Field Name   | Type    | Validation Rules            | Mandatory | Notes |
|--------------|--------|-----------------------------|-----------|-------|
| PAN Card     | Upload | Only PDF/JPEG/PNG ≤ 5 MB    | Yes       | OCR-enabled |
| Aadhar Card  | Upload | Only PDF/JPEG/PNG ≤ 5 MB    | Yes       | OCR-enabled |
| Salary Slip  | Upload | Only PDF ≤ 5 MB             | Yes       | For employed |
| Bank Statement | Upload | Only PDF ≤ 10 MB          | Optional  | For income proof |

**Error Handling:**  
- Wrong format → error message.  
- File too large → prompt to re-upload.  

---

### 1.5 Status Dashboard  

| Field Name          | Type     | Rules                                   | Mandatory | Notes |
|---------------------|---------|-----------------------------------------|-----------|-------|
| Application ID      | Text    | Auto-generated                          | Yes       |       |
| Current Status      | Label   | “Submitted”, “In Review”, “Approved”…   | Yes       |       |
| Last Updated Date   | Date    |                                         | Yes       |       |
| Next Action         | Label   | “Awaiting Docs”, “Pending Review”…      | No        |       |

---

## 2. Admin Screens  

### 2.1 Admin Login  

(Same as Customer Login, but role = Admin)  

---

### 2.2 Application Review Screen  

| Field Name          | Type     | Rules                                   | Mandatory | Notes |
|---------------------|---------|-----------------------------------------|-----------|-------|
| Application ID      | Text    | Auto-generated                          | Yes       |       |
| Customer Name       | Text    |                                         | Yes       |       |
| Loan Amount         | Text    |                                         | Yes       |       |
| Uploaded Documents  | Links   | Openable inline                         | Yes       |       |
| Risk Score          | Numeric | Calculated automatically                | Yes       |       |
| Decision            | Dropdown| Approve / Reject / On-Hold              | Yes       | Mandatory before saving |

**Error Handling:**  
- If Decision = Reject → rejection reason must be entered.  

---

### 2.3 Reports Screen  

| Report Name         | Fields                                   | Frequency | Notes |
|---------------------|------------------------------------------|-----------|-------|
| Loan Application Report | Total submitted, approved, rejected | Daily     | Export CSV |
| Turnaround Time     | Avg approval time by officer            | Weekly    | Dashboard |
| Risk Analysis       | Applications by risk category           | Monthly   | Dashboard |

---

# Summary  
- Customer screens: Registration, Login, Loan Application, Document Upload, Status Dashboard.  
- Admin screens: Login, Application Review, Reports.  
- Each field defined with **type, rules, mandatory status, and error handling.**  
