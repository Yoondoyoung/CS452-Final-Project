# CS452 Final Project Report — Receipt Scanner App

## Project Github Repository

**Repo Link:** [https://github.com/your-username/receipt-scanner-app](https://github.com/your-username/receipt-scanner-app)

# 🧾 Receipt Scanner App — Final Project Report

## Project Summary

The **Receipt Scanner App** allows users to scan grocery or retail receipts using OCR to extract item data, categorize purchases, and visualize spending trends. It combines expense tracking, nutritional insights, and clean visual dashboards into a single mobile experience.

---

# Architecture & Design

## System Architecture

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                              RECEIPT SCANNER                                 │
│                           System Architecture                                │
└─────────────────────────────────────────────────────────────────────────────┘

                                    ┌─────────────┐
                                    │   User      │
                                    │  (Mobile)   │
                                    └──────┬──────┘
                                           │
                                           ▼
┌──────────────────────────────────────────────────────────────────────────────┐
│                              CLIENT LAYER                                     │
│  ┌────────────────────────────────────────────────────────────────────────┐  │
│  │                     React Native / Expo App                             │  │
│  │  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐  │  │
│  │  │  Home    │  │  Camera  │  │ Calendar │  │ Reports  │  │ Settings │  │  │
│  │  │  Screen  │  │  Screen  │  │  Screen  │  │  Screen  │  │  Screen  │  │  │
│  │  └──────────┘  └──────────┘  └──────────┘  └──────────┘  └──────────┘  │  │
│  └────────────────────────────────────────────────────────────────────────┘  │
│                                      │                                        │
│  ┌────────────────────────────────────────────────────────────────────────┐  │
│  │                         Shared Components                               │  │
│  │  • AuthContext  • API Config  • Supabase Client  • Custom Hooks        │  │
│  └────────────────────────────────────────────────────────────────────────┘  │
└──────────────────────────────────────────────────────────────────────────────┘
                                           │
                          ┌────────────────┴────────────────┐
                          │                                 │
                          ▼                                 ▼
┌─────────────────────────────────────┐   ┌─────────────────────────────────────┐
│         BACKEND LAYER               │   │         BAAS LAYER                  │
│  ┌───────────────────────────────┐  │   │  ┌───────────────────────────────┐  │
│  │     Node.js Express Server    │  │   │  │         Supabase              │  │
│  │                               │  │   │  │                               │  │
│  │  • /parse-receipt             │  │   │  │  • Authentication             │  │
│  │  • /process-receipt           │  │   │  │  • PostgreSQL Database        │  │
│  │  • /save-receipt              │  │   │  │  • Storage (Images)           │  │
│  │  • /process-multiple-receipts │  │   │  │  • Row Level Security         │  │
│  │  • /health                    │  │   │  │                               │  │
│  └───────────────────────────────┘  │   │  └───────────────────────────────┘  │
│              │                      │   └─────────────────────────────────────┘
│              ▼                      │
│  ┌───────────────────────────────┐  │
│  │      Google Gemini AI         │  │
│  │   (Vision API for OCR)        │  │
│  └───────────────────────────────┘  │
└─────────────────────────────────────┘

                          │
                          ▼
┌──────────────────────────────────────────────────────────────────────────────┐
│                              DATA LAYER                                       │
│  ┌─────────────────────────────────────────────────────────────────────────┐ │
│  │                        Supabase PostgreSQL                               │ │
│  │  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐   │ │
│  │  │  users   │  │ receipts │  │  items   │  │categories│  │ budgets  │   │ │
│  │  └──────────┘  └──────────┘  └──────────┘  └──────────┘  └──────────┘   │ │
│  └─────────────────────────────────────────────────────────────────────────┘ │
│  ┌─────────────────────────────────────────────────────────────────────────┐ │
│  │                       Supabase Storage                                   │ │
│  │                    (receipt-images bucket)                               │ │
│  └─────────────────────────────────────────────────────────────────────────┘ │
└──────────────────────────────────────────────────────────────────────────────┘
```


---

## 📊 ERD (Entity Relationship Diagram)
![ERD](ERD/supabase-schema-uojsnkcipoiyvwflelav.png)

---

# Key Features

* Scan receipt images directly from a camera or photo gallery
* OCR-based text extraction using Google Vision or Gemini Flash
* Automatic classification of items into spending categories
* Authentication using Supabase (with optional Google Auth)
* Budget tracking, calendar tracking, and spending history
* Weekly & Monthly spending visualization
* Nutritional analysis for food-related purchases

---

# Technology Stack

| Layer             | Technology                           |
| ----------------- | ------------------------------------ |
| **Frontend**      | React Native + Expo                  |
| **Backend**       | Supabase (Auth, Storage, PostgreSQL) |
| **OCR / AI**      | Google Vision API or Gemini          |
| **Visualization** | Chart.js / Recharts                  |
| **Language**      | JavaScript / TypeScript              |

---

# Work Log

| Date       | What                                                             | Hours |
| ---------- | ---------------------------------------------------------------- | ----- |
| 11/04/2025 | Planned database structure and created ERD in Supabase           | 2     |
| 11/05/2025 | Wrote README and outlined goals + architecture, created Git repo | 2     |
| 11/07/2025 | Designed workflow and UI                                         | 4     |
| 11/08/2025 | Backend + OCR integration                                        | 4     |
| 11/10/2025 | Debugging                                                        | 2     |
| 11/11/2025 | Debugging                                                        | 2     |
| 11/13/2025 | Prompt Engineering                                               | 2     |
| 11/14/2025 | Analysis feature added                                           | 4     |
| 11/16/2025 | Added Categories                                                 | 2     |
| 11/18/2025 | Debugging                                                        | 2     |
| 11/19/2025 | Gallery image selection                                          | 2     |
| 11/20/2025 | Budget tracking                                                  | 1     |
| 11/21/2025 | Calendar feature                                                 | 2     |
| 11/22/2025 | Google Auth                                                      | 2     |

| **Total** |  | **33 hrs** |

---

# What I Learned

### 1. **Incremental Data Model Design Is Normal**

At first I wanted a *perfect database design*, but this project taught me that:

* real-world applications evolve as features are added
* schemas should be designed with extensibility in mind
* planning for change is more practical than aiming for perfection on day one

### 2. **AI Prompt Engineering Requires Iterations**

I manually wrote the initial prompt structures and refined them by asking successive questions. The OCR pipeline and categorization logic improved significantly as I iteratively engineered better prompts.

### 3. **Mobile App Development Requires UI/UX Thinking**

This was my **first mobile app**, and I learned that:

* performance matters (rendering large lists, charts)
* onboarding and usability matter more than raw functionality
* UX feedback loops are essential

### 4. **Supabase is a Strong Firebase Alternative**

I learned:

* Supabase makes auth and data management fast
* built-in storage + Postgres is extremely helpful
* SQL schemas offer clearer structure than a NoSQL-based approach
* working with SQL helps design better relationships between data entities

---

# AI Integration

### **Does your project integrate AI in any interesting way?**

**Yes.** OCR + AI categorization is core to the app:

* The app uses Google Vision or Gemini Flash to perform **OCR extraction**
* Extracted text is cleaned and processed using **prompt-driven classification**
* AI assists in identifying **store names, product categories, and nutritional alignment**

Example workflow:

1. Extract full receipt text via OCR
2. Feed paragraphs into an AI model for:

   * item extraction
   * price matching
   * category prediction
   * recipe recognition (if applicable)

---

# How I Used AI to Assist Development

I used AI at multiple stages:

* **Prototyping OCR pipeline logic**
* **Generating categorization prompts**
* **Testing data-cleaning rules**
* **React Native debugging questions**
* **Schema design reasoning**
* **Improving architectural decisions**
* **Designing interactions and UX**

I wrote my own rough ideas first, then used AI to:

* explore edge cases
* validate decisions
* compare alternative approaches

AI was especially useful when:

* understanding how to handle unknown receipts
* optimizing Supabase queries
* refining prompts for reliable categorization

---

# Why This Project Is Interesting To Me

This is my **first real mobile project**, and I continue to use it personally for everyday expense tracking. I care about it because it makes something useful in daily life: visualizing where my money goes, how often I buy certain foods, and whether my nutrition seems balanced.

Because I already see real value from the MVP, I hope to release it to the **App Store soon**. This motivates ongoing UX improvements, data accuracy enhancements, and performance tuning.

---

# Scaling, Performance, and Reliability

### **Failover Strategy**

* Supabase provides database replication and uptime guarantees
* Local caching can reduce dependency on live OCR calls
* Receipt data is stored locally until network connectivity resumes

### **Performance**

* Data queries are paginated and indexed
* Only deltas (new receipts) are processed instead of full history re-analysis
* Batch categorization reduces network calls

### **Concurrency**

* Each user has isolated receipt data
* Supabase row-level security ensures item-level isolation and protection

### **Authentication**

* Supabase Auth with optional Google OAuth
* JWT-based session management
* Storage buckets require authenticated access policies
