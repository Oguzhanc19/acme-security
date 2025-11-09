## 📋 Submission Information

**Name:** Oğuzhan Çilkurt  

**Email:**  oguzhan196060@gmail.com

**LinkedIn:** [[linkedin.com/in/yourprofile] ](https://www.linkedin.com/in/oguzhan-cilkurt/) 

**Submission Date:** 09.11.2025

---

## ✅ Deliverables Checklist

Please confirm you've included all required items:

- [x] **Report** (PDF, max 5 pages)
  - [x] Section 1: Incident Analysis
  - [x] Section 2: Architecture Review
  - [x] Section 3: Response & Remediation
  
- [x] **Video Presentation** (10-15 minutes)
  - [x] Link provided in `video_link.md`
  - [x] Video is accessible (tested in incognito)
  - [x] Duration is within guidelines

- [x] **File Structure**
```
  submissions/firstname-lastname/
  ├── report.pdf
  ├── video_link.md
  └── notes.md (optional)
```

---

## 📊 Self-Assessment

**Time spent on this lab:** Approximately 12 hours

**Tools used:**
- Log analysis: From Manual Web Screen
- Diagrams: Draw.io
- Video recording: Windows Video Tool

**Confidence level:**
- [ ] Very confident in my analysis
- [x] Confident but some uncertainties
- [ ] Attempted my best with available knowledge

---

## 🎯 Brief Summary (2-3 sentences)

_Briefly describe your approach and key findings:_

My approach was to first identify the attacker's IP (203.0.113.45) by cross-referencing the security_test_schedule.pdf with the log files. I then pivoted on this IP to build a chronological attack timeline. This revealed three critical, documented-but-unmitigated vulnerabilities: BOLA, SQLi via a misconfigured WAF, and insufficient Rate Limiting.

[Write here]

---

## 🔍 Key Findings Highlight

**Main attack vectors identified:**
1. API - Broken Object Level Authorization (BOLA)
2. Web - SQL Injection (via WAF Bypass)
3. API - Insufficient Rate Limiting & Account Enumeration

**Most critical vulnerability:**

The Broken Object Level Authorization (BOLA) vulnerability. It was explicitly noted in the api_docs.pdf ("may not verify account ownership") and allowed the attacker to systematically enumerate and exfiltrate portfolio data from all other users using a single, low-privilege token.

**Top recommendation:**

Implement Centralized, Enforced Authorization at the API Gateway level. This control must validate that the user_id from the JWT token matches the account_id being requested in the API path before forwarding the request to the Trading API.

---

## 💭 Challenges & Learnings

**What was most challenging?**

Correlating the precise timestamps across multiple log files (api_logs.csv, waf_logs.csv, web_logs.csv) to build an accurate attack timeline. Also, correctly interpreting the current_architecture.png to identify the architectural disconnect between the Auth Service and Trading API was a key challenge that required careful re-evaluation.

**What did you learn?**

I learned how critical WAF configuration (DETECT vs. BLOCK mode) is; a misconfigured WAF is as bad as no WAF. I also learned that "notes" in API documentation (like "may not verify account ownership" or "rate limiting not strictly enforced") are often giant red flags pointing directly to exploitable vulnerabilities.

**What would you do differently?**

I would start by focusing more on the architectural diagram first. Understanding the fundamental flaw (the disconnect between Auth Service and Trading API) before diving deep into the logs would have made the BOLA log analysis even faster and more intuitive.

---

## 📝 Additional Notes _(optional)_

Any context, assumptions, or additional information you'd like evaluators to know:

My analysis concluded that the attacker's 1523 user account was provided as part of a "Grey Box" test. This assumption is based on the timeline, as the BOLA enumeration (starting 06:47) occurred before the Phishing attack (09:00). The jwt_token_1523_stolen name in the logs also strongly supports this test scenario.

Note: An artificial intelligence assistant was used for guidance and verification in the analysis, reporting and presentation text preparation processes.

---

## ⚖️ Declaration

I declare that:
- [x] This work is entirely my own
- [x] I have not copied from other submissions or answer keys
- [x] I have not modified the provided log files
- [x] All sources and tools are properly attributed
- [x] I understand plagiarism results in disqualification

**Signature:** Oğuzhan Çilkurt 

**Date:** 2025.11.09

---

## 🚀 Ready for Review

By submitting this PR, I confirm that my work is complete and ready for evaluation.

---

_Thank you for your submission! Our team will review it within 1 week._
