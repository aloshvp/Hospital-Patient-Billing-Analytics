# Hospital Patient & Billing Analytics Dashboard

## Objective

Analyze patient admission, treatment, and billing data to build an interactive Power BI
dashboard that helps hospital management monitor patient trends, admission patterns, and
revenue performance to support operational and financial decision-making.

## Dataset

- **Source:** Kaggle — "Healthcare Dataset" (synthetic, prasad22)
- **Rows / Columns (raw):** 55,500 rows × 15 columns
- **Rows / Columns (cleaned):** 54,966 rows × 16 columns (added `Length of Stay`)
- **Key columns:** Name, Age, Gender, Blood Type, Medical Condition, Date of Admission,
  Doctor, Hospital, Insurance Provider, Billing Amount, Room Number, Admission Type,
  Discharge Date, Medication, Test Results

## Folder Structure

```
Project_Name/
├── BRD/                    # Business Requirements Document
├── FRD/                    # Functional Requirements Document
├── Data/
│   ├── raw/                # Original dataset
│   ├── cleaned/            # Cleaned dataset + Dim_Date table
│   └── assessment/         # Column-wise assessment (Column_Assessment.xlsx)
├── Visuals/                # Dashboard mockups (pptx + html)
├── PowerBI/
│   ├── pbix/                # dashboard.pbix (built in Power BI Desktop)
│   ├── exports/              # Exported PDF/PNG of final dashboard
│   ├── Data_Model_and_DAX_Build_Guide.md
│   └── PowerQuery_Import_Script.m
├── Reports/                # Analysis Report (insights, data model, recommendations)
├── Scripts/                 # Cleaning & analysis scripts
└── README.md
```

## Steps to Reproduce

1. **Assess & clean dataset** — see `Data/assessment/Column_Assessment.xlsx` for the full
   column-by-column review, and `Data/cleaned/cleaned_dataset.csv` for the cleaned output.
   Cleaning removed 534 duplicate rows, standardized `Name` casing, converted date columns
   to proper date type, and corrected 108 negative `Billing Amount` values to absolute value.
2. **Design dashboard mockups** — see `Visuals/Dashboard_Mockup.pptx` for the four-section
   layout (Overview/KPIs, Demographics & Admissions, Billing & Insurance, Clinical Outcomes).
3. **Build Power BI dashboard & data model** — follow
   `PowerBI/Data_Model_and_DAX_Build_Guide.md` for table relationships, build steps, and
   ready-to-paste DAX measures. Import `cleaned_dataset.csv` and `Dim_Date.csv`, or use
   `PowerBI/PowerQuery_Import_Script.m` to automate the import and column typing.
4. **Export reports** — once `PowerBI/pbix/dashboard.pbix` is finalized, export it to PDF
   (File → Export → Export to PDF) and save as `PowerBI/exports/dashboard_export.pdf`.

## Key Insights / Learnings

- **40,240 unique patients** across 54,966 admission records; **$1.40B total billing**,
  averaging **$25,550 per patient**.
- Admissions are nearly evenly distributed across all 6 medical conditions (~9.1K–9.2K each)
  and all 3 admission types (Elective 33.61%, Urgent 33.46%, Emergency 32.93%), indicating a
  balanced patient population with no single dominant driver.
- Test results split almost evenly three ways: Abnormal 33.54%, Normal 33.35%,
  Inconclusive 33.11%.
- Billing totals are consistent across insurance providers (within a $277M–$284M range),
  with no single payer standing out.
- Average Length of Stay across the dataset is **15.50 days**.
- Admissions Over Time shows a dip in 2024 — this reflects a partial year in the dataset
  (data ends 07-05-2024), not a real decline; 2019 is also a partial year (starts 08-05-2019).
- Top hospital by volume: **LLC Smith (44 admissions)**, followed by Ltd Smith (39).
- Hospital and Doctor fields are near-unique per record and were kept as descriptive
  attributes rather than modeled as separate dimension tables.
- Full analysis, conclusions, and recommendations are documented in
  `Reports/Analysis_Report.pdf`.

