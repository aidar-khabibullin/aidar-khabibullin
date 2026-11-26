# Aidar Khabibullin

**Senior Full Stack Engineer (Go + React)** · 10+ years building SaaS products in cybersecurity, fintech and e-commerce

Istanbul, Turkey · Remote / Hybrid · English, Russian

[![Telegram](https://img.shields.io/badge/Telegram-26A5E4?style=flat-square&logo=telegram&logoColor=white)](https://t.me/aidar_work)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/aidar-khabibullin)
[![Email](https://img.shields.io/badge/Email-0078D4?style=flat-square&logo=microsoftoutlook&logoColor=white)](mailto:aidar.khabibullin@outlook.com)
[![Location](https://img.shields.io/badge/Istanbul%2C%20Turkey-gray?style=flat-square&logo=googlemaps&logoColor=white)](#)

---

## About

I build enterprise SaaS end to end: React/TypeScript/Next.js interfaces, API integrations, and production backends in Go with Kafka and PostgreSQL. I have led a full-stack team as Tech Lead and own what I ship in production.

In design reviews my first question is which invariant must never break, and what protects it during a failover.

**Open to:** remote Senior Full Stack / Senior Software Engineer and Tech Lead roles, or hybrid in Istanbul.

---

## Impact

| | |
|---|---|
| **−35%** | failed transactions after Stripe integration with idempotent webhooks and subscription reconciliation |
| **−65%** | p95 sync latency in real-time collaboration; concurrent editors grew from 5 to 20+ |
| **−50%** | failed jobs, via idempotent Kafka consumers and a DLQ |
| **2 h → 20 min** | deployment time for 12 Go microservices and all frontend apps on AWS EKS |
| **1.5×** | faster feature delivery after migrating to a Turborepo monorepo |
| **−40%** | engineer onboarding time; team grown from 2 to 5 developers |

---

## Experience

### Senior Full Stack Engineer · ShelterZoom
`Apr 2021 – Sep 2026` · New York, US (Remote) · Enterprise cybersecurity SaaS: document control, collaboration, e-signatures

- Built an end-to-end signing workflow (Apryse e-signatures, Go, React): multi-party orchestration, signer routing and a tamper-evident audit trail for 150+ enterprise customers.
- Optimized real-time collaboration with WebSockets, Redis Pub/Sub and optimistic UI across Kubernetes pods: p95 sync latency down ~65%, concurrent editors from 5 to 20+.
- Built 4 Go microservices on Kafka and PostgreSQL (document processing, notifications, audit, access control); failed jobs down ~50% with idempotent consumers and a DLQ.
- Led the migration to a Turborepo monorepo with shared React/TypeScript packages, shipping desktop and mobile apps plus Gmail and Outlook add-ins from one codebase.
- Automated CI/CD for 12 Go microservices and all frontend apps on AWS EKS (GitHub Actions, Docker, Helm) with parallel tests, layer caching and auto-rollbacks.
- Scaled the team from 2 to 5 developers as Tech Lead: code review standards, architecture docs, buddy system.
- Integrated Stripe payments and subscriptions with Go services: idempotent webhook processing and reconciliation.

### Senior Full Stack Engineer · Sberbank (SberVmeste)
`Jan 2020 – Apr 2021` · Moscow (Remote) · Fintech, charitable donation platform

- Built the donation payment system from scratch (React, TypeScript, Node.js): acquiring integration, daily/monthly subscriptions, auto-closing campaigns. 100K+ donations worth $1M+.
- Launched the SberVmeste web app with live campaign progress, a donor account for recurring gifts and a donation calculator: +25% first-time donors.
- Built a customizable partner portal (React, Redux) for 50+ charities: support requests down 70%.

### Frontend Engineer · CloudAlly (now OpenText CloudAlly Backup)
`Feb 2018 – Jan 2020` · Ontario, Canada · Cybersecurity / SaaS data protection

- Built the React UI for backup and restore: scheduling, point-in-time restore and job monitoring for Office 365, G Suite and Salesforce.
- Delivered Backup for Salesforce onboarding (OAuth org connection, self-service setup): +32% customer acquisition.
- Built the MSP Partner Portal with a unified dashboard for 600+ partners.

### Frontend Engineer · Moneta (Runtime LLC)
`Oct 2016 – Feb 2018` · Moscow · E-commerce, group-buying marketplace

- Redesigned catalog and group-purchase pages (React, Redux): +33% checkout conversion.
- Cut page load time and Time to Interactive by 46% with code splitting, lazy loading and image optimization.
- Integrated online payments with order confirmation and status tracking.

---

## Tech Stack

| | |
|---|---|
| **Backend** | Go, gRPC, Protobuf, REST, WebSockets, GraphQL, Node.js, Python |
| **Frontend** | React, TypeScript, Next.js (App Router, SSR/RSC), Redux Toolkit, TanStack Query, Tailwind CSS, Turborepo |
| **Data & Messaging** | Apache Kafka, Kafka Connect, PostgreSQL, MongoDB, Redis, Elasticsearch / AWS OpenSearch |
| **Cloud & Infra** | AWS, Kubernetes, Docker, GitLab CI/CD, GitHub Actions |
| **Testing** | Jest, Vitest, React Testing Library, Playwright, Testify, load and stress testing |
| **Observability** | Prometheus, Grafana, Kibana, Sentry |
| **AI** | AI-assisted development, LLM APIs (Anthropic, OpenAI), Claude Code |
| **Expertise** | Microservices, Event-driven architecture, Distributed systems, System design, Idempotency & reliability patterns (retries, DLQ), Clean architecture, Technical leadership, Mentoring |

---

## Education

**Master's degree in Information Security and Computer Technologies**, Kazan National Research Technical University (KAI), 2008–2014
