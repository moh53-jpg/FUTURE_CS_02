# 🔐 Phishing Detection & Awareness Report
### Cyber Security Task 2 — 2026
**Prepared by:** Mohamed Abdikadir Ahmed  
**Date:** June 5, 2026  
**Classification:** Internal Use / Educational

---

## 📋 Overview

This repository contains the full deliverables for **Cyber Security Task 2: Phishing Email Detection & Awareness**. The goal of this task was to analyse real-world phishing email archetypes, identify the techniques attackers use to deceive victims, and produce a practical awareness resource for employees and organisations.

Phishing accounts for over **80% of reported corporate security incidents** — not because systems are weak, but because people are the target. This project exists to change that.

---

## 📁 Repository Contents

```
📂 phishing-awareness-report/
├── 📄 README.md                          ← You are here
├── 📄 Phishing_Awareness_Report_2026.docx ← Full analysis report (Word)
├── 📄 Phishing_Awareness_Report_2026.pdf  ← PDF version
└── 📂 evidence/
    ├── sample_1_account_suspension.txt    ← Email sample: Account lure
    ├── sample_2_it_helpdesk.txt           ← Email sample: IT impersonation
    └── sample_3_prize_fraud.txt           ← Email sample: Advance-fee fraud
```

---

## 🛠️ Tools Used

### Email Header Analysis
| Tool | Purpose | Link |
|------|---------|------|
| **Google Apps Message Header Analyser** | Parse full email headers, inspect relay chains, and verify timestamps | [toolbox.googleapps.com](https://toolbox.googleapps.com/apps/messageheader/) |
| **MXToolbox Email Headers** | Analyse SPF, DKIM, and DMARC authentication results | [mxtoolbox.com](https://mxtoolbox.com/EmailHeaders.aspx) |

### URL & Domain Inspection
| Tool | Purpose | Link |
|------|---------|------|
| **VirusTotal** | Check URL and file hash reputation against 70+ security engines | [virustotal.com](https://www.virustotal.com) |
| **URLScan.io** | Safely detonate and screenshot suspicious URLs in an isolated sandbox | [urlscan.io](https://urlscan.io) |
| **PhishTank** | Cross-reference URLs against a community-maintained phishing database | [phishtank.org](https://www.phishtank.org) |

### Documentation
| Tool | Purpose |
|------|---------|
| **MS Word / docx** | Report writing, formatting, and final deliverable production |
| **PDF Export** | Client-ready, read-only report distribution |

> ⚠️ **Safety Note:** No suspicious links were opened directly at any point. All URL inspection was performed exclusively through sandboxed tools listed above.

---

## 🔍 Analysis Approach

The analysis followed a consistent **7-step methodology** applied identically to every email sample. This ensures findings are reproducible and comparable across samples.

### Step 1 — Collect Samples
Three phishing email archetypes were selected to cover the most common attack categories in corporate environments, each targeting a different psychological trigger:

| # | Attack Type | Psychological Trigger | Primary Goal |
|---|-------------|----------------------|--------------|
| 1 | Account Suspension Lure | Fear — loss of bank access | Credential theft |
| 2 | IT Helpdesk Impersonation | Authority — employer mandate | VPN credential harvest |
| 3 | Prize / Advance-Fee Fraud | Greed — unexpected windfall | Identity theft + financial fraud |

---

### Step 2 — Analyse Email Headers
Full headers were extracted and inspected for the following fields:

- **Return-Path** — does it match the From domain?
- **Reply-To** — does it differ from From (attacker intercept)?
- **Received-SPF** — FAIL / SOFTFAIL / NONE = unauthorised sender
- **DKIM-Signature** — missing or invalid = unauthenticated message
- **DMARC** — none / missing = no domain protection policy
- **Originating IP** — unexpected country or bulk-mail provider
- **X-Mailer** — PHPMailer or generic strings indicate phishing kits
- **Received Chain** — gaps or unexpected relay hops

---

### Step 3 — Inspect Sender Domains & Links
Every sender domain and embedded URL was examined for deception techniques:

| Technique | Example | Detection Method |
|-----------|---------|-----------------|
| Lookalike domain | `secure-bank-verify.net` | Compare against real domain character by character |
| Subdomain spoofing | `vpn-reset.company-itsupport247.co` | True domain = segment before first `/` |
| Typosquatting | `paypa1.com` (digit 1 not letter l) | Read every character carefully |
| Homograph attack | Unicode characters replacing Latin letters | Hover, inspect, copy-paste to a text editor |
| Free subdomain abuse | `company-login.netlify.app` | Legitimate orgs use their own domains |
| URL shortener | `bit.ly/3xK9pQr` | Expand before clicking — never click blind |

---

### Step 4 — Identify Phishing Indicators
Each email was assessed against **7 universal phishing indicators**:

1. Urgency / fear-based language (~95% frequency)
2. Suspicious / spoofed sender domain (~92%)
3. Misleading or lookalike URL (~88%)
4. Generic / non-personalised greeting (~75%)
5. Spelling / grammar anomalies (~68%)
6. Unexpected attachment (~61%)
7. Request for credentials or personal data (~55%)

---

### Step 5 — Classify Email Risk
Every email was rated on a three-tier scale:

| Level | Criteria | Action |
|-------|----------|--------|
| 🔴 **PHISHING** | 2+ confirmed indicators | Quarantine. Do not click, reply, or open attachments. Report immediately. |
| 🟠 **SUSPICIOUS** | 1–2 weak indicators | Do not click links. Verify via official phone number. |
| 🟢 **LIKELY SAFE** | No indicators detected | Routine vigilance. Verify unexpected requests separately. |

All three samples in this report were classified as **PHISHING — HIGH RISK**.

---

### Step 6 — Document Findings
Each sample was documented in a consistent format:
- Full email metadata (From, To, Subject, Auth results)
- Reproduced email body
- Step-by-step explanation of how the attack works
- Indicator table with severity ratings (CRITICAL / HIGH / MEDIUM)

---

### Step 7 — Prevention Guidelines
Findings were translated into:
- **Employee Do's & Don'ts** — practical, plain-language actions
- **5-Second Email Safety Check** — a quick five-question decision framework
- **Organisational Controls** — technical and process controls prioritised by impact (Critical / High / Medium)

---

## 📊 Key Findings Summary

- ✅ All three samples used **urgency** as the primary manipulation tactic
- ✅ **Spoofed sender domains** were present in every sample — all detectable with basic inspection
- ✅ **Blocking verification channels** ("do NOT contact IT") is one of the strongest single red flags
- ✅ **MFA** neutralises 99%+ of credential-stuffing attacks that follow a successful phish
- ✅ The most effective defence is a **trained, sceptical person** — not a firewall

---

## 📚 Reference Datasets

The following public repositories were referenced for sample validation and indicator frequency data. No content was reproduced — these are listed for transparency and further study only.

| Repository | Description |
|------------|-------------|
| [rf-peixoto/phishing_pot](https://github.com/rf-peixoto/phishing_pot) | Real phishing samples collected in the wild |
| [autinerd/phishing-mail-examples](https://github.com/autinerd/phishing-mail-examples) | Header and body samples for education |
| [sadat1971/Phishing_Email](https://github.com/sadat1971/Phishing_Email) | Labelled phishing / non-phishing dataset |
| [Phishing-Database/Phishing.Database](https://github.com/Phishing-Database/Phishing.Database) | Domain and URL phishing threat database |

---

## ⚠️ Disclaimer

This project was produced for **educational purposes** as part of Cyber Security Task 2 (2026). All email samples are representative examples used for security awareness training. No real user data, live phishing infrastructure, or illegal activity was involved. This analysis does not constitute professional cybersecurity or legal advice.

---

*Prepared by Mohamed Abdikadir Ahmed — June 2026*
