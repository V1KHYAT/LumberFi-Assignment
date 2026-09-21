# BuilderFax — Add Work Experience Mobile Web Prototype

An interactive, production-ready mobile web prototype (iOS native layout, 393×852px viewport scaled to 80vh) designed for **BuilderFax**, an identity and credential wallet for construction tradespeople.

🌐 **Live Demo (GitHub Pages)**: [https://v1khyat.github.io/LumberFi-Assignment/](https://v1khyat.github.io/LumberFi-Assignment/)

---

## 🏗️ Problem Statement & Objective

Construction tradespeople frequently switch subcontractors and job sites while maintaining the same trade craft. The legacy onboarding experience relied on repetitive, 7-field manual forms with clunky date pickers and zero automated verification.

This prototype redesigns the experience into a **Role-First, Zero-Typing Workflow**:
1. **Multiple Automated Ingestion Channels**: Resume OCR, 1-tap Lumber sync, major US trade platforms (Procore, ADP, NCCER, HCSS HeavyJob), and camera dispatch slip scanner.
2. **Dual-View Experience Profile**:
   - **Role-Wise View**: Aggregates total hours by trade craft (e.g. 2,440 hrs for *Journeyman Electrician*, 980 hrs for *Solar PV Specialist*) with instant job compatibility stamps (e.g. `Journeyman Qualified (>2,000h Met)`).
   - **Timeline-Wise View**: Career sequence arranged chronologically from present projects down to apprenticeship.
3. **Role-First Manual Entry**:
   - Step 1: Role & Trade with autocomplete suggestions and automatic trade classification detection.
   - Step 2: Multi-company logging under the same role (*Company 1*, *Company 2*, etc.) with calendar month pickers (`From Date` → `To Date`), "Currently working here" active toggle, and location suggestions.
4. **Light Mode Dismissible Toast System**: Full-width notifications with animated countdown progress bar that dismisses automatically or on tap.

---

## 📱 User Flow & Architecture

```
[Screen 1: Add Work Experience]
   │
   ├── 1. "Upload your resume" (PDF, DOCX) ──────────────────────────┐
   ├── 2. "Connect with Lumber" (1-Tap 1,840h timesheet sync) ───────┤
   ├── 3. US Trade Platforms: [Procore] [ADP] [NCCER] [HeavyJob] ────┤
   ├── 4. "Scan Documents" (Dispatch slips, union tickets, paystubs) ┘
   │                                                                 │
   └── 5. "Enter Details Manually"                                   ▼
          │                                            [Screen 2: Work Experience]
          ▼                                                   │
   [Screen 3: Add Experience Flow]                            ├── Segmented Control:
      │                                                       │   • Role Wise (Hours & Compatibility)
      ├── Step 1: Your Role & Trade                           │     - Role 1: Electrician (2,440 hrs)
      │   (Empty default, Datalist, Auto Trade Mapping)       │     - Role 2: Solar PV (980 hrs)
      │                                                       │   • Timeline Wise (Career Rail)
      └── Step 2: Companies under Role                        │
          ├── Company 1 (Empty default, Location datalist)    └── "+ Add New Experience" Action
          ├── Calendar Selectors (From Month -> To Month)               │
          ├── "+ Add another company under this role"                   │
          │   └── Generates identical "Company 2" card                  │
          └── "Save Experience to Profile" ─────────────────────────────┘
```

---

## 🎨 Design System & HIG Implementation

- **Aesthetic**: Native iOS Human Interface Guidelines with pure white background, subtle slate borders (`#E2E8F0`), and tactile `active:scale-[0.965]` micro-interactions.
- **Brand Palette**:
  - **BuilderFax Navy**: `#2C4A6F`
  - **Navy Dark**: `#1E3550`
  - **Surface Wash**: `#F8FAFC` & `#F0F4F8`
  - **Verified Emerald**: `#059669`
  - **Trade Amber**: `#D97706`
- **Typography**: `Plus Jakarta Sans` with tight tracking (`-0.012em`) and tabular figures (`tabular-nums`) for hours and stats.
- **Ergonomics**: Touch targets ≥ 48px, optimized for quick mobile tapping on outdoor job sites.

---

## 🚀 Running Locally

1. Clone this repository:
   ```bash
   git clone https://github.com/V1KHYAT/LumberFi-Assignment.git
   cd LumberFi-Assignment
   ```

2. Start any local static file server:
   ```bash
   # Python 3
   python -m http.server 8080
   ```

3. Open your browser at [http://localhost:8080/index.html](http://localhost:8080/index.html).

---

## ⚙️ GitHub Pages Setup

This repository is pre-configured with a GitHub Actions workflow at `.github/workflows/pages.yml`.
To deploy:
1. In your GitHub repository, go to **Settings** > **Pages**.
2. Under **Build and deployment** > **Source**, select **GitHub Actions** (or select **Deploy from a branch** -> `main` / `root`).
3. The site will deploy to `https://v1khyat.github.io/LumberFi-Assignment/`.
