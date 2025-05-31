---
title: "Authentication Bypass in Indian Government Mobile App"
date: 2025-05-30 10:00:00 +0530
categories: [Security, Mobile]
tags: [responsible-disclosure, auth-bypass, government, android]
---

While exploring a government-issued Android mobile app meant for departmental users, I discovered a severe authentication vulnerability that allowed **unauthorized access without valid credentials**.

---

## 🔍 Overview

The app's login flow allowed users to enter a mobile number and request a One-Time Password (OTP). However, it turned out that entering a **hardcoded mobile number and OTP** would grant full access—without any real verification.

---

## 🧪 Steps to Reproduce

1. Open the mobile app (latest version).
2. Select the login type.
3. Enter mobile number: `0000000000`.
4. Click “Login with OTP”.
5. Enter OTP: `123456`.
6. You are logged in successfully — no real OTP validation occurs.

---

## ⚠️ Vulnerability Type

- CWE-287: Improper Authentication  
- CWE-798: Use of Hard-coded Credentials  
- OWASP A01:2021 – Broken Access Control

---

## 🎯 Impact

- Bypasses authentication completely.
- Grants access to restricted departmental functionality.
- Poses potential for data exposure or misuse of internal features.

---

## ✅ Status

The vulnerability was reported through the official CERT-In responsible disclosure channel. It has since been fixed by the concerned organization.

---

## 💡 Takeaway

Always validate OTPs and login tokens on the **server side**. Avoid using test or placeholder credentials in production code.

---

> **Note:** I’m intentionally withholding the app name due to responsible disclosure. The goal is to educate and raise awareness, not to expose.

---

Best,  
**Bytewreaker**
