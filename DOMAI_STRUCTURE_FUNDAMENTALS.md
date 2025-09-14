# Journey of Life (JOL) - EU Marketplace Platform

> A trusted, AI-powered B2B/B2C marketplace dedicated to the end-of-life industry, serving with respect and technological excellence.

**Initial MVP Domains:**
*   🇱🇹 Lithuania: [gyvenimo-kelias.lt](https://gyvenimo-kelias.lt) (Life's Journey)
*   🇱🇻 Latvia: [dzives-cels.lv](https://dzives-cels.lv) (Path of Life)
*   🇪🇪 Estonia: [elu-tee.ee](https://elu-tee.ee) (Path of Life)

---

## 📖 Table of Contents
1.  [Vision & Mission](#-vision--mission)
2.  [MVP Scope & Target Audience](#-mvp-scope--target-audience)
3.  [Core Technical Architecture](#-core-technical-architecture)
4.  [Compliance & Security First](#-compliance--security-first)
5.  [AI Integration Strategy](#-ai-integration-strategy)
6.  [Monetization Model](#-monetization-model)
7.  [Repository Structure & Contribution Guidelines](#-repository-structure--contribution-guidelines)
8.  [Roadmap: From Baltics to the EU](#-roadmap-from-baltics-to-the-eu)
9.  [FAQ](#-faq)
10. [Getting Started (For Developers)](#-getting-started-for-developers)

---

## 🎯 Vision & Mission

**Our Vision:** To become the unifying digital platform for Europe's end-of-life industry, fostering connection, dignity, and support during life's most meaningful transitions.

**Our Mission:** To leverage cutting-edge AI and robust, compliant engineering to eliminate fragmentation and language barriers. We provide churches, funeral homes, cemeteries, and individuals with a seamless, secure, and respectful marketplace to find the equipment, services, and products they need.

---

## 🧰 MVP Scope & Target Audience

Our initial focus is a validated learning launch in the Baltic states.

*   **Geographic Scope:** Lithuania, Latvia, Estonia.
*   **Product Categories:** Physical goods across all three verticals.
    *   **Church Equipment:** Vestments, candles, communionware, icons, furniture.
    *   **Funeral Home Supplies:** Caskets, urns, memorial books, hearses.
    *   **Cemetery & Monument:** Headstones, monuments, cleaning equipment, floral arrangements.
*   **Target Users:**
    *   **B2B Buyers/Sellers:** Churches, Funeral Homes, Cemetery Maintenance Companies.
    *   **B2C/SMB Buyers/Sellers:** Individual artisans, small workshops, families.

---

## 🛠 Core Technical Architecture

Our stack is chosen for scalability, maintainability, and performance.

| Layer | Technology | Justification |
| :--- | :--- | :--- |
| **Frontend** | Next.js (React) | SSR, excellent SEO, great developer experience. |
| **Backend API** | Django REST Framework (Python) | Rapid development, built-in security, ORM, and i18n support. |
| **Database** | PostgreSQL (+ PostGIS, pgvector) | Reliability, complex queries, geospatial search, AI vector embeddings. |
| **Cache** | Redis | High-performance session storage and caching. |
| **Orchestration** | Kubernetes (GKE) | Auto-scaling, self-healing, container management. |
| **Hybrid Infrastructure** | **70% Own Ubuntu Servers** (DB, Vault) & **30% Google GKE** (App Logic, AI) | Optimal balance of cost control and scalable compute. |
| **Payment Gateway** | Stripe | PCI-DSS Level 1 compliance, handles VAT MOSS & SEPA Instant. |
| **Logistics** | DPD API | Strong Baltic coverage, reliable tracking API. |

---

## 🔒 Compliance & Security First

We are building a platform of trust. Our architecture is designed to be **GDPR-compliant by design, not by add-on**.

*   **Data Protection:** All PII is encrypted at rest. Data minimization principles are core to our data models.
*   **Privacy by Design:** User data erasure requests are automated and comprehensive.
*   **Financial Security:** We are **PCI-DSS compliant via Stripe**. No raw payment data ever touches our servers.
*   **Infrastructure Security:** Private database servers are not publicly accessible. All internal communication is secured via VPN. Mandatory 2FA (TOTP) for all user and admin accounts.

---

## 🤖 AI Integration Strategy

AI is not a gimmick; it is a utility to serve our users.

1.  **MVP Priority 1: Multilingual Support Chatbot**
    *   **Purpose:** To provide instant, respectful guidance and build trust. It will answer FAQs, guide users through listing an item, and explain platform policies in their native language.
2.  **MVP Priority 2: Semantic Product Search**
    *   **Purpose:** To allow natural language search ("small oak urn for ashes" or "gold embroidered priest robe") using vector embeddings (`pgvector`).
3.  **MVP Priority 3: Real-time Translation of Listings**
    *   **Purpose:** To break language barriers. A listing posted in Lithuanian will be discoverable and readable by a user in Estonia via automated translation.

---

## 💰 Monetization Model

Sustainable and fair.

*   **Listings:** The first **10 listings per user per month are free**. This encourages adoption and small-scale participation.
*   **Premium Listings:** Each additional listing costs **€1**.
*   **Transaction Fee:** A **1% fee (minimum €1)** is applied to the total sale price for every successful transaction processed through the platform's secure payment system.

---

## 📁 Repository Structure & Contribution Guidelines


**We welcome contributions!** Please read our `CONTRIBUTING.md` guide before submitting a pull request. All code must pass linting and tests.

---

## 🗺 Roadmap: From Baltics to the EU

1.  **Phase 1 (Now):** MVP Launch in Baltics. Validate core functionality, AI features, and unit economics.
2.  **Phase 2 (Q4 2025):** Expand to Poland, Germany, and France. Integrate local payment methods and postal carriers.
3.  **Phase 3 (2026):** Pan-EU rollout to all 27 member states. Introduction of service listings (e.g., funeral planning, monument engraving).

---

## ❓ FAQ

**Q: Why start in the Baltics?**
**A:** It's a strategically perfect test market: three distinct EU countries with different languages, a manageable scale for testing, and a simplified initial GDPR compliance scope.

**Q: How do you handle 27 different VAT rates?**
**A:** Our payment partner, Stripe, automatically calculates, collects, and remits VAT via the VAT MOSS scheme for all EU transactions, eliminating a massive administrative burden.

**Q: Is this platform respectful of religious sensitivities?**
**A:** Absolutely. This is our core principle. Our content guidelines, AI training data, and community policies are being developed in consultation with cultural and religious advisors to ensure a platform that serves with dignity.

**Q: Why open-source parts of the project?**
**A:** We believe in transparency, especially for a project handling sensitive data. Open-sourcing non-core components allows for community audit, builds trust, and fosters innovation. The core marketplace logic will remain proprietary.

---

## 🚀 Getting Started (For Developers)

### Prerequisites
- Python 3.11+, Node.js 18+, Docker, PostgreSQL

### Local Development Setup
1.  **Clone the repository:**
    ```bash
    git clone https://github.com/[your-org]/jol-platform.git
    cd jol-platform
    ```
2.  **Set up backend (Django):**
    ```bash
    cd backend
    python -m venv venv
    source venv/bin/activate  # On Windows: .\venv\Scripts\activate
    pip install -r requirements.txt
    python manage.py migrate
    python manage.py runserver
    ```
3.  **Set up frontend (Next.js):**
    ```bash
    cd frontend
    npm install
    npm run dev
    ```
4.  Open [http://localhost:3000](http://localhost:3000) to view the application.

*For detailed setup instructions, including environment variables and database configuration, please see our detailed [SETUP.md](docs/SETUP.md) guide.*

---

## 🙏 Acknowledgments

We are grateful for the support of the open-source community and the advisors from various faith communities guiding this project's development.

**© 2025 Journey of Life (JOL).** This project is licensed under the terms of the proprietary JOL license for the core platform, with specific components available under MIT license. See `LICENSE` for details.
