#  Case Study 1: AI-Powered Diagnostic Assistant for Rural India
### AI Product Management Case Study | HealthTech | New Product Design

> **Domain:** HealthTech | AI Diagnostics | Bharat (Tier-2/3 Markets)
> **Role Simulated:** AI Product Manager
> **Type:** New Product Concept

---

##  STAR Summary 
 **S — Situation**  600M+ Indians in Tier-2/3 cities have <1 specialist doctor per 10,000 people. Patients travel 3–6 hours for basic diagnostics. 70% of diseases are detected late due to access barriers. |
 **T — Task**  Design an AI-powered diagnostic assistant that enables community health workers (ASHAs) to conduct preliminary screenings without specialist presence. |
 **A — Action**  Conducted user research across 3 personas, wrote full PRD, defined AI model requirements, designed offline-first architecture, built product roadmap with GTM via government health schemes. |
 **R — Result**  Product concept validated against real India market data. Projected to reduce diagnostic wait time from 6 hours to 20 minutes. TAM: ₹12,000 Cr rural health diagnostics market growing at 18% YoY. 

##  Problem Statement

India has **one of the worst doctor-to-patient ratios** in the world for rural areas.

- 1 doctor per 11,000 rural patients (WHO recommends 1:1,000)
- Average rural patient travels **47 km** to reach a diagnostic center
- **52% of rural disease burden** is from conditions detectable with basic screening (diabetes, TB, anaemia, hypertension)
- Community health workers (ASHAs) are present in every village but have **no diagnostic tools** — only paper registers

**Core Insight:** The problem isn't lack of medical knowledge in rural India. It's lack of **accessible, AI-assisted screening tools** in the hands of already-present health workers.

**How Might We:** *How might we give ASHA workers an AI co-pilot that helps them screen, flag, and refer patients accurately — without needing a doctor present?*


##  User Personas

| Persona | Profile | Goals | Pain Points |
 **Savitri, 34 — ASHA Worker**  Govt health worker, semi-literate, uses basic Android phone | Screen her 200-family village, report correctly | No tools, paper forms, can't diagnose, fears making errors 
 
 **Ramesh, 58 — Rural Patient**  Farmer, Maharashtra, diabetic but undiagnosed | Know if he needs to see a doctor | Can't afford travel + day off work for every symptom 
 
 **Dr. Anjali, 31 — District Doctor**  PHC doctor handling 300+ patients/day | Focus on complex cases, reduce trivial consults | Overwhelmed with basic cases that could be screened elsewhere |
 
 **State Health Official**  NHM/Ayushman Bharat program officer | Improve health outcomes, reduce hospitalizations | No real-time data from grassroots, poor visibility 



##  Solution: "NivaaranAI" — AI Diagnostic Co-Pilot for ASHA Workers

### Product Vision
> *"Give every ASHA worker an AI co-pilot that screens, flags risk, and connects rural patients to care — in their local language, without internet."*

### Core Features (V1 Scope)

| Feature | Description | AI Component |

 **Symptom Checker**  Voice-input symptom collection in Hindi/Marathi/Telugu | NLP + local language model |
 **Risk Scorer**  Flags high-risk patients for immediate referral | Trained classification model (diabetes, TB, anaemia, BP) |
  **Photo Diagnostics**  Photograph tongue/eye/skin → AI reads anaemia, jaundice signs | Computer Vision (MobileNet-based, lightweight) |
  **Offline Mode**  Full functionality without internet (sync when connected) | On-device inference (TFLite) |
  **Referral Generator**  Auto-generates doctor referral letter with patient history | Template + LLM summary |
 **Dashboard for PHC**  District doctor sees real-time village health map | Analytics layer |

### Why Offline-First Architecture?
Rural India has **only 27% consistent 4G coverage.**
On-device AI (TensorFlow Lite) ensures the tool works in zero-connectivity villages.
Data syncs to cloud when ASHA visits a town — maintaining continuity without requiring internet.


## Product Requirements Document (PRD) — Summary

**Product Name:** NivaaranAI
**Version:** 1.0
**PM:** Vivek Bakade
**Target Launch:** Q3 2025 (Pilot — 50 villages, Maharashtra)

### Goals
- Enable ASHA workers to screen for 5 common conditions without specialist
- Reduce patient referral-to-diagnosis time from 6 hrs to <30 min
- Achieve >85% screening accuracy (validated against doctor diagnosis)

### Non-Goals (V1)
- Does not replace doctor diagnosis — it is a screening and referral tool only
- Does not handle emergencies or complex multi-morbidity cases
- No telemedicine (V2 feature)

### User Stories
```
As an ASHA worker, I want to record patient symptoms by speaking in Hindi
so that I don't need to type or be literate in English.

As an ASHA worker, I want the app to tell me if a patient needs urgent referral
so that I can act quickly without waiting for a doctor's call.

As a district doctor, I want to see which villages have high-risk patients flagged
so that I can prioritize my field visits efficiently.

As a state health official, I want monthly reports auto-generated from ASHA data
so that I can submit NHM compliance reports without manual data entry.
```

### Technical Requirements
- Android app, works on ₹5,000 phones (low RAM)
- Offline-first: TFLite models, local SQLite DB
- Supports: Hindi, Marathi, Telugu, Tamil (Phase 1)
- Model size: <25MB (fits on low-storage devices)
- Sync: Background sync every 24 hrs when connected

---

##  Success Metrics & KPIs

| Metric | Baseline | Target (6-month pilot) | How to Measure |
  **Screening Accuracy**  N/A (manual = ~60%) | >85% | Compare AI flag vs doctor diagnosis (gold standard) |
  **Time-to-Referral**  6 hours avg | <30 minutes | Session timestamp data |
  **ASHA Adoption Rate**  N/A | >70% weekly active ASHAs | DAU/MAU in pilot villages |
  **Patient Referral Completion**  ~30% (most don't follow through) | >60% | Track referral → PHC visit |
  **False Negative Rate**  — | <8% | Critical safety metric — missing high-risk patients |
  **Cost per Screening**  ₹800 (travel + doctor time) | <₹50 | Total cost / screenings done |

**North Star Metric:** *Number of high-risk patients detected and successfully referred per month*

---

##  Product Roadmap

```
Q1 2025 — Foundation
├── Core symptom checker (text input)
├── 3 condition risk models (diabetes, anaemia, hypertension)
├── Hindi language support
└── Offline mode

Q2 2025 — Pilot Launch
├── Voice input in Hindi + Marathi
├── Photo diagnostics (anaemia via eye/tongue)
├── PHC doctor dashboard
├── 50-village Maharashtra pilot
└── A/B test: AI referral vs manual referral accuracy

Q3 2025 — Expand
├── TB screening module (cough audio analysis)
├── 3 more languages (Telugu, Tamil, Bengali)
├── Ayushman Bharat ID integration
└── 500-village expansion

Q4 2025 — Scale
├── API for state NHM systems
├── Auto-report generation for government compliance
├── Telemedicine video consult integration
└── National rollout pitch to Ministry of Health
```

---

##  Risks & Mitigation

| Risk | Severity | Mitigation Strategy |

| **AI misdiagnosis → patient harm** |  Critical | Position as "screening only" — always refer, never diagnose. Human-in-loop mandatory for high-risk flags. |
| **ASHA worker not adopting the app** |  High | Co-design with ASHAs. Voice-first UI. Incentive: govt recognition for high screening counts. |
| **Low-end phone compatibility** |  High | Test on ₹4,000–6,000 devices. TFLite optimization. Minimum 1GB RAM. |
| **Data privacy (patient health data)** |  Critical | DPDP Act compliance. No PII on cloud without consent. Anonymized model training. |
| **Government approval delays** |  Medium | Partner with NHM from day one. Frame as tool for ASHAs, not replacement of doctors. |
| **Bias in AI model (urban training data)** |  High | Train exclusively on rural Indian patient datasets. Partner with rural PHCs for data. |


##  Business Model & Go-To-Market

### GTM Strategy
**Not direct-to-consumer. B2G (Business to Government) model.**

1. **Pilot via NHM (National Health Mission):** Free pilot in 50 villages → generate outcome data
2. **State Government Contract:** Pitch outcome data to state health ministry → annual licensing per district
3. **Ayushman Bharat Integration:** Connect to India's largest health insurance scheme → automatic patient ID verification

### Revenue Model
| Stream | Description | Unit Economics |

| **State Licensing** | Annual per-district subscription | ₹5L/district/year × 700 districts = ₹350 Cr potential |
| **API Access** | Diagnostic API for hospital chains | ₹2 per API call |
| **Impact Reports** | NGO/CSR partnerships for data insights | Project-based |

### Market Sizing
- **TAM:** India rural healthcare market — ₹1.2 Lakh Crore
- **SAM:** AI diagnostics + screening tools — ₹12,000 Crore
- **SOM:** ASHA-deployed tools, Year 1-3 — ₹200 Crore (50,000 ASHAs × ₹40K/year licensing)

---

##  Key PM Learnings

1. **Offline-first is not optional for Bharat products** — it is the product
2. **Regulatory framing matters more than features** — calling it "screening" not "diagnosis" unlocks govt adoption
3. **ASHA workers are the real users, not patients** — designing for a semi-literate intermediary required completely different UX thinking
4. **False negatives kill trust** — in safety-critical AI, recall matters more than precision
5. **B2G GTM is slow but defensible** — once in NHM, switching costs are enormous




*This is an independent product concept created for portfolio purposes. Not affiliated with any government scheme or company.*
