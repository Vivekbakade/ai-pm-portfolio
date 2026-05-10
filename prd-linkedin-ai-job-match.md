# PRD: LinkedIn AI Job Match — Redesigning Job Recommendations for Indian Freshers
### Product Management Case Study | Career Tech | Feature Redesign

> **Domain:** Career Tech | AI Personalization | India Fresher Market
> **Role Simulated:** AI Product Manager
> **Type:** Feature Redesign + PRD
> **Author:** Vivek Bakade | vivekbakade14@gmail.com | [LinkedIn](https://linkedin.com/in/vivek-bakade-a2726224b)

---

## STAR Summary *(Resume-Ready)*



| **S — Situation** | 8M+ Indian engineering freshers use LinkedIn to find jobs, but the job recommendation algorithm is built for experienced professionals — showing irrelevant senior roles, requiring 2-5 years experience, and completely ignoring India-specific career contexts like tier-2 colleges, CGPA, and skill certifications. 72% of freshers report applying to 50+ jobs with less than 5% callback rate. |

| **T — Task** | Redesign LinkedIn's job recommendation engine specifically for Indian freshers — making it context-aware, skills-first, and actionable within their actual constraints (0 experience, tier-2 college, 6-8 CGPA). |

| **A — Action** | Conducted pain point analysis, defined 3 user personas, wrote full PRD for "LinkedIn AI Job Match" — an AI layer that understands fresher context, skills signals, and India-specific hiring patterns to surface relevant internships and entry-level roles. |

| **R — Result** | Proposed feature projected to increase fresher application-to-callback rate from 5% to 18%+, reduce job search time from 4 months to 6 weeks, and increase LinkedIn DAU among Indian students by 35%. |

---

##  Problem Statement

### The Numbers Don't Lie

Students with an active LinkedIn presence report 30–50% higher interview calls — yet most Indian freshers feel LinkedIn's job recommendations are completely irrelevant to them.

- **8M+** engineering graduates in India every year
- **72%** apply to 50+ jobs with less than 5% callback rate *(user research)*
- Freshers report frustration with outdated listings and mismatched roles
- Average Indian fresher spends **4+ months** searching for first job
- LinkedIn recommendations default to **2-5 years experience** roles even for fresh graduates

### Root Cause Analysis (5 Whys)

```
Problem: Indian freshers get irrelevant job recommendations on LinkedIn

Why 1: Recommendations are based on experience level signals
Why 2: Algorithm treats "0 years experience" as incomplete profile, not as fresher
Why 3: No India-specific context — tier-2 college, CGPA, certifications not weighted
Why 4: Skills from projects, certifications, GitHub not parsed as strong signals
Why 5: LinkedIn's core algorithm is built for US/global experienced professionals —
        Indian fresher market is a completely different user segment with different needs

Root Cause: LinkedIn has no dedicated AI layer for the fresher/intern job market in India
```

### User Pain (Real Quotes from User Research)

> *"LinkedIn shows me 'Senior Product Manager — 5 years required' when I search for PM roles. I'm a final year student."* — Engineering student, Nagpur

> *"I have 4 certifications in data analytics but LinkedIn still shows me jobs I'm not qualified for. It doesn't read my certifications properly."* — B.Tech student, Pune

> *"I don't even know if my application was seen. Zero feedback, zero match score, nothing."* — MBA fresher, Tier-2 college

---

##  User Personas

| Persona | Profile | Job Search Goal | Current Pain |
|---|---|---|---|
| **Arjun, 22 — ECE Fresher, Nagpur** | B.Tech, 7.2 CGPA, 4 data analytics certs, built AI project | AI PM / Data Analyst internship | LinkedIn shows senior roles; doesn't recognise his certs and projects as experience |
| **Priya, 21 — CS Student, Tier-2 College, Pune** | Good coder, low CGPA (6.1), active GitHub, no internship | SDE internship at startup | Algorithm penalises her CGPA; GitHub projects not recognised as signals |
| **Rahul, 23 — MBA Fresher, Indore** | Tier-2 MBA, good communication, no work ex | Sales / Marketing role at startup | Recommendations irrelevant to MBA freshers; too many MNC roles requiring experience |

---

##  Proposed Solution: "LinkedIn AI Job Match"

### One-Line Pitch
> *LinkedIn AI Job Match is a context-aware recommendation layer that understands who an Indian fresher actually is — not just what their resume says — and surfaces roles they can realistically get.*

### How It's Different from Current LinkedIn

| Signal | Current LinkedIn | LinkedIn AI Job Match |
|---|---|---|
| Experience | Years of work experience | Skills + projects + certs as proxy for experience |
| College | Tier ranking affects visibility | Skill signals override college tier bias |
| CGPA | Not used | Used contextually — not as filter but as one signal |
| Certifications | Listed but not weighted | Parsed and matched to job requirements |
| Projects | Plain text, ignored | GitHub/portfolio parsed for tech stack signals |
| Location | Binary (city match) | Includes remote-first and relocation-willing signals |
| Apply status | One-click blind apply | Match score shown before applying |

---

##  Product Requirements Document (PRD)

**Product Name:** LinkedIn AI Job Match
**Feature Owner:** AI Job Recommendations Team
**PM:** Vivek Bakade
**Priority:** P1
**Target Users:** Indian college students + freshers (0-1 year experience)
**Target Launch:** Q3 2025 — Beta (India only)

---

### Goals
- Increase fresher application-to-callback rate from ~5% to 18%+
- Reduce average job search duration from 4 months to 6 weeks
- Increase LinkedIn DAU among Indian students by 35%
- Become the #1 platform for Indian fresher job discovery (beating Naukri for freshers)

### Non-Goals (V1)
- Does not replace existing job recommendation for experienced professionals
- Does not build a separate app — feature within existing LinkedIn app
- Does not handle campus placement (separate product)
- No resume builder (V2)

---

### Core Features

**1. Fresher Context Engine**
AI automatically detects fresher status from profile signals (graduation year, 0 experience, student tag) and switches to fresher-optimised recommendation mode.

**2. Skills-First Matching**
Instead of experience-years matching, the algorithm matches:
- Listed skills → job required skills
- Certifications (Google, Coursera, etc.) → role requirements
- GitHub/portfolio links → tech stack signals
- Projects described in experience section → relevant technologies

**3. India-Specific Filters**
- Internship vs full-time toggle (freshers need internships first)
- Stipend range filter (₹5,000 – ₹50,000/month)
- Work from home / hybrid / office filter
- City tier filter (Tier-1 / Tier-2 / any)
- "Freshers welcome" tag on job posts

**4. Match Score (Transparency)**
Before applying, user sees:
```
Match Score: 78%
 Skills match: Python, SQL, Data Analytics
 Role level: Entry level — matches your profile
 Missing: Tableau (mentioned in JD)
 Tip: Add your Kaggle project to improve match
```

**5. Gap Nudge**
AI identifies what's missing for top roles and nudges:
*"3 jobs you almost qualify for need Tableau. Here's a free 2-hr course."*
This drives LinkedIn Learning engagement while helping the user.

**6. Application Tracker**
Simple dashboard showing:
- Jobs applied
- Views on your application
- Status: Seen / Under review / Rejected
- Weekly application stats

---

### User Stories

```
As an Indian fresher, I want LinkedIn to show me jobs that match my skills and 
projects — not just my years of experience —
so that I can find roles I actually have a chance at.

As a student with certifications, I want my Google and Coursera certificates 
to be recognised as qualification signals —
so that I'm not penalised for having 0 work experience.

As a job seeker, I want to see my match score before applying —
so that I don't waste time on applications I have no chance at.

As a fresher, I want to know exactly what skill I'm missing for a dream role —
so that I can upskill and come back stronger.

As a tier-2 college student, I want my skills and projects to matter more 
than my college name —
so that I get a fair shot at good companies.
```

---

### Technical Architecture

```
Input Signals:
├── Profile data (skills, education, projects, certs, GitHub URL)
├── Job description (NLP-parsed requirements, experience level, skills)
├── Behavioral signals (jobs clicked, time spent, applied vs skipped)
├── India market signals (company size, startup vs MNC, stipend range)
└── Historical success data (which fresher profiles got callbacks at which companies)

AI Layer:
├── NLP parser → extracts skills from project descriptions and certs
├── Skills embedding model → semantic matching (not just keyword)
├── Collaborative filtering → "freshers like you got callbacks at these companies"
├── Gap analysis model → identifies missing skills for top roles
└── Match score calculator → weighted scoring across all signals

Output:
├── Ranked job feed (fresher-relevant roles only)
├── Match score per job
├── Missing skills nudge
└── Application tracker updates
```

---

## Success Metrics & KPIs

| Metric | Current Baseline | V1 Target | Measurement |
|---|---|---|---|
| **Application-to-Callback Rate** | ~5% | 18%+ | Survey + recruiter data |
| **Job Search Duration** | 4 months avg | 6 weeks | User survey (30-day cohort) |
| **DAU — Indian Students** | Baseline | +35% | LinkedIn Analytics |
| **Feature Adoption Rate** | N/A | >60% of fresher users | DAU on new feature |
| **Match Score Accuracy** | N/A | >75% (user rates match as relevant) | In-app feedback |
| **LinkedIn Learning CTR** | Baseline | +25% via Gap Nudge | Click tracking |
| **Fresher NPS** | ~28 (low) | 45+ | Quarterly survey |

**North Star Metric:** *% of Indian freshers who receive at least 1 interview call within 30 days of using AI Job Match*

### A/B Test Design
```
Control (50%): Current job recommendation feed
Variant (50%): AI Job Match feed with match scores + gap nudge

Duration: 6 weeks
Sample: 500,000 Indian users with graduation year 2024/2025
Primary Metric: Application-to-callback rate
Guardrail: No decrease in overall job application volume
Success: 2x improvement in callback rate, p-value < 0.05
```

---

##  Product Roadmap

### V1 — Skills-First Matching (Q3 2025)
- Fresher context detection
- Skills-based job matching
- India-specific filters (stipend, WFH, freshers welcome)
- Match score display
- Beta: India only, final-year students

### V2 — Gap Intelligence (Q4 2025)
- Gap nudge → LinkedIn Learning integration
- GitHub/portfolio parsing
- Application tracker
- Certification recognition engine
- "Freshers like you" collaborative signal

### V3 — Full Ecosystem (Q1 2026)
- Resume builder with AI suggestions
- Interview prep recommendations based on applied jobs
- Company culture signals (startup vs MNC for freshers)
- Alumni connection — "This IIT Bombay alumnus works here"
- Campus ambassador program integration

---

##  Risks & Mitigation

| Risk | Severity | Mitigation |
|---|---|---|
| Recruiters don't update job posts with "freshers welcome" tag | High | Auto-detect from JD language; infer from hiring history |
| Match score demoralises freshers with low scores | Medium | Show score only after profile is 80% complete; frame as "opportunity score" not rejection |
| Algorithm bias against tier-2 colleges persists | High | Explicitly remove college name from matching model; skill signals only |
| Freshers game the system (add irrelevant skills) | Medium | Skill endorsements + assessment scores weighted higher than self-declared skills |
| Low recruiter adoption of fresher-specific tags | Medium | Auto-tag based on JD analysis; recruiter dashboard with fresher applicant analytics |

---

##  Business Case for LinkedIn

### Why LinkedIn Should Build This

- LinkedIn has over 100 million users in India — largest professional network
- Indian fresher market: 8M+ graduates/year × growing → massive TAM
- LinkedIn's AI-driven recruitment tools now allow companies to filter candidates based on skills — infrastructure already exists
- Naukri dominates fresher market currently — this is LinkedIn's chance to win that segment
- LinkedIn Learning upsell opportunity via Gap Nudge = direct revenue impact
- Premium subscriptions: freshers who get jobs become paying professionals

### Revenue Impact Model
```
Current: 100M India users, low fresher engagement
Post AI Job Match:
- 35% DAU increase among students = ~15M more active users
- 10% convert to Premium after getting job = 1.5M new premium users
- Premium ARPU India: ~₹1,500/month
- Annual incremental revenue: ₹2,700 Crore
```

---

##  Key PM Learnings

1. **The user is not the customer** — freshers are the users, recruiters are the customers. The feature must serve both or it fails
2. **India ≠ Global** — LinkedIn's global algorithm is blind to India-specific signals (tier-2 colleges, CGPA culture, certificate-heavy resumes)
3. **Transparency builds trust** — showing match score before applying reduces frustration even when the score is low
4. **Nudge > Block** — showing "you're missing Tableau" is better than not showing the job at all
5. **North Star alignment** — "interview call within 30 days" aligns user, recruiter, and LinkedIn business goals simultaneously

---

##  Links
- [GitHub Portfolio](https://github.com/Vivekbakade)
- [Case Study: NivaaranAI — Rural Health](./case-study-1-rural-health-ai.md)
- [Case Study: Zomato ContextRec](./case-study-2-zomato-contextrec.md)
- [Case Study: SolvAI EdTech](./case-study-3-solvai-edtech.md)

---

*© Vivek Bakade | B.Tech Electronics Engineering, Nagpur | AI Product Management Portfolio | 2025*
*This is an independent product concept created for portfolio purposes. Not affiliated with LinkedIn.*
