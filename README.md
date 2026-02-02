# Airport Infrastructure Project Finance Model  
**Circular Debt Sculpting & Cash Sweep (Lender View)**

---

## 📌 Executive Summary

This repository contains an advanced **Project Finance debt model** for an **Airport Infrastructure asset**, built from a lender’s perspective.

The model addresses a complex challenge in infrastructure finance: **circular debt sculpting**, where **principal repayments depend on available cash**, while **interest expense (which affects cash) depends on outstanding debt**.

The model resolves this circularity while implementing **cash sweep mechanics**, **DSCR-based amortisation**, and an **automated analytical summary** designed to replicate how lenders and credit committees assess bankability under a Base Case.

---

## 🚀 Key Features

### 🔹 Advanced Debt Sculpting
- Automated principal repayment sizing to meet a **target DSCR**
- Debt service dynamically adjusts to CFADS availability
- Circular reference handled in a controlled and auditable manner

### 🔹 Circular Logic Resolution
- Interest expense depends on opening debt
- Available cash depends on interest expense
- Principal repayment depends on remaining cash  
→ Circularity is preserved and stabilized rather than artificially broken

### 🔹 Dynamic Cash Sweep
- Excess cash is swept toward accelerated principal repayment
- Sweep activated only when DSCR exceeds a **lock-up threshold (e.g. 1.20x)**
- Configurable sweep percentage (e.g. 75%)

### 🔹 Automated Credit Commentary
- A dedicated **Analytical Summary** sheet converts model outputs into
  human-readable lender-style commentary
- Narrative highlights:
  - DSCR performance
  - Cash sweep effectiveness
  - Residual debt / balloon risk
  - Refinancing dependency

### 🔹 Covenant & Structural Monitoring
- Real-time checks for:
  - DSCR compliance
  - Cash leakage
  - Debt fully repaid at maturity
  - Lock-up trigger breaches
- Designed to feed directly into a lender checklist

---
![Project Dashboard Screenshot](./assets/Screenshot 2026-02-02 115826.png)
---

## 🛠 Technical Stack — Excel (Advanced)

This model goes beyond standard Excel usage and focuses on **financial logic expressed through Excel**:

- **Circular Calculation Control**
  - Iterative calculations used intentionally for debt sculpting
  - Clear separation between inputs, calculations, and checks

- **Structured References**
  - Excel Tables (ListObjects) used for debt schedules and cash flow blocks
  - Improves auditability and scalability

- **Advanced Formula Logic**
  - IF / IFERROR for structural robustness
  - TEXT, CHAR(10), and conditional logic to generate narrative summaries
  - Dynamic aggregation of key credit metrics (min DSCR, total debt service, residual balance)

- **Data Validation & Error Checks**
  - Input controls to prevent invalid scenarios
  - Dedicated `Debt_Check` sheet with visual flags (pass / fail)

---

## 📈 Financial Strengths

The model is designed to withstand **lender-level scrutiny**:

- **Liquidity Analysis**
  - Detailed tracking of CFADS (Cash Flow Available for Debt Service)
  - Explicit separation between operating cash flow and financing flows

- **Risk Identification**
  - Automatic detection of **balloon / residual debt** at maturity
  - Clear signaling of refinancing dependency

- **Scenario-Ready Architecture**
  - Structure allows rapid stress testing:
    - Revenue downside (e.g. passenger traffic decline)
    - Cost inflation (O&M stress)
  - All credit metrics update consistently under stress

---

## 📂 Project Structure

```text
├── Inputs
│   └── Macroeconomic assumptions, debt terms, DSCR targets
│
├── Operating_Cashflow
│   └── Revenue → OpEx → CFADS calculation
│
├── Debt_Schedule
│   └── Interest, sculpted principal, cash sweep, closing debt
│
├── Debt_Check
│   └── Covenant tests, lock-up logic, visual flags
│
└── Summary
    └── Automated lender-style analytical summary
