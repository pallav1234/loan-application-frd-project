# Screen-Level Specifications – Online Loan Application System  

This document expands Section 7 of the FRD with detailed **field-level and screen-level requirements** for both Customer and Admin views.  
Each field is assigned a **unique ID**, mapped to **FRD requirements**, and prioritized.  

---

## 1. Customer Screens  

### 1.1 Registration Screen  

| Field ID   | Field Name       | Type      | Validation Rules                          | Mandatory | Priority | FRD Ref | Notes |
|------------|-----------------|-----------|-------------------------------------------|-----------|----------|---------|-------|
| REG_FN_001 | Full Name        | Text      | Alphabets only, min 3 chars               | Yes       | High     | FR1     |       |
| REG_EM_002 | Email            | Text      | Must be valid email format                | Yes       | High     | FR1     | Unique |
| REG_MN_003 | Mobile Number    | Numeric   | 10 digits only, OTP sent                  | Yes       | High     | FR2     | OTP verified before save |
| REG_PW_004 | Password         | Password  | Min 8 chars, 1 upper, 1 lower, 1 number   | Yes       | High     | FR2     | Show password toggle |
| REG_CP_005 | Confirm Password | Password  | Must match Password                       | Yes       | High     | FR2     |       |

**Error Handling:**  
- If email already exists → *“Email already registered”*.  
- If OTP not verified → registration cannot proceed.  
- Weak password → inline message.  

---

### 1.2 Login Screen  

| Field ID   | Field Name   | Type      | Validation Rules               | Mandatory | Priority | FRD Ref | Notes |
|------------|-------------|-----------|--------------------------------|-----------|----------|---------|-------|
| LOG_UN_001 | Email/Mobile | Text     | Must exist in database          | Yes       | High     | FR2     |       |
| LOG_PW_002 | Password     | Password | Must match registered password | Yes       | High     | FR2     |       |

**Error Handling:**  
- Invalid credentials → *“Incorrect username or password”*.  
- Account locked after 5 failed attempts → *“Account temporarily locked”*.  

---

### 1.3 Loan Application Form  

| Section            | Field ID    | Field Name       | Type      | Validation Rules                         | Mandatory | Priority | FRD Ref | Notes |
|--------------------|-------------|------------------|-----------|------------------------------------------|-----------|----------|---------|-------|
| Personal Details   | APP_FN_001  | Full Name        | Text      | Alphabets only                           | Yes       | High     | FR3     | Pre-filled from registration |
|                    | APP_DOB_002 | Date of Birth    | Date      | Age must be ≥ 21                         | Yes       | High     | FR3     |       |
|                    | APP_PAN_003 | PAN Number       | Text      | 10-digit alphanumeric                    | Yes       | High     | FR4     | Unique |
| Employment Details | APP_EM_004  | Employer Name    | Text      |                                          | Yes       | Medium   | FR5     |       |
|                    | APP_INC_005 | Income           | Numeric   | Must be > 0                              | Yes       | High     | FR5     | Monthly income |
| Loan Details       | APP_AMT_006 | Loan Amount      | Numeric   | ₹50,000 – ₹50,00,000                     | Yes       | High     | FR6     |       |
|                    | APP_TEN_007 | Tenure           | Dropdown  | 12/24/36/48/60 months                    | Yes       | Medium   | FR6     |       |

**Error Handling:**  
- Duplicate PAN → *“Application already exists”*.  
- Loan amount > (Income × 20) → error message.  
- Missing mandatory field → inline validation.  

---

### 1.4 Document Upload Screen  

| Field ID    | Field Name     | Type    | Validation Rules             | Mandatory | Priority | FRD Ref | Notes |
|-------------|---------------|---------|------------------------------|-----------|----------|---------|-------|
| DOC_PAN_001 | PAN Card       | Upload  | PDF/JPEG/PNG ≤ 5 MB          | Yes       | High     | FR7     | OCR-enabled |
| DOC_AAD_002 | Aadhar Card    | Upload  | PDF/JPEG/PNG ≤ 5 MB          | Yes       | High     | FR7     | OCR-enabled |
| DOC_SAL_003 | Salary Slip    | Upload  | PDF ≤ 5 MB                   | Yes       | High     | FR7     | Only if employed |
| DOC_BNK_004 | Bank Statement | Upload  | PDF ≤ 10 MB                  | Optional  | Medium   | FR7     | For self-employed |

**Error Handling:**  
- Invalid format → error.  
- File too large → prompt to re-upload.  

---

### 1.5 Status Dashboard  

| Field ID   | Field Name        | Type     | Rules                                 | Mandatory | Priority | FRD Ref | Notes |
|------------|------------------|---------|---------------------------------------|-----------|----------|---------|-------|
| STAT_ID_01 | Application ID    | Text    | Auto-generated                        | Yes       | High     | FR8     |       |
| STAT_ST_02 | Current Status    | Label   | Submitted / In Review / Approved etc. | Yes       | High     | FR8     | Color-coded |
| STAT_DT_03 | Last Updated Date | Date    | Auto-updated                          | Yes       | Medium   | FR8     |       |
| STAT_NX_04 | Next Action       | Label   | Awaiting Docs / Pending Review etc.   | No        | Medium   | FR8     |       |

---

## 2. Admin Screens  

### 2.1 Admin Login  

(Same as Customer Login, but with **role = Admin**)  

---

### 2.2 Application Review Screen  

| Field ID   | Field Name        | Type     | Rules                                   | Mandatory | Priority | FRD Ref | Notes |
|------------|------------------|---------|-----------------------------------------|-----------|----------|---------|-------|
| REV_ID_001 | Application ID    | Text     | Auto-generated                          | Yes       | High     | FR9     |       |
| REV_CN_002 | Customer Name     | Text     |                                         | Yes       | High     | FR9     |       |
| REV_AM_003 | Loan Amount       | Numeric  |                                         | Yes       | High     | FR9     |       |
| REV_DOC_04 | Uploaded Documents| Links    | Open inline                             | Yes       | High     | FR9     | OCR view enabled |
| REV_RSK_05 | Risk Score        | Numeric  | Auto-calculated                         | Yes       | High     | FR10    |       |
| REV_DEC_06 | Decision          | Dropdown | Approve / Reject / On-Hold              | Yes       | High     | FR11    | Mandatory before save |
| REV_RSN_07 | Rejection Reason  | Text     | Mandatory if Decision = Reject          | Conditional | High  | FR11    | Visible only if rejected |

**Error Handling:**  
- If “Reject” selected but no reason entered → block submission.  
- Once rejected → status = “Rejected”, customer notified via email + dashboard.  
- Rejected application locked from editing unless resubmitted.  

---

### 2.3 Reports Screen  

| Report ID | Report Name              | Fields                                   | Frequency | Priority | FRD Ref | Notes |
|-----------|--------------------------|------------------------------------------|-----------|----------|---------|-------|
| REP_001   | Loan Application Report  | Total submitted, approved, rejected       | Daily     | High     | FR12    | Export to CSV |
| REP_002   | Turnaround Time          | Avg approval time by officer             | Weekly    | Medium   | FR12    | Dashboard |
| REP_003   | Risk Analysis            | Applications by risk category            | Monthly   | Medium   | FR12    | Dashboard |

---
.  

