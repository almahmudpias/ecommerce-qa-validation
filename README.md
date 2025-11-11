# 🛒 E-Commerce Web Platform - QA Validation Report (v1.1.2)

This repository contains the complete **Quality Assurance (QA) artifacts** for the v1.1.2 release of the E-Commerce Web Platform. It documents the full QA lifecycle—**test planning, manual execution, defect tracking, and reporting**—to ensure the platform is functional, secure, and production-ready.

---

## 🌟 Key Project Highlights

| Metric | Result | Analysis |
|--------|--------|----------|
| **Test Execution** | 40 / 40 Cases Executed | 100% of planned scope covered (User Auth, Product Browse, Cart, Checkout, Security) |
| **Pass Rate** | **92.5%** (37 Passed / 3 Failed) | Core functionality stable; failures isolated to high-risk payment & auth flows |
| **Defect Density** | 10 Defects Logged | 25% of test cases revealed an issue, indicating good test case effectiveness |
| **Critical Blocker Issues** | **3** | Showstoppers: Checkout API (500 Error), Authentication Bypass, Post-Patch Regression |

---

## 📁 Repository Structure

| Folder | Content | Description |
|--------|---------|-------------|
| `01_Test_Plan/` | `Test_Plan_V1.0.pdf` | Scope, objectives, strategy, schedule, and deliverables for testing |
| `02_Test_Cases/` | `E-Commerce_Test_Cases.xlsx`, `Test_Execution_Report.pdf` | Full list of 40 test cases and final execution results |
| `03_Bug_Reports/` | `Jira_Export_Bugs.xlsx`, Screenshots | Detailed defect reports with severity, steps-to-reproduce, and visual evidence |
| `04_Summary_Report/` | `QA_Summary_Report_V1.0.md` | High-level analysis of test execution, defect metrics, and recommendations |
| `Screenshots/` | `.png/.jpg files` | Visual evidence of critical defects and UI issues |
| `README.md` | (This file) | Overview and navigation guide for the repository |

---

## 📈 Defect Analysis Summary

A total of **10 defects** were identified and tracked, with severity breakdown:  

![Defect Severity Pie Chart](https://quickchart.io/chart?c={type:'doughnut',data:{labels:['Critical','Major','Minor'],datasets:[{data:[3,4,3],backgroundColor:['#dc3545','#ffc107','#20c997']}]}})

### Primary Failing Areas & Root Cause Analysis

1. **Checkout Process (Critical)**
   - **Issue:** REST API endpoint `/api/v1/checkout` returns `500 Internal Server Error` on payment submission.
   - **Evidence:** Logs indicate a `NullPointerException` in `PaymentProcessorService`. **This is a release blocker.**

2. **Authentication & Security (Critical)**
   - **Issue:** Login allows access with invalid credentials (password bypass).
   - **Evidence:** Manual test shows access granted if username is valid; reproducible 100%.

3. **Product Cart Functionality (Major - Regression)**
   - **Issue:** 'Add to Cart' fails post v1.1.2 patch.
   - **Evidence:** UI shows success, but cart icon count doesn’t increment; item missing in cart page. **Regression detected.**

---

### 📋 Defect Summary Table

| ID | Module | Severity | Issue | Status |
|----|--------|---------|-------|--------|
| ECOM-101 | Checkout | Critical | API 500 Error | Open |
| ECOM-107 | Auth | Critical | Login Bypass | Open |
| ECOM-115 | Cart | Major | Add to Cart Regression | Open |
| ECOM-120 | Checkout | Minor | Slow page load | Open |
| ECOM-122 | UI | Minor | Footer misalignment | Open |
| ECOM-125 | Auth | Major | Password reset error | Open |
| ECOM-130 | Product | Major | Filter not working | Open |
| ECOM-135 | UI | Minor | Responsive issue | Open |
| ECOM-140 | Checkout | Major | Email not sent post checkout | Open |
| ECOM-145 | Product | Critical | Price mismatch | Open |

---

## 🛠 Next Steps & Recommendations

1. **🚨 Blocker Resolution (Priority 1):** Resolve **ECOM-101 (Checkout 500 Error)** and **ECOM-107 (Auth Bypass)** immediately. No release until verified.
2. **🔁 Targeted Regression Suite:** Re-run Checkout & Auth Regression Suite (25 test cases) after fixes.
3. **🤖 Automation Pipeline:** Implement Selenium Python automation for **Checkout Happy Path** and **Login Validation**.
4. **📊 Go/No-Go Recommendation:** **Release is NOT recommended**. Follow-up QA cycle required after critical fixes.

---

## 📸 Evidence

![Checkout API 500 Error](Screenshots/checkout_500_error.png)  
*Checkout API failing with 500 Internal Server Error.*

![Authentication Bypass](Screenshots/auth_bypass_evidence.png)  
*Successful login with incorrect password – critical security flaw.*

---

## 📝 Prepared By

**Md Abdullah Al Mahmud Pias (QA Engineer)**  
**Date:** 2025-11-11  

**Confidential – For Internal QA & Development Use Only**
