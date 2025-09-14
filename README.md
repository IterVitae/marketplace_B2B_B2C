# Journey of Life (JOL)

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python](https://img.shields.io/badge/Python-3.11%2B-blue)](https://www.python.org/)
[![Django](https://img.shields.io/badge/Django-4.2-brightgreen)](https://www.djangoproject.com/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15+-336791)](https://www.postgresql.org/)
[![GDPR Compliant](https://img.shields.io/badge/GDPR-Compliant-green)](https://gdpr-info.eu/)

**The first pan-European, AI-powered B2B/B2C marketplace dedicated to the end-of-life industry.**

JOL connects suppliers of church equipment, funeral services, and cemetery maintenance products with buyers across the European Union, transcending language and cultural barriers with cutting-edge technology, built on a foundation of trust and respect.

> **"A mission-driven platform, built with technical excellence."**

---

## 🌟 Vision

To create a dignified and seamless digital ecosystem for the end-of-life industry, supporting communities of faith, professionals, and individuals during times of need by providing a trusted, transparent, and technologically advanced marketplace.

---

## 🚀 MVP Scope (Phase 1)

Our initial focus is on a secure and compliant launch in the Baltic states, validating our core technology and business model.

*   **Geography:** Estonia, Latvia, Lithuania.
*   **Product Categories:** Physical goods across Church Equipment, Funeral Supplies, and Cemetery Maintenance.
*   **Users:** B2B (Churches, Funeral Homes, Services) & B2C (Artisans, Individuals).
*   **Key Features:**
    *   Multilingual Listings (30 languages, inc. RTL support for Arabic)
    *   AI-Powered Semantic Search & Multilingual Support Chatbot
    *   Secure Escrow Payment Processing with Stripe
    *   Integrated Shipping with DPD
    *   GDPR-Compliant Data Handling by Design

---

## 🛠️ Tech Stack

| Layer | Technology | Rationale |
| :--- | :--- | :--- |
| **Backend** | Django 4.2 (Python), Django REST Framework | Robust, secure, batteries-included framework for rapid development. |
| **Database** | PostgreSQL 15+ with PostGIS & pgvector | Reliability, advanced features for geospatial and AI vector search. |
| **Frontend** | Next.js 13+ (React) | High-performance, SEO-friendly, excellent developer experience. |
| **AI** | Llama 3 (Self-hosted), DeepL API | Cost-effective control over translation and NLP tasks. |
| **Infrastructure**| Hybrid: Google GKE & Private Ubuntu Servers | Optimized for cost, scalability, and security. |
| **Cache** | Redis | High-performance caching for sessions and frequently accessed data. |
| **Payments** | **Stripe** | Full PCI-DSS compliance, VAT MOSS handling, SEPA Instant. |

---

## 🗺️ High-Level Architecture

```mermaid
graph TD
    subgraph "Client Layer"
        A[Web Browser - Next.js/React App]
        B[Stripe.js Elements]
        C[AI Chatbot Widget]
    end

    subgraph "Public Cloud - Google GKE (30%)"
        D[Nginx Ingress/LB]
        subgraph "App Cluster"
            E[Django API Pods]
            F[Celery Worker Pods]
            G[LLM Inference Pods]
            H[Redis Cache]
        end
    end

    subgraph "Private Cloud - Ubuntu Servers (70%)"
        I[PostgreSQL w/ PostGIS & pgvector]
        J[Hashicorp Vault]
        K[Encrypted Backup Server]
    end

    subgraph "External Services"
        L[Stripe API]
        M[DPD API]
        N[DeepL API]
    end

    A <-->|HTTPS| D
    B <-->|HTTPS| L
    D <-->|VPN| E
    E <-->|VPN| I
    E <-->|VPN| J
    E <-->|Async| F
    E <-->|API Calls| L
    E <-->|API Calls| M
    E <-->|API Calls| N
    G <-->|Cache| H

---

## 🔒 Compliance & Security

We are built on a **Paranoid Compliance** model:
*   **GDPR:** Data encrypted at rest, automated right-to-erasure workflows, DPO appointed.
*   **PCI-DSS:** Zero sensitive payment data handled by our servers. Fully delegated to Stripe.
*   **Infrastructure:** No public ingress to databases. Secure VPN between clouds. Immutable backups.

---

## 💰 Business Model

*   **Listings:** Freemium. First 10 listings per month are free, then **€1** per listing.
*   **Transactions:** **1%** commission on sales (min. **€1**).

---

## 🧩 Getting Involved

We welcome contributions from developers, students, and domain experts who share our vision.

**Prerequisites:**
*   Python 3.11+, Node.js 18+, Docker, PostgreSQL

**Initial Setup:**
```bash
# Clone the repository
git clone https://github.com/your-org/journey-of-life.git
cd journey-of-life

# Setup backend (Django)
cd backend
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python manage.py migrate
python manage.py runserver

# Setup frontend (Next.js)
cd frontend
npm install
npm run dev
```
*For detailed development, testing, and deployment guides, please see our [Contributing Documentation](CONTRIBUTING.md).*

---

## 📫 Contact & Links

*   **Documentation:** [Full Technical Docs](docs/) | [API Reference](docs/api.md)
*   **Issue Tracker:** [GitHub Issues](https://github.com/your-org/journey-of-life/issues)
*   **Business Inquiries:** `contact@journey-of-life.eu`

---

## 🙏 Acknowledgments

This project is dedicated to the communities and professionals who serve others with dignity and respect. Built with faith in technology for the journey of life.

**License:** This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details.
```
