#  Case Study : Redesigning Zomato's AI Recommendation Engine
### AI Product Management Case Study | FoodTech | Product Teardown + Feature Design

> **Domain:** FoodTech | AI Personalization | Consumer Product
> **Role Simulated:** AI Product Manager
> **Type:** Product Teardown + Feature Redesign



##  STAR Summary *(Resume-Ready — copy this directly)*

| **S — Situation** | Zomato's recommendation feed shows generic "popular near you" results — ignoring time of day, weather, past habits, and occasion context. Users take 4+ minutes to decide, increasing drop-off. |
| **T — Task** | Identify the root cause of low recommendation relevance and design "ContextRec" — an AI context-aware personalization layer as a new product feature. |
| **A — Action** | Conducted product teardown, competitive analysis (Swiggy, Uber Eats), defined 4 user personas, wrote PRD with user stories, designed A/B test plan, and built a 3-phase roadmap. |
| **R — Result** | Proposed feature projected to improve recommendation CTR by 22%, reduce time-to-order by 35%, and increase revenue per session from ₹185 to ₹210+, based on industry personalization benchmarks. |


##  Problem Statement

Zomato serves **100M+ users** across India. Yet the recommendation feed treats a Monday office lunch and a Saturday birthday dinner as identical contexts.

**User Quote (simulated from user research):**
> *"I open Zomato and know exactly what I want — but the app shows me the same 10 restaurants every single day. I end up just reordering the last thing I had."*

### The Numbers Behind the Problem
- Average time-to-first-click on Zomato: **4.2 minutes**
- Industry benchmark for well-personalized feeds: **<2 minutes**
- Every additional minute of scrolling = **~8% higher drop-off probability**
- Personalization improvements at similar scale (Netflix, Spotify) drove **15–25% engagement uplift**

**Core PM Question:** Why is Zomato's AI not using the rich context signals it already has access to?

##  Product Teardown — Current State Analysis

### What Zomato Does Well 
- Real-time location-based restaurant fetching
- Reorder shortcut for last 3 orders
- "Trending near you" social proof signals
- Dietary filter (veg/non-veg)

### What's Broken 

| Problem | Root Cause Hypothesis | User Impact |

| Same restaurants shown at 8am and 8pm | Time signal not passed to ranking model | Dinner restaurants shown at breakfast, vice versa |
| No weather adaptation | Weather API not integrated into ranking | Hot day → no cold drinks/ice cream boost |
| No occasion awareness | Session context not captured | Solo lunch and group birthday treated identically |
| Budget not personalized | Price filter is static user-set, not ML-learned | Students see premium restaurants above budget |
| No "variety nudge" | No diversity constraint in recommendations | Users see same 5 restaurants for weeks |

### Root Cause Analysis (5 Whys)


Problem: Users scroll too long before ordering

Why 1: Recommendations aren't relevant enough
Why 2: Ranking model uses limited signals (location + popularity + rating)
Why 3: Context signals (time, weather, budget, occasion) not fed into model
Why 4: Engineering prioritized restaurant supply/logistics over personalization
Why 5: Personalization seen as "nice to have" vs core product — no dedicated AI PM owning it

Root Cause: No product owner driving a context-aware AI recommendation strategy


##  User Personas

| Persona | Ordering Pattern | Current Frustration |

| **Riya, 24 — Working Professional** | Daily office lunch, health-conscious | Sees same biryani restaurants every day, no healthy options surfaced |
| **Rahul, 32 — Family Man** | Weekend dinner for family of 4, budget ₹600 | No family meal combos shown, has to manually filter |
| **Priya, 19 — College Student** | Late-night orders, ₹100–150 budget | Premium restaurants dominate feed, frustrating to scroll past |
| **Anil, 45 — Health Conscious** | Salads and low-calorie, 3x/week | Promoted content always junk food, feels the app "doesn't know him" |

##  Proposed Feature: "ContextRec"

### One-Line Pitch
> *ContextRec is an AI recommendation layer that combines 5 real-time context signals to serve the right restaurant, to the right user, at the right moment.*

### The 5 Context Signals


┌─────────────────────────────────────────────────────┐
│              CONTEXTREC SIGNAL STACK                │
├─────────────────┬───────────────────────────────────┤
│ Signal          │ Example Usage                     │
├─────────────────┼───────────────────────────────────┤
│ 1. Time of Day  │ 8am → breakfast; 2pm → lunch;     │
│                 │ 11pm → late-night snacks          │
├─────────────────┼───────────────────────────────────┤
│ 2. Day of Week  │ Monday → quick meals;             │
│                 │ Saturday → explore new cuisine    │
├─────────────────┼───────────────────────────────────┤
│ 3. Weather      │ Rainy → soup/maggi/comfort food;  │
│                 │ Hot → cold drinks, ice cream      │
├─────────────────┼───────────────────────────────────┤
│ 4. User History │ Learns price range, cuisine       │
│                 │ preference, dietary, reorder rate │
├─────────────────┼───────────────────────────────────┤
│ 5. Session      │ Search "birthday" → occasion mode;│
│   Intent        │ Search "healthy" → diet mode      │
└─────────────────┴───────────────────────────────────┘


### How It Changes the Feed
**Before ContextRec:** User opens Zomato at 8am on a rainy Monday → sees biryani, pizza, Chinese
**After ContextRec:** Same user → sees "Rainy morning?  Warm up with these →" *[Maggi, Poha, Upma places near you]*

##  PRD Summary

**Feature Name:** ContextRec — Context-Aware AI Recommendations
**Priority:** P1
**Estimated Effort:** L (3–4 month engineering sprint)
**Dependencies:** Weather API, ML ranking model retraining, A/B test infra

### User Stories

As a user opening Zomato at breakfast time,
I want to see breakfast-appropriate restaurants first
So that I don't waste time filtering through dinner places.

As a budget-conscious student,
I want the app to learn my ₹100-150 price range
So that I don't see restaurants I can't afford at the top.

As a user on a rainy day,
I want the app to surface comfort food options
So that I discover relevant options I wouldn't have searched for.


### Acceptance Criteria
-  Time signal (6 buckets: early morning, breakfast, lunch, snack, dinner, late night) fed to ranking model
-  Weather API integrated; top 3 weather states (rain, hot, cold) influence ranking weights
-  User's historical price range learned over 30-day rolling window
-  Session query intent parsed via NLP for occasion/diet signals
-  Feed shows context label ("Perfect for a rainy evening ") on top recommendation card
-  No performance degradation: feed load time stays <1.2s

### Out of Scope (V1)
- Group ordering detection
- Festive/event calendar integration (Diwali, Eid) — V2
- Friend recommendation social signals — V3

##  Success Metrics

| Metric | Current Baseline | Target | Test Method |

| **Recommendation CTR** | ~14% | 17%+ | A/B test (4 weeks) |
| **Time-to-First-Order-Click** | 4.2 min | <2.8 min | Session analytics |
| **Reorder Rate** | 38% | 45%+ | 30-day cohort |
| **Revenue per Session** | ₹185 avg | ₹210+ | Transaction data |
| **Feed Diversity Score** | Low (same 5 restaurants) | 40% new restaurants in top 10 | Recommendation audit |
| **User Satisfaction (NPS)** | 42 | 50+ | In-app survey post-order |

### A/B Test Design
Control Group (50%): Current recommendation feed
Test Group (50%): ContextRec-powered feed

Duration: 4 weeks
Sample: 2M users (randomized, stratified by city tier)
Primary Metric: CTR on recommendation feed
Guardrail Metric: No increase in app load time
Success Threshold: CTR uplift >15%, p-value <0.05


##  Product Roadmap

### Phase 1 — Time + History (Month 1–2)
- Integrate time-of-day bucket into ranking model
- 30-day rolling price range learning per user
- Cuisine affinity score from order history
- A/B test launch with 10% traffic

### Phase 2 — Weather + Occasion (Month 3–4)
- OpenWeatherMap API integration
- Session query intent parsing (NLP)
- Context label UI component on feed cards
- Full A/B test rollout to 50% traffic

### Phase 3 — Social + Festive (Month 5–6)
- Friend order signals (opt-in)
- Festive/event calendar integration
- Group ordering occasion detection
- ContextRec API for restaurant partners (to optimize listings)


##  Risks & Mitigation

| Risk | Impact | Mitigation |

| Cold start for new users (no history) | Medium | Default to time + location signals only until 5 orders completed |
| Weather API latency slowing feed load | High | Cache weather data per city every 30 min, not real-time per request |
| Model recommends same cuisine repeatedly (filter bubble) | Medium | Add diversity constraint: max 3 of same cuisine in top 10 |
| Restaurant partners game the algorithm | High | Context signals derived from user behavior, not restaurant metadata |
| Privacy concerns about behavioral tracking | Medium | Full DPDP compliance; clear opt-out in settings |


##  Business Impact Projection

Current: 100M users × ₹185 avg revenue/session × 2 sessions/week
= ₹1,480 Cr/week

With ContextRec (+13.5% revenue per session):
= ₹1,680 Cr/week

Weekly incremental revenue: ₹200 Cr
Annual incremental revenue: ~₹10,000 Cr
Engineering investment: ~₹15 Cr (one-time)
ROI: 667x in Year 1


*(Note: Projections based on industry benchmarks from similar AI personalization rollouts at comparable scale)*



##  Key PM Learnings

1. **Root cause before solution** — the real problem wasn't "bad recommendations," it was "wrong signals in the model"
2. **A/B test design is part of the PRD** — success metrics must be defined before building, not after
3. **Guardrail metrics protect the user experience** — load time is a guardrail, CTR is a goal
4. **Context labels build user trust** — showing "why" a restaurant is recommended increases CTR by itself
5. **Competitive benchmarking sets the bar** — Uber Eats' weather integration proved the concept works

---

##  Related Links
*This is an independent product analysis created for portfolio purposes. Not affiliated with Zomato.*
