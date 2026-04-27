# 📧 Email Deliverability Checker

A lightweight, browser-based tool for checking the email security configuration of any domain. Built by Meta Eagle, this tool checks for SPF, DKIM, and DMARC records using Google's public DNS API — no backend required.

---

## 🔍 What It Does

Enter any domain name and the tool will perform a live DNS lookup to check whether the three core email authentication standards are correctly configured:

| Record | Purpose |
|--------|---------|
| **SPF** (Sender Policy Framework) | Specifies which mail servers are authorised to send email on behalf of your domain, preventing spoofing. |
| **DKIM** (DomainKeys Identified Mail) | Adds a cryptographic signature to outbound emails, verifying they haven't been tampered with in transit. |
| **DMARC** (Domain-based Message Authentication, Reporting & Conformance) | Builds on SPF and DKIM to tell receiving servers what to do with emails that fail authentication, and provides visibility via reporting. |

Each check returns a **PASS** or **FAIL** result, along with the raw record value where one is found, and a plain-English explanation of what the record does and why it matters.

An overall **email security score out of 10** is calculated based on the results:
- SPF: 3 points
- DKIM: 3 points
- DMARC: 4 points

---

## 🚀 How to Use

1. Open the HTML file in any modern browser (no installation required)
2. Enter a domain name (e.g. `example.com`)
3. Click **Check Now**
4. Review the results for SPF, DKIM, and DMARC

The tool also displays your current public IP address at the top of the page.

---

## ⚙️ How It Works

All DNS lookups are performed client-side using the [Google DNS over HTTPS API](https://developers.google.com/speed/public-dns/docs/doh/json) (`dns.google/resolve`). No data is sent to any third-party server beyond Google's public DNS resolver.

**DKIM detection** checks a range of common selectors automatically:

```
default, google, dkim, k1, s1, s2, mail, selector1, selector2
```

Both `TXT` and `CNAME` record types are checked for DKIM.

---

## 🛠️ Tech Stack

- Plain HTML, CSS, and JavaScript — no frameworks, no dependencies
- [Google DNS-over-HTTPS API](https://dns.google/resolve) for DNS resolution
- [ipify API](https://www.ipify.org/) for IP address display

---

## 📁 Files

```
├── index.html    # The complete tool (self-contained)
└── README.md     # This file
```

---

## 📌 Notes

- Originally developed in 2023
- DKIM detection relies on common selector names; custom or obscure selectors may not be detected
- Results reflect live DNS at the time of the query
- No data is stored or logged

---

## 🏢 About

Built by **Meta Eagle** — a managed IT services provider based in Birmingham, UK.  
For more information, visit [metaeagle.co.uk](https://metaeagle.co.uk)
