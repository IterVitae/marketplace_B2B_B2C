
***

# **Project: Journey of Life (JOL) - AI-Powered Pan-European Marketplace**

> **Building a trusted digital community for the end-of-life industry, connecting faith, tradition, and modern technology across Europe.**

[![License: AGPL v3](https://img.shields.io/badge/License-AGPL_v3-blue.svg)](https://www.gnu.org/licenses/agpl-3.0)
[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)
[![Architecture: Microservices](https://img.shields.io/badge/Architecture-Microservices-ff69b4)](https://microservices.io/)
![GDPR Compliant](https://img.shields.io/badge/GDPR-Compliant-green)
![EU Focus](https://img.shields.io/badge/Focus-European%20Union-0052cc)

## 🕊️ Vision & Mission

**Vision:** To become the primary digital infrastructure for the European end-of-life industry, fostering community, ensuring dignity in transactions, and preserving cultural and religious traditions through technology.

**Mission:** To seamlessly connect suppliers of church equipment, funeral services, and cemetery maintenance products with trusted buyers across all 27 EU member states and key linguistic regions, eliminating fragmentation through AI-powered translation and discovery.

## ⚠️ The Problem: A Fragmented Market of Essential Needs

The European market for end-of-life products is vast yet deeply localized and fragmented.
*   **For Buyers** (Churches, Funeral Homes, Families): Finding specific, high-quality, and culturally appropriate items (e.g., a specific type of funeral urn, church vestments, or monument cleaning equipment) often requires inefficient, local word-of-mouth searches.
*   **For Sellers** (Artisans, Manufacturers, Distributors): Gaining visibility beyond a very small regional radius is difficult and expensive, limiting growth and the preservation of traditional craftsmanship.
*   **A Universal Barrier:** Language and cultural differences across Europe have historically prevented the formation of a single, efficient market.

## 🚀 The JOL Solution: Unity Through Technology

JOL is a B2B/B2C marketplace platform designed to unify this market with respect, precision, and technological excellence.

*   **AI-Powered Discovery:** Advanced semantic search allows users to find products using natural language (e.g., "hand-carved oak crucifix" or "biodegradable urn for ash scattering").
*   **Trust Through Community:** Verified business profiles, reviews, and a mission-driven focus create a trusted environment for sensitive transactions.
*   **No Language Barrier:** Real-time, context-aware AI translation (30 languages) makes the entire European market accessible to everyone, preserving the nuance of original listings.
*   **Dignified & Compliant:** Built from the ground up to adhere to the strictest EU data protection (GDPR) and financial regulations, ensuring user privacy and security.

## 📊 Market Opportunity

*   **Target Audience:** 400,000+ Churches, 150,000+ Funeral Homes, 120,000+ Cemetery Maintenance Companies across the EU.
*   **Monetization:** Sustainable and low-friction model:
    *   **Freemium Listings:** First 10 listings per month are free.
    *   **Premium Listings:** €1 for each additional listing.
    *   **Transaction Fee:** 1% (minimum €1) on successfully processed sales.

## 🧰 MVP Scope & Strategy (Baltic Launch)

Our Minimum Viable Product focuses on a controlled launch to validate the platform, technology, and business model.

*   **Geography:** Launch focused on Lithuania, Latvia, and Estonia.
*   **Product Categories:** Physical goods across all three verticals (Church, Funeral, Cemetery).
*   **Core Features:**
    *   User Registration & Authentication (Email/Password + 2FA)
    *   Product Listing & Management
    *   AI Semantic Search & 30-language Real-time Translation
    *   AI-Powered Multilingual Support Chatbot
    *   Integrated Payment Processing (Stripe) & DPD Logistics
    *   GDPR-compliant Data Management

## 🛠️ Technology Stack (Designed for Scale & Security)

Our architecture is built with performance, security, and future growth in mind.

| Layer | Technology | Justification |
| :--- | :--- | :--- |
| **Frontend** | Next.js, React, Tailwind CSS | Modern, performant, SEO-friendly, simple UX. |
| **Backend API** | **Django REST Framework (Python)** | Battle-tested, secure, excellent for rapid development and complex data models. |
| **Database** | **PostgreSQL** with **PostGIS** & **pgvector** | Robust, reliable, with spatial data and AI vector search capabilities. |
| **AI/LLM** | **Llama 3** (Self-hosted), Stripe-powered Translations | Cost-effective control over translation and semantic search; premium API for chatbot. |
| **Cache** | **Redis** | High-performance caching for sessions and frequent queries. |
| **Infrastructure** | **Hybrid Cloud:** **GKE** (30%) + **Ubuntu LTS** servers (70%) | Optimizes cost and performance. Stateful data on private secure servers, scalable compute on GKE. |
| **Orchestration** | **Kubernetes** | Containerized, scalable, and resilient deployment. |
| **Payment Gateway** | **Stripe** | PCI-DSS Level 1 certified. Handles SEPA, cards, and **VAT MOSS** compliance automatically. |
| **Logistics** | **DPD API** (MVP) | Strong Baltic coverage and reliable API for shipping integration. |

## 🔒 Compliance & Security: Our Non-Negotiable Foundation

*   **GDPR:** Data Protection by Design and by Default. All PII encrypted at rest. Processes for user data rights (erasure, access) are built-in. A **Data Protection Officer (DPO)** is engaged.
*   **PCI-DSS:** We are **PCI Compliant by proxy** through our Stripe integration. We never handle raw credit card data.
*   **Financial:** Stripe handles all VAT MOSS reporting and SEPA Instant payments, ensuring full financial regulatory compliance across the EU.

## 📂 Repository Structure

```
jol-platform/
├── 📁 docs/                 # Project documentation, architecture diagrams
├── 📁 infrastructure/       # Terraform/K8s manifests for GKE & on-prem
├── 📁 backend/             # Django REST API application
├── 📁 frontend/            # Next.js application
├── 📁 ai-services/         # LLM inference & translation microservices
├── 📁 docker/              # Dockerfiles for all services
└── 📁 scripts/             # Utility scripts for deployment, backup, etc.
```

## 🚀 Getting Started (Contributors)

*Prerequisites: Docker, Python 3.11, Node.js 18+*

1.  **Clone the Repository:**
    ```bash
    git clone https://github.com/[your-org]/jol-platform.git
    cd jol-platform
    ```
2.  **Set Up Environment:**
    ```bash
    cp .env.example .env
    # Edit .env with your local secrets and configuration
    ```
3.  **Run with Docker Compose (Development):**
    ```bash
    docker-compose -f docker-compose.dev.yml up --build
    ```
4.  The backend API will be available at `http://localhost:8000` and the frontend at `http://localhost:3000`.

## 👥 Contributing

We welcome contributions from developers, students, and domain experts who share our vision. Please read our [Contributing Guidelines](CONTRIBUTING.md) and [Code of Conduct](CODE_OF_CONDUCT.md) before submitting a Pull Request.

Please feel free to open an issue for feature requests, bugs, or discussions.

## 📄 License

This project is licensed under the GNU Affero General Public License v3.0 - see the [LICENSE](LICENSE) file for details. This license ensures all modifications and services based on this code remain open and benefit the community.

## 🙏 A Note on Faith & Sensitivity

This project serves an industry built on reverence, tradition, and compassion. We are committed to building a platform that reflects these values. Our technology choices are made not only for performance but for **trust, transparency, and dignity.** We invite people of all faiths and backgrounds to contribute to this mission.

---

**Disclaimer:** *This project is in active development. The MVP is targeted for the Baltic states. All specifications are subject to refinement as we learn and grow.*
