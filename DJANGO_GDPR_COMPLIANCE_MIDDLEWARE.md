
***

# **JOL GDPR-Compliant Security Middleware for Django**

![Django](https://img.shields.io/badge/Django-4.2-green) ![GDPR](https://img.shields.io/badge/GDPR-Compliant-blue) ![License](https://img.shields.io/badge/License-MIT-yellow) ![Status](https://img.shields.io/badge/Status-Production%20Ready-brightgreen)

## Overview

**Journey of Life (JOL)** is the first pan-European, AI-powered B2B/B2C marketplace dedicated to the end-of-life industry. Operating across all 27 EU member states necessitates a foundational commitment to privacy and data protection by design and by default.

This repository contains the core Django middleware that enforces **General Data Protection Regulation (GDPR)** compliance throughout the JOL platform. It is a critical component of our architecture, ensuring that every HTTP request is processed within the strictest legal and ethical frameworks from the moment it enters our system.

> **Disclaimer:** This middleware is a powerful tool for enforcing compliance logic but does not constitute legal advice. JOL has appointed a dedicated Data Protection Officer (DPO). Always consult with your DPO and legal counsel to ensure your implementation meets all regulatory requirements.

---

## Features

Our middleware suite provides a layered defense strategy for data privacy:

*   **Strict Transport Security:** Automatically enforces HTTPS across the entire platform.
*   **Privacy-Focused Headers:** Sets headers like `X-Content-Type-Options`, `X-Frame-Options`, and `Content-Security-Policy` to mitigate common attack vectors.
*   **Consent Management Gateway:** Intercepts requests to ensure valid legal basis (consent, contract) exists for processing personal data before any view logic is executed.
*   **Geolocation-Based Compliance Checks:** Automatically tailors data handling practices based on the user's inferred EU member state.
*   **Audit Logging Hook:** Seamlessly integrates with our auditing system to log access and processing events for accountability.
*   **Right to Be Forgotten Pre-Processor:** Flags requests from users who have initiated data erasure requests, ensuring their data is not processed further.

## Installation

1.  **Add to Django Settings:**
    Add the middleware to the `MIDDLEWARE` list in your `settings.py`. The order is critical for security.

    ```python
    # settings.py

    MIDDLEWARE = [
        'django.middleware.security.SecurityMiddleware',
        # ... other middleware ...
        'jol_gdpr_middleware.middleware.GDPRComplianceMiddleware',  # Add this line
        'django.middleware.locale.LocaleMiddleware',
    ]
    ```

2.  **Install Required Package (Optional Geolocation):**
    ```bash
    pip install django-ipware
    ```

3.  **Clone and Install this Repository:**
    ```bash
    git clone <your-github-repo-url>
    pip install -e ./jol_gdpr_middleware
    ```

## Configuration

Configure the middleware by adding the following variables to your Django settings. **Many of these are secrets and must be stored in environment variables, not in code.**

```python
# settings.py

# GDPR Configuration
GDPR_CONSENT_COOKIE_NAME = 'jol_consent'  # Name of the cookie storing consent tokens
GDPR_AUDIT_LOG_PATH = os.path.join(BASE_DIR, 'gdpr_audit.log')  # Path for audit logs

# Stripe Configuration for Payment Tokenization (PCI-DSS Compliance)
STRIPE_PUBLISHABLE_KEY = os.environ.get('STRIPE_PUBLISHABLE_KEY')
STRIPE_SECRET_KEY = os.environ.get('STRIPE_SECRET_KEY')
STRIPE_WEBHOOK_SECRET = os.environ.get('STRIPE_WEBHOOK_SECRET')

# External Service API Keys (for DPD, Translation, etc.)
DPD_API_USERNAME = os.environ.get('DPD_API_USERNAME')
DPD_API_PASSWORD = os.environ.get('DPD_API_PASSWORD')
DEEPL_AUTH_KEY = os.environ.get('DEEPL_AUTH_KEY')
```

## Usage

The middleware works automatically upon installation. However, to leverage its full functionality in your views, you can use the provided helper functions.

### Checking for Valid Consent

In any view processing personal data, you can check the consent status stored in the request object by the middleware.

```python
# views.py
from .models import ProductListing

def product_detail(request, product_id):
    product = get_object_object_or_404(ProductListing, id=product_id)
    
    # The middleware adds the `gdpr_consent` attribute to the request object.
    if not request.gdpr_consent.get('necessary'):
        # Log this attempt and return a permission denied error.
        return HttpResponseForbidden("Consent for necessary data processing is required.")
    
    # ... proceed with view logic ...
```

## API Reference (Middleware Methods)

### `process_request(self, request)`
*   **Purpose:** The main entry point. Checks for HTTPS, validates consent cookies, performs geolocation, and checks against the "erasure list".
*   **Triggers:** `GDPRComplianceError` if critical compliance checks fail.

### `process_response(self, request, response)`
*   **Purpose:** Sets crucial security headers on every outgoing response.
*   **Headers Set:** `Strict-Transport-Security`, `X-Content-Type-Options`, `X-Frame-Options`.

### `_get_user_country(self, request)`
*   **Purpose:** Internal method to determine the user's country code using `django-ipware` and a geolocation API (e.g., GeoIP2).
*   **Returns:** A two-character country code (e.g., 'LT', 'LV', 'EE').

## Extensibility

This middleware is designed to be extended for country-specific rules.

1.  **Create a new file:** `country_rules.py`
2.  **Define rule functions:**
    ```python
    # country_rules.py

    def specific_rule_for_lt(request):
        """Example rule: Lithuania requires specific cookie consent wording."""
        if request.user_country == 'LT':
            # Implement LT-specific logic
            pass
    ```
3.  **Import and register the rule** in the middleware's `__init__.py`.

## Contributing

We welcome contributions from the community, especially those that help address the nuanced privacy laws across different jurisdictions. Please read our `CONTRIBUTING.md` guide and ensure all code changes are thoroughly reviewed by our DPO before merging.

## License

This project is licensed under the MIT License - see the `LICENSE` file for details. This license does not override or negate the legal requirements of the GDPR.

## Support

For technical support regarding this middleware, please open an issue in this GitHub repository.

For questions regarding JOL's overarching data privacy policy or to contact our Data Protection Officer (DPO), please visit [https://journey-of-life.eu/legal/privacy](https://journey-of-life.eu/legal/privacy) or email `dpo@journey-of-life.eu`.

---

**Building a platform based on trust.**
**JOL - Honoring life's journey with dignity and security.**
