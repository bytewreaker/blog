---
title: "Leaking Mobile Numbers via Base64 on Government Portal"
date: 2025-05-30 11:00:00 +0530
categories: [Android]
tags: [government, android]
---

In a recent audit of a state-level government portal, I found a vulnerability that exposed mobile numbers linked to citizen records through a **public API response**.

---

## 🔍 Overview

The portal offers a way to check status using a public identifier. On submission, the site responds with a JSON payload containing the associated mobile number — encoded in Base64.

---

## 🧪 Steps to Reproduce

1. Visit the public government portal.
2. Use any valid public ID.
3. Submit the form and open Developer Tools → Network.
4. Look at the POST request to an endpoint like:  
   `/SendOTP******Card`
5. In the response, a base64-encoded mobile number is visible.
6. Decode using any online Base64 tool to reveal the full mobile number.

---

## ⚠️ Vulnerability Type

- CWE-200: Exposure of Sensitive Information to Unauthorized Actor  
- OWASP A01:2021 – Broken Access Control

---

## 🎯 Impact

- Anyone with a valid ID (often public or guessable) can retrieve a mobile number.
- No authentication is required.
- Potential for targeted phishing or data harvesting.

---

## ✅ Status

The issue was reported to CERT-In. While the risk is mitigated by the need for a valid ID, it still exposes sensitive data and is under review.

---

## 💡 Takeaway

**Encoding ≠ Encryption.** Never expose sensitive information like phone numbers in client-facing APIs, even in an encoded format.

---

> **Note:** I’m intentionally withholding the website name due to responsible disclosure. The goal is to educate and raise awareness, not to expose.

---

Best,  
**Bytewreaker**
