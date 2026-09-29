# Bug Bounty Reports - Ethical Hacking

## Finding #1: Insecure Client-Side Request Signing (Medium)

**Platform Type:** White-label Gaming Platform (Vue SPA + REST API)

**Vulnerability:**
API signature was MD5(JSON.stringify(sorted_params)) with no secret. Attacker can generate valid signature offline.

**Proof of Concept (Sanitized):**
- Intercepted request with Burp Suite
- Regenerated signature using JS: MD5(JSON(params))
- Server returned code 0 Succeed

**Issues Found:**
1. No HMAC / No secret key
2. Timestamp not validated (old timestamp accepted)
3. Nonce reuse possible

**Impact:**
Request forgery, replay attack

**Fix:**
Use HMAC-SHA256 with server secret, check timestamp freshness, track nonce.

---
More findings will be added as I learn.
Contact: [Your Fiverr / LinkedIn later]
