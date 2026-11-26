# Aidar Khabibullin

**Senior Full Stack Engineer (Go + React)** with 10+ years building SaaS products in cybersecurity, fintech and e-commerce — from React interfaces to Go microservices and cloud infrastructure.

`Go` · `React` · `TypeScript` · `Next.js (App Router, SSR/RSC)` · `Apache Kafka` · `PostgreSQL` · `Redis` · `gRPC` · `WebSockets` · `Kubernetes` · `AWS` · `Turborepo`

[![Telegram](https://img.shields.io/badge/Telegram-26A5E4?style=flat-square&logo=telegram&logoColor=white)](https://t.me/aidar_work)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/aidar-khabibullin)
[![Email](https://img.shields.io/badge/Email-0078D4?style=flat-square&logo=microsoftoutlook&logoColor=white)](mailto:aidar.khabibullin@outlook.com)
[![Location](https://img.shields.io/badge/Istanbul%2C%20Turkey-gray?style=flat-square&logo=googlemaps&logoColor=white)](#)

---

## About

Senior Full Stack Engineer and Tech Lead with a backend core: Go microservices, Kafka, PostgreSQL and Redis, built around event-driven architecture and reliable delivery (idempotent consumers, retries, DLQ). On top of that I ship the React, TypeScript and Next.js interfaces, so I can take a feature from the database to the screen.

At ShelterZoom, an enterprise cybersecurity SaaS for document control and e-signatures, I built Go microservices for document processing, notifications, audit and access control, Stripe billing, real-time collaboration, and the CI/CD for 12 services on AWS EKS. I led the full-stack team there as Tech Lead, growing it from 2 to 5 engineers.

I own what I ship in production. In design reviews my first question is which invariant must never break, and what protects it during a failover.

I hold a Master's in Information Security. Based in Istanbul, working in English and Russian.

**Open to:** remote Senior Full Stack / Senior Software Engineer and Tech Lead roles, or hybrid in Istanbul.

---

## Highlights

- 📨 **−50% failed jobs** — 4 Go microservices on Kafka and PostgreSQL with idempotent consumers and a DLQ.
- 💳 **−35% failed transactions** — Stripe payments and subscriptions on Go services with idempotent webhook processing and subscription reconciliation.
- 🚀 **Deployment time from 2 hours to 20 minutes** — CI/CD for 12 Go microservices and all frontend apps on AWS EKS.
- ⚡ **−65% p95 sync latency** in real-time document collaboration (WebSockets, Redis Pub/Sub, optimistic UI on Kubernetes); concurrent editors grew from 5 to 20+.
- 🏗️ **Turborepo monorepo migration** — desktop and mobile apps plus Gmail and Outlook add-ins from one codebase, 1.5× faster delivery.
- 👥 **Team from 2 to 5 engineers** as Tech Lead, with 40% shorter onboarding.

---

## Architecture & Reliability

How I approach backend design: first decide which invariants must never break, then pick the mechanism that protects them.

- **At-least-once delivery, exactly-once effects.** Kafka consumers are idempotent; failures go through retries and a dead-letter queue instead of blocking the partition or being lost.
- **Payments you can trust.** Stripe webhooks are processed idempotently, and subscription state is reconciled against the provider, so duplicates and missed events don't corrupt billing.
- **Auditability.** Signing workflows keep a tamper-evident audit trail, and access control is a separate service with its own boundary.
- **Operability.** Health checks, metrics (Prometheus/Grafana), traces and centralized logs (Kibana), with automated rollbacks in CI/CD.

### Open-source reference: [MSA_Rocket_Factory](https://github.com/aidar-khabibullin/MSA_Rocket_Factory)

My production code is private, so this public Go monorepo shows the same approach end to end: 6 microservices (`order`, `inventory`, `payment`, `iam`, `assembly`, `notification`), gRPC contracts in protobuf/OpenAPI, Kafka events, PostgreSQL / MongoDB / Redis, Envoy as the single entry point (REST/JSON → gRPC), OpenTelemetry tracing with Jaeger, Prometheus and Grafana, and a React + TypeScript frontend.

```mermaid
flowchart LR
    Browser([Browser]) -->|REST/JSON| Envoy

    Envoy -->|gRPC| IAM
    Envoy -->|gRPC| Inventory
    Envoy -->|HTTP| Order

    Order -->|gRPC| Inventory
    Order -->|gRPC| Payment
    Order -->|gRPC| IAM

    Order -->|order.paid| Kafka{{Kafka}}
    Kafka -->|order.paid| Assembly
    Assembly -->|ship.assembled| Kafka
    Kafka -->|ship.assembled| Order
    Kafka -->|order.paid, ship.assembled| Notification
    Notification -->|gRPC| IAM
    Notification --> Telegram([Telegram])

    Order --- PG[(PostgreSQL)]
    IAM --- PG
    IAM --- Redis[(Redis)]
    Inventory --- Mongo[(MongoDB)]
```

- **Quality gates in CI:** golangci-lint, unit and integration tests (testcontainers, `-race`), coverage report, `govulncheck`, `gitleaks`, Trivy.
- **Safety by design:** health checks on every service, rate limiting and body-size limits at Envoy, brute-force protection in `iam`, JWT sessions.

---

## Selected Work

### Document Signing & Collaboration Platform · ShelterZoom
`Senior Full Stack Engineer` · `Apr 2021 – Sep 2026` · `Cybersecurity SaaS` · `51–200 employees` · `Remote, New York`

Enterprise cybersecurity SaaS: real-time document control, collaboration and e-signatures.

- Developed an end-to-end signing workflow by integrating Apryse e-signatures with Go and React: multi-party signing orchestration, signer routing and a tamper-evident audit trail for 150+ enterprise customers.
- Optimized real-time collaboration with WebSockets, Redis Pub/Sub and optimistic React UI, scaled across Kubernetes pods: p95 sync latency down ~65%, concurrent editors from 5 to 20+.
- Built and integrated 4 Go microservices on Kafka and PostgreSQL (document processing, notifications, audit, access control); failed jobs down ~50% with idempotent consumers and a DLQ.
- Led the migration to a Turborepo monorepo with shared React/TypeScript packages, shipping desktop and mobile apps plus Gmail and Outlook add-ins from one codebase; optimized CI builds and bundle sizes, speeding up delivery 1.5×.
- Automated CI/CD for 12 Go microservices and all frontend apps on AWS EKS with GitHub Actions, Docker and Helm: parallel tests, layer caching and auto-rollbacks cut deployment time from 2 hours to 20 minutes.
- Scaled a full-stack team from 2 to 5 developers as Tech Lead: code review standards, architecture docs and a buddy system reduced onboarding time by 40%.
- Integrated Stripe payments and subscription management with Go services: idempotent webhook processing and subscription reconciliation reduced failed transactions by 35%.

### Donation Payment Platform · Sberbank (SberVmeste)
`Senior Full Stack Engineer` · `Jan 2020 – Apr 2021` · `Fintech` · `51–200 employees` · `Remote, Moscow`

SberVmeste is a Sberbank charitable donation platform for daily, targeted giving.

- Developed the donation payment system from scratch (React, TypeScript, Node.js): acquiring integration, daily/monthly subscriptions and auto-closing campaigns. Processed 100K+ donations worth $1M+.
- Launched the SberVmeste web app: campaign pages with live progress, a donor account for recurring gifts and a donation calculator. First-time donors +25%.
- Developed a customizable partner portal (React, Redux) with self-service campaign management and reporting for 50+ vetted charities. Support requests −70%.

### Cloud Backup Platform · CloudAlly (now OpenText CloudAlly Backup)
`Frontend Engineer` · `Feb 2018 – Jan 2020` · `Cybersecurity / SaaS` · `11–50 employees` · `Ontario, Canada`

Backup and recovery for cloud applications.

- Developed the React UI for backup and restore workflows: scheduling, point-in-time restore and job status monitoring for Office 365, G Suite and Salesforce data of thousands of business customers.
- Delivered Backup for Salesforce onboarding (React, Salesforce API): OAuth org connection and self-service setup. Customer acquisition +32%.
- Built the MSP Partner Portal (React, REST) with a unified dashboard of accounts, trials, backups and billing, and drill-down to individual backups for 600+ MSP partners.

### Group-Buying Marketplace · Moneta (Runtime LLC)
`Frontend Engineer` · `Oct 2016 – Feb 2018` · `E-commerce` · `11–50 employees` · `Moscow`

- Redesigned catalog and group-purchase pages (React, Redux): product filters, live purchase progress and online checkout. Checkout conversion +33%.
- Optimized performance with webpack code splitting, lazy loading and image optimization: page load time and Time to Interactive −46%.
- Integrated online payments into the group-purchase checkout (React, REST): payment status tracking and order confirmation flows.

---

## 💻 Tech Stack

| **Backend** | [![Go](https://img.shields.io/badge/Go-00ADD8?style=flat-square&logo=go&logoColor=white)](https://go.dev/) [![gRPC](https://img.shields.io/badge/gRPC-244C5A?style=flat-square&logo=grpc&logoColor=white)](https://grpc.io/) [![Protobuf](https://img.shields.io/badge/Protobuf-4285F4?style=flat-square&logo=google&logoColor=white)](https://protobuf.dev/) [![REST](https://img.shields.io/badge/REST-009688?style=flat-square&logo=fastapi&logoColor=white)](#) [![WebSockets](https://img.shields.io/badge/WebSockets-010101?style=flat-square&logo=socket.io&logoColor=white)](#) [![GraphQL](https://img.shields.io/badge/GraphQL-E10098?style=flat-square&logo=graphql&logoColor=white)](https://graphql.org/) [![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=node.js&logoColor=white)](https://nodejs.org/) [![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)](https://www.python.org/) |
| :--- | :--- |
| **Frontend** | [![React](https://img.shields.io/badge/React-20232a?style=flat-square&logo=react&logoColor=%2361DAFB)](https://react.dev/) [![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=flat-square&logo=typescript&logoColor=white)](https://www.typescriptlang.org/) [![Next.js](https://img.shields.io/badge/Next.js-black?style=flat-square&logo=next.js&logoColor=white)](https://nextjs.org/) [![Redux Toolkit](https://img.shields.io/badge/Redux%20Toolkit-593D88?style=flat-square&logo=redux&logoColor=white)](https://redux-toolkit.js.org/) [![TanStack Query](https://img.shields.io/badge/TanStack%20Query-FF4154?style=flat-square&logo=react-query&logoColor=white)](https://tanstack.com/query) [![Tailwind CSS](https://img.shields.io/badge/Tailwind-38B2AC?style=flat-square&logo=tailwind-css&logoColor=white)](https://tailwindcss.com/) [![Turborepo](https://img.shields.io/badge/Turborepo-EF4444?style=flat-square&logo=turborepo&logoColor=white)](https://turbo.build/) |
| **Data & Messaging** | [![Apache Kafka](https://img.shields.io/badge/Apache%20Kafka-231F20?style=flat-square&logo=apachekafka&logoColor=white)](https://kafka.apache.org/) [![Kafka Connect](https://img.shields.io/badge/Kafka%20Connect-231F20?style=flat-square&logo=apachekafka&logoColor=white)](https://kafka.apache.org/documentation/#connect) [![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)](https://www.postgresql.org/) [![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=flat-square&logo=mongodb&logoColor=white)](https://www.mongodb.com/) [![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white)](https://redis.io/) [![Elasticsearch](https://img.shields.io/badge/Elasticsearch-005571?style=flat-square&logo=elasticsearch&logoColor=white)](https://www.elastic.co/elasticsearch) [![AWS OpenSearch](https://img.shields.io/badge/AWS%20OpenSearch-005EB8?style=flat-square&logo=opensearch&logoColor=white)](https://aws.amazon.com/opensearch-service/) |
| **Cloud & Infra** | [![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazonaws&logoColor=white)](https://aws.amazon.com/) [![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white)](https://kubernetes.io/) [![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)](https://www.docker.com/) [![GitLab CI/CD](https://img.shields.io/badge/GitLab%20CI%2FCD-FC6D26?style=flat-square&logo=gitlab&logoColor=white)](https://docs.gitlab.com/ee/ci/) [![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat-square&logo=github-actions&logoColor=white)](https://github.com/features/actions) |
| **Testing** | [![Jest](https://img.shields.io/badge/Jest-C21325?style=flat-square&logo=jest&logoColor=white)](https://jestjs.io/) [![Vitest](https://img.shields.io/badge/Vitest-729B1B?style=flat-square&logo=vitest&logoColor=white)](https://vitest.dev/) [![React Testing Library](https://img.shields.io/badge/Testing%20Library-E33332?style=flat-square&logo=testinglibrary&logoColor=white)](https://testing-library.com/) [![Playwright](https://img.shields.io/badge/Playwright-2EAD33?style=flat-square&logo=playwright&logoColor=white)](https://playwright.dev/) [![Testify](https://img.shields.io/badge/Testify-00ADD8?style=flat-square&logo=go&logoColor=white)](https://github.com/stretchr/testify) ![Load & Stress](https://img.shields.io/badge/Load%20%26%20Stress%20Testing-555555?style=flat-square) |
| **Observability** | [![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=flat-square&logo=prometheus&logoColor=white)](https://prometheus.io/) [![Grafana](https://img.shields.io/badge/Grafana-F46800?style=flat-square&logo=grafana&logoColor=white)](https://grafana.com/) [![Kibana](https://img.shields.io/badge/Kibana-005571?style=flat-square&logo=kibana&logoColor=white)](https://www.elastic.co/kibana) [![Sentry](https://img.shields.io/badge/Sentry-362D59?style=flat-square&logo=sentry&logoColor=white)](https://sentry.io/) |
| **AI** | [![Anthropic](https://img.shields.io/badge/Anthropic-CC785C?style=flat-square&logo=anthropic&logoColor=white)](https://anthropic.com/) [![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=flat-square&logo=openai&logoColor=white)](https://openai.com/) [![Claude Code](https://img.shields.io/badge/Claude%20Code-CC785C?style=flat-square&logo=claude&logoColor=white)](https://claude.com/claude-code) ![AI-assisted development](https://img.shields.io/badge/AI--assisted%20development-555555?style=flat-square) |
| **Expertise** | Microservices · Event-driven architecture · Distributed systems · System design · Idempotency & reliability patterns (retries, DLQ) · Clean architecture · Technical leadership · Mentoring |

---

## Education

**Master's degree in Information Security and Computer Technologies** — Kazan National Research Technical University named after A. N. Tupolev (KAI), 2008–2014
