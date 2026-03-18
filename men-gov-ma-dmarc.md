# DMARC Misconfiguration in men.gov.ma

**Author:** 0xIceberg
**Date:** March 2026
**Type:** Passive Reconnaissance
**Severity:** Medium ⚠️
**Target:** Moroccan Ministry of National Education

---

## Introduction

DMARC (Domain-based Message Authentication,
Reporting and Conformance) is an email
security protocol that prevents attackers
from sending fake emails using a
legitimate domain name.

When DMARC is set to "none", there is
zero protection against email spoofing.
Anyone can send emails pretending to be
from that domain.

---

## Discovery

Using only passive reconnaissance via
builtwith.com (no active testing), I found:

**DMARC Policy: None**

This means:
- No emails are rejected
- No emails are quarantined
- Zero protection against spoofing

---

## Technology Stack

| Technology | Details |
|---|---|
| CMS | Microsoft SharePoint (96 pages) |
| LMS | Moodle (2 pages) |
| Framework | CodeIgniter |
| Email | Microsoft Exchange Online |
| DMARC | p=none |
| IP (Current) | 196.200.143.116 |

---

## Impact

With DMARC = none, an attacker can:

1. Send phishing emails from @men.gov.ma
2. Steal credentials of millions of students
3. Impersonate ministry officials
4. Target teachers and administrators

This affects millions of Moroccan students
using the Moutamadris platform.

### Attack Scenario

Attacker sends email:
- From: admin@men.gov.ma
- Subject: Your Moutamadris password expired
- Body: Click here to reset your password
- Result: Student enters credentials on fake page
- Account compromised

---

## Verification

Anyone can verify this publicly:

dig TXT _dmarc.men.gov.ma

No systems were accessed or tested.
Finding based entirely on public data.

---

## Recommendation

Update DMARC policy immediately:

v=DMARC1; p=reject; rua=mailto:dmarc@men.gov.ma

This will:
- Block all spoofed emails
- Protect millions of students
- Secure the ministry reputation

---

## Disclosure Timeline

| Date | Action |
|---|---|
| March 2026 | Discovered via builtwith.com |
| March 2026 | Public writeup published |

---

## Conclusion

A simple misconfiguration like DMARC=None
can expose millions of users to phishing.

Government organizations serving students
must prioritize basic email security.

---

## References

- https://dmarc.org
- https://builtwith.com
- https://mxtoolbox.com/dmarc.aspx

---

All findings based on passive reconnaissance.
No systems were accessed or tested.

0xIceberg | Security Researcher | 2026
