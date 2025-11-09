---
name: Lab Submission
about: Submit your security incident lab analysis
title: '[SUBMISSION] Oğuzhan Çilkurt - Security Incident Lab'
labels: submission
assignees: ''
---

## 👤 Candidate Information

**Full Name: Oğuzhan Çilkurt** 

**Email: oguzhan196060@gmail.com** 

**LinkedIn: https://www.linkedin.com/in/oguzhan-cilkurt/**

**Submission Date: 09.11.2025** 

---

## 📎 Submission Files

**Option A: Attached Files**
- Report PDF: [[Attach here]](https://drive.google.com/file/d/1OednnfDLOBJl1CgseiXXvWJ9N6CBCn-N/view?usp=sharing)
- Video link: https://youtu.be/L_V5aRKQgls

**Option B: External Links**
- Report: [[Google Drive / Dropbox link]](https://drive.google.com/file/d/1OednnfDLOBJl1CgseiXXvWJ9N6CBCn-N/view?usp=sharing)
- Video: [[YouTube / Vimeo / Loom link]](https://youtu.be/L_V5aRKQgls)

---

## ⏱️ Time Tracking

**Total time spent:** 12 hours

**Breakdown:**
- Log analysis: 5 hours
- Architecture design: 2 hours
- Report writing: 3 hours
- Video creation: 2 hours

---

## 🎯 Summary

### Attack Vectors Identified
1.  API - Broken Object Level Authorization (BOLA)

2.  Web - SQL Injection (WAF Bypass)

3.  Email - Phishing (Domain Spoofing)

### Key Findings
- Critical BOLA Vulnerability: The API allowed a user (1523) to access other users' (1524-1538) data using their token. This was noted in the document as ‘account ownership verification may not be performed’.

- WAF Configuration Error: The WAF was left in DETECT mode for both SQLi (981001) and Rate Limit (942100) rules and did not block attacks due to blocked: no.

- Weak Rate Limiting: The API allowed the BOLA attack to be performed as ‘Fast Sequential Access’ and was not stopped by the WAF.

-  Lack of Email Authentication: The Email Gateway permitted spoofing of the security@acme-finance.com domain name, indicating a lack of DMARC/SPF/DKIM.

### Top 3 Recommendations
1. Centralised Authorisation (BOLA Fix): At the API Gateway level, implement a centralised authorisation (Policy Enforcement) rule that strictly verifies the user_id in the incoming token against the requested account_id.

2. Set WAF to ‘BLOCK’ Mode: Change 981001, 942100, and all other critical OWASP rules from DETECT mode to BLOCK mode.

3. Implement Email Security (DMARC): Implement a DMARC record with SPF, DKIM, and p=reject policy to prevent domain spoofing.

---

## 🛠️ Tools Used

**Analysis:**

- VS Code / Notepad++ (To open, review, search, and correlate log files)

- Microsoft Excel / Google Sheets (To filter, sort, and organise timestamps in CSV log files)

- Terminal / Git Bash (To run Git commands and navigate between folders)

- Manual Correlation (To manually match IP addresses, timestamps, and user IDs across different log files)

- Web Browser (To view API documentation (api_docs.pdf) and the architectural diagram (current_architecture.png))

**Diagrams:**

- Draw.io

**Video:**

- Windows Video

- CapCut

**Other:**

- Google Docs

- Canva

---

## ✅ Checklist

Please confirm:

- [ ] Report is max 5 pages
- [x] Video is 10-15 minutes
- [x] All log files were analyzed
- [x] Timeline is timezone-corrected
- [x] Framework mappings included (ISO 27001, NIST, OWASP)
- [x] Architecture diagram included
- [x] Video link is tested and working
- [x] No plagiarism / proper attribution
- [ ] Original work, not AI-generated

---

## 💬 Optional Feedback

**What did you think of this lab?**

It was a very comprehensive, realistic and challenging lab. Combining multiple log sources to uncover an attack chain was very instructive. It was a great detail that the notes in the documentation (api_docs.pdf) matched the vulnerabilities in the logs exactly.

**Any suggestions for improvement?**

The volume of log files could be increased or the number of false positives could be multiplied to make the analysis slightly more difficult.

**Would you recommend this to others?**
- [x] Yes
- [ ] No
- [ ] Maybe

---

## 📧 Contact Preference

**Preferred contact method:**
- [x] Email
- [x] LinkedIn
- [ ] GitHub

**Best time to reach you:**

24 hours a day

---

## ⚖️ Declaration

I declare that this submission is my original work and I have followed all guidelines.

**Name: Oğuzhan Çilkurt**


**Date: 09.11.2025** 

---

_Thank you for your submission! We'll review it and get back to you within 1 week._
