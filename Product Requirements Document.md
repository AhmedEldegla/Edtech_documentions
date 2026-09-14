# Product Requirements Document (PRD)
## Product: EduPath — EdTech & Internship Simulation Platform
### Version: 1.0.0 — Baseline: 1-Month MVP (Sprint 0 through Sprint 4)

---

## 1. Executive Summary
EduPath is an innovative B2C EdTech SaaS designed to solve the critical employability gap for fresh graduates and university students in the MENA region. While traditional learning platforms (e.g., Udemy, Coursera) offer video lectures without real team execution, and job portals merely aggregate listings, EduPath delivers a simulated, structured corporate internship environment. Learners undergo AI-driven skill gap assessment, work in Agile teams on real-world projects with sprint backlogs, and receive guidance from experienced industry mentors.

## 2. Problem Statement & Market Opportunity
### 2.1 The Problem
- **Academic-Industry Disconnect:** Universities focus heavily on theoretical knowledge without real industry workflows.
- **The Experience Catch-22:** Employers require 1-2 years of practical experience for entry-level roles, leaving fresh graduates trapped.
- **Passive Video Learning:** 90%+ drop-off rates on pure video platforms due to lack of accountability, team interaction, and authentic project feedback.
### 2.2 The Solution
EduPath transforms learners from passive consumers into agile team contributors via three tightly integrated pillars:
1. **Learning:** Target foundation skills aligned with modern market stacks.
2. **Internship Simulation:** Team-based project execution mimicking software enterprise operations (Sprints, Standups, PRs, Code Reviews).
3. **Mentoring:** High-impact, credit-based 1-on-1 and team guidance from senior tech leads.

## 3. Product Vision & Value Proposition
**Vision:** To become the primary career-launchpad for tech talent across the Arab world.
**Core Value Proposition:** Transitioning students through: Learning -> Practice -> Simulated Internship -> Mentoring -> Objective Evaluation -> Verified Career Readiness.

## 4. Target User Personas
### Persona 1: Kareem — The Fresh Computer Science Graduate
- **Background:** Graduated with basic OOP and database concepts; zero commercial project experience.
- **Goal:** Wants a verifiable portfolio with production-grade architecture to pass technical interviews.
- **Pain Point:** Rejection by recruiters citing lack of practical experience.
- **Package Fit:** 6-Month Standard or 3-Month Fast-Track.
### Persona 2: Sarah — The Career Switcher / Beginner
- **Background:** Non-technical background, learning Web Development from scratch.
- **Goal:** Comprehensive structured journey from zero to junior employability.
- **Pain Point:** Overwhelmed by fragmented tutorials; no senior code reviews.
- **Package Fit:** 12-Month Comprehensive Package (CV Optional).
### Persona 3: Tarek — The Senior Mentor
- **Background:** Staff Software Engineer at a regional tech unicorn.
- **Goal:** Monetize spare hours, give back to the community, and scout top junior talent.
- **Pain Point:** Lack of structured platforms to host and evaluate junior cohorts.

## 5. Package Matrix & Entitlements Engine
| Feature / Capability | 3-Month Package (Fast Track) | 6-Month Package (Standard) | 12-Month Package (Comprehensive) |
|---|---|---|---|
| **Target Audience** | Ready developers needing portfolio | Mid-level learners needing prep gate | Beginners starting from scratch |
| **CV Requirement** | **Mandatory** | **Mandatory** | **Optional** (Beginner toggle) |
| **AI Interview & Assessment**| Mandatory before team matching | Mandatory before team matching | Mandatory before team matching |
| **Internship Start** | Immediate post-assessment | After 4-week prep gate | After 12-week foundation learning |
| **Mentoring Credits** | Fixed session credits (TBD) | Fixed session credits (TBD) | Fixed session credits (TBD) |
| **Certificate of Completion**| On successful internship + review| On successful internship + review| On successful internship + review|
| **Career Recommendation** | TBD | TBD | Eligible on evaluation score >= 85% |
| **Mid-Cycle Package Upgrade** | Permitted (3M -> 6M/12M) | Permitted (6M -> 12M) | N/A |
| **Package Pause / Freeze** | **Disallowed in MVP** | **Disallowed in MVP** | **Disallowed in MVP** |

## 6. Feature Prioritization (MoSCoW Framework)
### Must Have (P0 — 1-Month MVP Scope)
- **Identity & Auth:** Email verification, Phone OTP, Google OAuth login.
- **Student Profile & CV:** Profile editor, CV PDF upload, asynchronous AI parsing.
- **Tracks Catalog:** Track selection (Backend, Frontend, Mobile, Data).
- **Packages & Entitlements:** Dynamic entitlement evaluation, pricing snapshot.
- **Orders & Payments:** Multi-gateway checkout (Paymob, Fawry, Stripe), Webhook activation engine.
- **AI Assessment Engine:** Dynamic technical assessment, skill gap discovery, Level placement (Beginner/Intermediate/Advanced).
- **Internship Simulation Core:** Team assignment, Project template provisioning, Sprint Kanban boards, Task submissions, Mentor reviews.
- **Mentoring System:** Slot scheduling, Credit-based bookings, Session reports.
- **Real-Time Communication:** SignalR team chat and mentor direct messaging.
### Should Have (P1 — Phase 2)
- Standalone additional mentoring session marketplace.
- Automated plagiarism & AI-generated code detection on task submissions.
- Advanced employer talent discovery directory.
### Could Have (P2 — Phase 3)
- Autonomous 24/7 AI Code Mentor agent.
- Native Mobile Applications (iOS / Android).

## 7. User Stories (By Functional Epic)
### Epic 1: Onboarding & Identity
- **US-01:** As a student, I want to sign up with email and phone so that my account credentials are secure.
- **US-02:** As a student, I want to verify my phone number via an SMS OTP so that my identity is authenticated.
- **US-03:** As a student, I want to sign in with Google so that I can access the platform with one click.
- **US-04:** As a student, I want to upload my CV in PDF format so that the system automatically extracts my skills.
- **US-05:** As a beginner, I want to toggle I am a beginner so that I am not blocked by mandatory CV upload.
### Epic 2: Tracks & Checkout
- **US-06:** As a student, I want to browse tracks and view their skill matrices so that I can choose the right career path.
- **US-07:** As a student, I want to pay using local Egyptian payment channels (Paymob wallets/cards or Fawry) so that checkout is frictionless.
- **US-08:** As an international student, I want to pay with credit card via Stripe in USD so that I can join from abroad.
- **US-09:** As a student, I want my enrollment to activate immediately upon payment confirmation without manual intervention.
### Epic 3: AI Assessment & Team Formation
- **US-10:** As a student, I want an interactive AI interview tailored to my track so that my real competency level is measured.
- **US-11:** As a student, I want a detailed skill-gap breakdown so that I know exactly what competencies I must develop.
- **US-12:** As a student, I want to be assigned to a collaborative team of peers with complementary skills.
### Epic 4: Internship Simulation & Tasks
- **US-13:** As an intern, I want to view our team project backlog and sprint goals so that I know what to build.
- **US-14:** As an intern, I want to claim tasks and update status from InProgress to InReview so that the team tracks progress.
- **US-15:** As an intern, I want to submit GitHub Pull Request links against tasks so that my code is reviewed by a mentor.
- **US-16:** As a mentor, I want to approve or reject submissions with inline feedback so that students learn professional standards.
### Epic 5: Mentoring & Collaboration
- **US-17:** As an intern, I want to view mentor availability slots and book a session using my package credits.
- **US-18:** As an intern, I want to chat in real-time with my team and mentor using SignalR channels.
- **US-19:** As an intern, I want to earn a cryptographically verifiable QR-coded certificate upon passing final sprint evaluations.

## 8. Success Metrics & Key Performance Indicators (KPIs)
| KPI Category | Metric Definition | Target Milestone (Post-Launch) |
|---|---|---|
| **Acquisition** | Visitor-to-Registration Conversion Rate | >= 18% |
| **Revenue** | Checkout Initiated to Payment Success Rate | >= 72% |
| **Engagement** | AI Assessment Completion Rate (within 48h of payment) | >= 85% |
| **Internship Quality** | Sprint Task Submission Completion Rate | >= 80% |
| **Mentoring** | Mentor Rating Average (out of 5.0) | >= 4.7 / 5.0 |
| **Satisfaction** | Net Promoter Score (NPS) among completing interns | >= +55 |

## 9. Risks and Mitigation Strategies
- **Risk: Payment Webhook Latency / Drops:** Mitigation: Robust idempotency tables, transaction hash verification, and scheduled reconciliation jobs.
- **Risk: AI Vendor Outage / Rate-Limiting:** Mitigation: Provider-agnostic abstraction (IAIService) with automatic exponential backoff and fallback queueing.
- **Risk: Team Inactivity / Dropouts:** Mitigation: Automated inactivity health checks, mentor alerts, and team rebalancing mechanisms.