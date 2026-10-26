# DrishtiSetu
**DrishtiSetu** is a role-locked clinical management and triage app for eye camps built with React Native/Expo. It enforces blind handoffs across 4 isolated counters (Registration, General Exam, Diagnostics, Refraction), keeping prior notes hidden to prevent bias. An Admin desk compiles the partitioned data for physical card printing.

Author- Bhavya

# DrishtiSetu (दृष्टिसेतु)

A role-locked, component-isolated clinical triage and management platform built with React Native/Expo for multi-station rural eye screening camps.

---

## Architecture & Security Highlights

* **Role-Locked Isolation:** Staff authenticate into dedicated counters (Station 1–4). The UI dynamically strips and unmounts all screens, navigation paths, and input fields outside that station's boundary.
* **Blind Handoff Protocol:** Downstream clinicians verify patients strictly via serialized identifiers (`Sl. No.` and `Name`). Prior diagnostic entries, examination findings, and test metrics remain completely hidden to eliminate clinical bias.
* **Partitioned Data Model:** Patient records are partitioned into station-specific sub-objects to prevent cross-network data exposure.
* **Unified Admin Compilation:** The Master Admin desk retains full access to compile separated station entries into standard physical cards for `@media print` browser printing and PDF export.

---

## Counter Workflow & Permissions

[Patient Arrival at Camp]
                          │
                          ▼
           [Station 1: Registration Desk]
            - Auto-generates Sl. No.
            - Captures Demographics
                          │
        ┌─────────────────┴─────────────────┐
        │ (Completed in parallel / any order)│
        ▼                                   ▼
[Station 2: General Examination]    [Station 3: Vision & Clinical]

Slit-lamp biomicroscopy           - Uncorrected & corrected acuity

Anterior segment findings         - Intraocular tension (IOP)

Systemic history (HTN, DM)        - Sugar, Urine, & Fundus
│                                   │
└─────────────────┬─────────────────┘
▼
[Station 4: Spectacles Rx]
- Distance refraction grid
- Near vision & ADD power
│
▼
[Master Admin / Printing Desk]
- Compiles full patient record
- Physical paper card export / print
