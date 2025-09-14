# Security Policy & Disclosure Program
## Project Journey of Life (JOL)

### 🛡️ Our Commitment to Security
At Journey of Life (JOL), we recognize the profound trust our users place in us to handle sensitive matters with the utmost care and security. Our security practices are built on the principles of **prevention, integrity, and transparency**. We are committed to protecting the data and privacy of our community—churches, funeral directors, cemetery operators, and families across Europe.

### 📋 Supported Versions
We provide security updates for the following versions of our platform:

| Version | Supported          |
| ------- | ------------------ |
| Latest Stable Release | ✅ |
| Previous Major Release | ✅ for 6 months |
| Other Versions        | ❌ |

### 🚨 Reporting a Vulnerability

**We consider security vulnerabilities with the highest seriousness.**

If you believe you have found a security vulnerability in our platform, please **report it responsibly**. Do not disclose it publicly until we have had sufficient time to investigate and address the issue.

**Please report vulnerabilities via email to our dedicated security team:**
**security@journey-of-life.eu**

#### What to Include in Your Report:
To help us understand and triage the issue, please include:
-   The type of vulnerability (e.g., SQL injection, XSS).
-   The full URL and parameters of the page where the vulnerability exists.
-   Step-by-step instructions to reproduce the issue.
-   Any proof-of-concept code or screenshots.
-   Your contact information (optional, but appreciated).

#### Our Pledge:
-   We will acknowledge your report within **2 business days**.
-   We will provide a more detailed response and timeline for a fix within **5 business days**.
-   We will notify you when the vulnerability is resolved and publicly acknowledge your contribution if you wish.

### 🔐 Our Security Practices

Our architecture is designed with a "paranoid" compliance-first approach:

-   **Data Encryption:** All user data is encrypted in transit (TLS 1.3) and at rest in our databases.
-   **Payment Security:** We are **PCI-DSS compliant** through our partner, Stripe. We never handle or store raw credit card numbers.
-   **GDPR Compliance:** Our system is built with "Data Protection by Design and by Default" principles. We have a appointed Data Protection Officer (DPO).
-   **Infrastructure Security:** Our hybrid infrastructure (Google GKE & private servers) is locked down with strict firewall rules, private networking (VPN), and mandatory multi-factor access for all internal systems.
-   **Rigorous Testing:** Our code undergoes static analysis, dependency scanning, and penetration testing by third-party experts before major releases.

### ⛪ A Note for Our Community of Faith
We believe that handling the practicalities of life's journey with dignity requires a foundation of unwavering trust. Our security policy is a core part of our ministry of service. We thank you for your trust and your help in keeping our community safe.

*Last Updated: {Current Date}*

