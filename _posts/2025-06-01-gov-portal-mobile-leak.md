# Leaking Mobile Numbers via Base64 on Government Portal

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
   `/SendOTP****`
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

The vulnerability was reported through the official CERT-In responsible disclosure channel. It has since been fixed by the concerned organization.

---

> **Note:** I’m intentionally withholding the app name due to responsible disclosure. The goal is to educate and raise awareness, not to expose.


