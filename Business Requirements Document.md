# Business Requirements Document (BRD)
## Project: EduPath — EdTech SaaS Platform
### Document Version: 1.0.0 — Target: 1-Month MVP (Sprint 0 through Sprint 4)

---

## 1. Executive Summary
EduPath is a direct-to-consumer (B2C) EdTech software-as-a-service designed to bridge the practical skills deficit of software engineering graduates and early-career practitioners across the MENA region. The platform replaces unassisted video consumption with real team-based internship simulations, code evaluations, and milestone-driven mentorship.

## 2. Business Context & Market Background
In Egypt and the broader Arab world, hundreds of thousands of computer science, engineering, and career-switching students graduate annually. While theoretical foundational skills exist, hiring managers routinely reject junior applicants due to an absence of commercial delivery exposure. EduPath captures this commercial market by monetizing comprehensive internship simulation cohorts with structured pricing packages.

## 3. Project Business Scope
### 3.1 In-Scope (1-Month MVP)
- Primary B2C customer journey: Student registration, CV upload, package purchase, AI-assisted interview assessment, team formation, and sprint execution.
- Payment processing supporting Egyptian regional instruments (Paymob cards & mobile wallets, Fawry cash counters) and international cards via Stripe.
- Three core package offerings: 3-Month Fast-Track, 6-Month Standard, and 12-Month Comprehensive.
- Automated student onboarding state machine strictly bound to verified server-side payment notifications.
- Simulated internship project backlogs, collaborative Kanban sprints, pull-request task reviews, and mentor evaluation reports.
- Credit-based 1-on-1 mentoring scheduling and SignalR real-time communications.

### 3.2 Out-of-Scope (Phase 2 & Beyond)
- Dedicated B2B Employer Portal with direct candidate hiring boards.
- University partnership management consoles and institutional single sign-on.
- Autonomous conversational AI coding tutor.
- Native mobile application clients (iOS / Android).

## 4. Stakeholder Matrix
| Stakeholder Group | Primary Interests & Goals | Key Responsibilities |
|---|---|---|
| **Students / Learners** | Acquire job-ready skills, complete real portfolio projects, receive guidance. | Complete profile, submit tasks, attend mentoring. |
| **Mentors** | Share industry expertise, monetize available consulting hours. | Conduct 1-on-1s, review code deliverables, submit evaluations. |
| **Platform Operations** | Maintain student cohort retention, streamline team assignments. | Manage tracks, audit anomalies, support users. |
| **Finance & Executive** | Drive unit economics, safeguard payment idempotency, lower churn. | Oversee cash settlements, gateway compliance, revenue targets. |

## 5. Core Business Rules (BR)
### 5.1 Account & Profile Rules
- **BR-001:** Every student must verify both an email address and a primary mobile telephone number before order checkout.
- **BR-002:** CV upload is mandatory for 3-Month and 6-Month package buyers. It is optional for 12-Month subscribers flagging Beginner status.
- **BR-003:** The platform prohibits manual tampering or artificial fabrication of extracted CV experiences.

### 5.2 Packages & Financial Rules
- **BR-004:** Package monetization is structured as a single one-time payment for the designated duration; recurring subscriptions are not enforced in the MVP.
- **BR-005:** Mid-term upgrades from lower-duration to higher-duration packages are permitted with prorated balance credit.
- **BR-006:** Package downgrades are prohibited in the MVP.
- **BR-007:** Freezing or pausing active enrollments is strictly disallowed in the MVP.
- **BR-008:** Enrollment activation is strictly gated on cryptographic webhook confirmation from the payment provider; client-side redirections must never activate subscriptions.
- **BR-009:** Payment handling must enforce transactional idempotency to prevent duplicate enrollment activations across retried webhooks.

### 5.3 Assessment & Level Placement Rules
- **BR-010:** Students must complete their AI interview assessment before being placed into team sprints.
- **BR-011:** AI scores serve as recommendations evaluated by backend business rules to assign one of three canonical levels: Beginner, Intermediate, or Advanced.
- **BR-012:** Administrative staff may manually override a level placement only with a documented business justification logged in the immutable AuditLog.

### 5.4 Internship Simulation Rules
- **BR-013:** 3-Month package students enter simulated internships immediately following assessment.
- **BR-014:** 6-Month package students must satisfy a 4-week preparation gate before entering team sprints.
- **BR-015:** 12-Month package students undergo a 12-week foundation curriculum before project team assignment.
- **BR-016:** Simulated internship teams must target a balanced capacity of 4 to 6 members.
- **BR-017:** Completion certificates are issued solely upon passing final project deliverables with an evaluation score >= 70%; passage of duration alone does not merit certification.

### 5.5 Mentoring Rules
- **BR-018:** Mentoring is governed by a credit entitlement model where 1 booking consumes 1 session credit.
- **BR-019:** Session cancellations require at least 24 hours notice to restore credit balance.
- **BR-020:** Mentors must submit an objective session evaluation report within 24 hours of session completion.

## 6. Business Process Flowcharts
### 6.1 End-to-End Student Commercial Journey
`mermaid
graph TD
    A[Student Visits Site] --> B[Register with Email & Phone OTP]
    B --> C[Select Career Track & Target Package]
    C --> D{Is CV Required?}
    D -->|Yes: 3M/6M| E[Upload PDF CV & Confirm Extracted Data]
    D -->|No: 12M| F[Toggle Beginner Status or Upload CV]
    E --> G[Proceed to Checkout]
    F --> G[Proceed to Checkout]
    G --> H[Pay via Paymob / Fawry / Stripe]
    H --> I[Webhook Received & Signature Verified]
    I --> J[Activate Student Enrollment]
    J --> K[AI Technical Assessment Interview]
    K --> L[Backend Assigns Level: Beg/Int/Adv]
    L --> M[Assigned to Agile Team & Project Backlog]
    M --> N[Sprint Execution & Task PR Reviews]
    N --> O[Book Mentoring Sessions with Credits]
    O --> P[Final Evaluation >= 70%]
    P --> Q[Issue Verified Certificate with QR Code]
`

## 7. Business Risks & Mitigation Matrix
| Risk Description | Probability | Impact | Mitigation Strategy |
|---|---|---|---|
| **Cash Flow Disruption (Gateway Hold)** | Low | High | Integrate three independent processors (Paymob, Fawry, Stripe) to avoid single points of failure. |
| **High Student Drop-Off in Assessment** | Medium | High | Limit initial assessment duration to 25-30 minutes with interactive, progressive questioning. |
| **Team Imbalance & Inactivity** | Medium | Medium | Implement automated activity heartbeats; empower mentors to reallocate tasks or request team rebalancing. |
| **Fraudulent Payment Chargebacks** | Low | Medium | Strict webhook HMAC verification, IP logging, and instant suspension of delinquent enrollments. |

## 8. Success Criteria & Commercial Metrics
- **Activation Velocity:** More than 80% of paid users complete assessment within 48 hours.
- **Sprint Completion:** Average team sprint completion rate above 75%.
- **Satisfaction Index:** Customer satisfaction score exceeding 85% on mentor sessions.
- **Zero Financial Discrepancies:** 100% automated reconciliation across gateway settlements and internal orders.
