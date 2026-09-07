# Networkwalks-B082-WEEK4-PENETRATION-TESTING-REPORT

# Penetration Testing Project – Mediroza General Hospital

**Tester:** Jenik Shrestha  
**Batch:** B082 | Week 4  
**Assessment Date:** 2026-09-06 to 2026-09-07  
**Target:** https://medirozahospital.com  

---

## 1. Project Overview

This submission contains the complete evidence and final report for the black-box penetration testing engagement conducted against the Mediroza General Hospital web infrastructure.

The assessment was performed with explicit written authorization and adhered strictly to the defined scope. The primary objective was to identify security vulnerabilities, exploit them to demonstrate real-world impact, and provide a comprehensive remediation roadmap.

---

## 2. Key Findings Summary

The following critical and high-risk vulnerabilities were identified and successfully exploited:

- **Critical – SQL Injection (SQLi):** Authentication bypass on the patient portal (`/patient/login.php`) allowing unauthorized access to Protected Health Information (PHI).
- **High – Weak Default Credentials:** The `admin` account was compromised using the password `password123`.
- **High – Information Disclosure:** A historical database backup (`/old/mediroza_db_backup_2019.sql`) was found publicly exposed, leaking 30 employee records (including National IDs and monthly salaries) and 10 shareholder details.
- **High – Weak PDF Encryption:** The three (3) retrieved patient lab reports were secured using trivial passwords, which were successfully recovered.

---

## 3. Submission Folder Structure

The evidence is organized by milestones for easy verification:

| Folder | Description |
| :--- | :--- |
| **M1_Access_and_PDFs/** | Contains the original encrypted PDF reports, brute-force proof (`mediroza_results.json`), SQLi bypass proof (`bypass_success.html`), and visual screenshots of the authenticated dashboard. |
| **M2_Cracked_PDFs/** | Contains the decrypted text files (`rep1.txt`, `rep2.txt`, `rep3.txt`) and screenshots confirming the hashcat cracking results. |
| **M3_Data_Exposure/** | Contains the exposed `full_backup.sql` file along with screenshots showing the extracted employee salaries and shareholder percentages. |
| **M4_Report/** | Contains the final penetration testing report (`Mediroza_Pentest_Report_FINAL.pdf`). |

---

## 4. Credentials & Recovered Passwords

The following credentials and passwords were discovered during the assessment:

| Type | Username / File | Password / Key |
| :--- | :--- | :--- |
| **Patient Portal Login** | `admin` | `password123` |
| **PDF Report 1** (Sipho Dlamini) | `rep1.pdf` | `123456` |
| **PDF Report 2** (Priya Reddy) | `rep2.pdf` | `password` |
| **PDF Report 3** (Emily Thompson) | `rep3.pdf` | `!@#$%^&` |

---

## 5. Milestone Completion Status

All four (4) project milestones have been successfully achieved:

| Milestone | Task | Status |
| :--- | :--- | :--- |
| **M1** | Find the 3 confidential PDF lab reports | ✅ **COMPLETED** |
| **M2** | Crack the encryption on all 3 retrieved files | ✅ **COMPLETED** |
| **M3** | Find the critical data exposure (Salaries & Shareholders) | ✅ **COMPLETED** |
| **M4** | Write the detailed Penetration Testing Report | ✅ **COMPLETED** |

---

## 6. How to Review the Submission

1. Extract the contents of the ZIP file.
2. Review the **Mediroza_Pentest_Report_FINAL.pdf** located in the `M4_Report/` folder for the full technical write-up, remediation steps, and appendix.
3. Refer to the specific milestone folders (`M1`, `M2`, `M3`) to cross-check the visual evidence (screenshots) and raw files referenced in the report.

---

## 7. Disclaimer

This report and its contents are confidential and intended solely for Mediroza General Hospital and authorized stakeholders. The findings are based on a specific testing window and may not cover all possible vulnerabilities.

---
**Prepared by:** Jenik Shrestha  
**Date:** 2026-09-07
