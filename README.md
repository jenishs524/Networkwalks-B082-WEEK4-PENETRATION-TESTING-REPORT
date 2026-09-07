# Penetration Testing Engagement Summary
## Mediroza General Hospital – Web Infrastructure Security Assessment

---

**Project Title:** Penetration Testing Project – Mediroza General Hospital  
**Tester Name:** Jenik Shrestha  
**Batch / Week:** B082 | Week 4  
**Assessment Dates:** 2026-09-06 to 2026-09-07  
**Target Domain:** https://medirozahospital.com  
**Report Date:** 2026-09-07  
**Classification:** CONFIDENTIAL – For Authorized Personnel Only  

---

## 1. Executive Summary

This submission encapsulates the complete deliverables for the black‑box penetration testing engagement conducted against the Mediroza General Hospital web infrastructure. The assessment was performed with explicit written authorization and adhered strictly to the defined scope of work (no social engineering, no Denial of Service, and testing limited to the target domain).

The engagement successfully identified **critical vulnerabilities** within the patient portal (`/patient/login.php`), including a **SQL Injection (SQLi)** authentication bypass and **weak default credentials** (`admin` / `password123`). These flaws allowed unauthorized access to three (3) confidential patient lab reports. The reports were protected with trivially weak passwords (`123456`, `password`, `!@#$%^&`), which were recovered using hashcat.

Additionally, a **historical database backup** (`mediroza_db_backup_2019.sql`) was discovered exposed in the `/old/` directory. This file contained 30 employee records (including National IDs and monthly salaries) and 10 shareholder records (including ownership percentages).

All **four (4) project milestones** were successfully achieved. This README serves as the index to the evidence provided in the attached ZIP archive.

---

## 2. Risk Rating Summary

| Vulnerability | Severity | CVSS Score | Status |
| :--- | :--- | :--- | :--- |
| SQL Injection (Authentication Bypass) | **Critical** | 9.8 | Exploited |
| Weak Default Credentials (`admin/password123`) | High | 7.5 | Discovered |
| Exposed Database Backup (PII & Financial Data) | High | 7.5 | Verified |
| Weak PDF Encryption (Patient Lab Reports) | High | 7.4 | Cracked |
| Directory Listing Enabled | Medium | 5.3 | Discovered |
| Username Enumeration | Low | 3.7 | Identified |

---

## 3. Credentials & Recovered Passwords

The following sensitive credentials and cryptographic keys were successfully recovered during the assessment:

| Target | Username / File | Password / Key |
| :--- | :--- | :--- |
| **Patient Portal Login** | `admin` | `password123` |
| **Lab Report – Sipho Dlamini** | `patient_report_001.pdf` | `123456` |
| **Lab Report – Priya Reddy** | `patient_report_002.pdf` | `password` |
| **Lab Report – Emily Thompson** | `patient_report_003.pdf` | `!@#$%^&` |

---

## 4. Submission Folder Structure (Evidence Index)

The evidence is organized by milestones to facilitate seamless verification by the examiner:

| Folder | Contents | Milestone |
| :--- | :--- | :--- |
| **M1_Access_and_PDFs/** | `mediroza_results.json`, `bypass_success.html`, `patient_report_*.pdf` (3 files), and visual screenshots of the authenticated dashboard & brute‑force proof. | M1 |
| **M2_Cracked_PDFs/** | `rep1.txt`, `rep2.txt`, `rep3.txt` (decrypted contents), and screenshots of hashcat recovery results. | M2 |
| **M3_Data_Exposure/** | `full_backup.sql` (the exposed database backup), along with screenshots of extracted employee salaries and shareholder percentages. | M3 |
| **M4_Report/** | The final penetration testing report (`Mediroza_Pentest_Report_FINAL.pdf`) containing full methodology, findings, remediation steps, and appendix. | M4 |

---

## 5. Milestone Completion Status

All project milestones have been achieved and are documented with supporting evidence:

| Milestone | Description | Status |
| :--- | :--- | :--- |
| **M1** | Attack the website and retrieve the 3 confidential patient PDF lab reports. | ✅ **COMPLETED** |
| **M2** | Crack the encryption on all 3 retrieved PDF files. | ✅ **COMPLETED** |
| **M3** | Find the critical data exposure – employee salaries and shareholder details. | ✅ **COMPLETED** |
| **M4** | Write the detailed, professional Penetration Testing Report. | ✅ **COMPLETED** |

---

## 6. How to Navigate This Submission

1. **Extract** the ZIP archive to your local machine.
2. **Open** `M4_Report/Mediroza_Pentest_Report_FINAL.pdf` to read the comprehensive pentest report. This document contains all technical explanations, proof-of-concept commands, and remediation recommendations.
3. **Cross‑reference** the report's "Attached Evidence" section (Section 9) with the files provided in the respective milestone folders (`M1`, `M2`, `M3`) to verify the visual and technical proof.
4. The `README.md` file (this document) serves as the master index.

---

## 7. Remediation Summary

The following critical actions are recommended to the client immediately:

1. **Remediate SQL Injection:** Rewrite all SQL queries using prepared statements (PDO/MySQLi). **(Critical)**
2. **Remove Exposed Backup:** Delete `/old/mediroza_db_backup_2019.sql` and disable directory listing globally. **(Critical)**
3. **Enforce Strong Passwords:** Remove the `admin/password123` credential and implement strong password policies. **(High)**
4. **Secure PDF Downloads:** Implement server‑side authorization checks on `/patient/download.php`. **(High)**

---

## 8. Disclaimer

This report and all associated evidence are intended solely for Mediroza General Hospital and authorized project stakeholders. The findings are based on a specific testing window (2026-09-06 to 2026-09-07) and may not cover all possible vulnerabilities present in the target environment.

---

**Prepared By:** Jenik Shrestha  
**Date:** 2026-09-07  
**Classification:** CONFIDENTIAL

---
