# 🏥 Apollo Hospitals: Appointment No-Show & Patient Engagement Analysis

An end-to-end Exploratory Data Analysis (EDA) project in Python exploring booking behavior, patient retention, doctor utilization, and financial losses caused by appointment no-shows across 15 cities in India.

---

## 📌 Project Overview
Apollo Hospitals provides healthcare consultations through in-clinic visits, video consults, and home visits across multiple channels (Mobile App, Website, Call Centre, Walk-in, and Partner Apps). 

A notable proportion of booked consultations result in patient **no-shows**, directly impacting doctor utilization, hospital revenue, and patient health outcomes. This project analyzes appointment trends from **2022 to 2024** to surface actionable operational, clinical, and financial insights.

---

## 📂 Dataset Information
The project analyzes two relational datasets:

1. **`apollo_appointments_fact.csv`**
   - **Records:** 75,000 rows × 52 columns
   - **Grain:** One row per booked appointment (contains booking metadata, timestamps, outcomes, reminders, demographics, and billing details).
2. **`apollo_doctors_dim.csv`**
   - **Records:** 320 rows × 15 columns
   - **Grain:** One row per doctor (experience, specialization, consultation fees, ratings).
   - **Join Key:** `doctor_id`

---

## ⚙️ Analytical Rules & Business Logic
Following strict domain rules specified for clean analysis:
- **No-Show Rate Calculation:**
  $$\text{No-Show Rate} = \frac{\text{No-Show Count}}{\text{Completed} + \text{No-Show} + \text{Cancelled}}$$
  *(Excludes `Scheduled` appointments as their outcome is pending).*
- **Quality & Utilization Metrics:** Metrics like `wait_time`, `patient_satisfaction`, `consultation_duration`, and `doctor_utilisation` are scoped exclusively to **`Completed`** appointments.
- **Revenue Scope:** Realized revenue analysis applies only to completed visits (non-completed visits carry zero realized revenue).
- **Categorical Handling:** String value `'None'` in fields like chronic condition, membership type, insurance provider, and cancellation reason represents a valid non-applicable state rather than missing data.

---

## 🔍 Key Analysis Sections

### 1. Business & Volume Trends
- Monthly & quarterly consultation volume trajectory (2022–2024).
- Outcome breakdown across Completed, No-Show, Cancelled, and Scheduled visits.
- Channel mix and volume drivers (App vs. Web vs. Walk-in vs. Call Centre).

### 2. No-Show & Dropout Analysis
- High-risk vs. low-risk specialties and geographical hubs.
- Correlation between **booking lead time** and no-show probability.
- Impact of time-of-day (morning vs. evening slots) and day-of-week (weekdays vs. weekends).

### 3. Patient Engagement & Reminder Efficacy
- Effectiveness of reminder channels (SMS, WhatsApp, Automated Call) vs. unreminded bookings.
- Predictive power of historical no-show patterns on future attendance.
- Attendance variance between Apollo Members vs. Non-members, and repeat vs. first-time patients.

### 4. Demographic & Clinical Segmentation
- Risk profiling across age cohorts, genders, and chronic illness patients.
- High-dropout visit reasons and specialty-level age distributions (Paediatrics, Gynaecology, Psychiatry).

### 5. Financial & Revenue Impact
- Estimation of lost revenue due to cancellations and no-shows.
- Average revenue realization across specialties and consultation formats.
- Top revenue-generating cities, payment modes, and out-of-pocket expenses vs. insurance claims.

### 6. Doctor Utilization & Service Quality
- Specialty-level doctor capacity and utilization rates.
- Clinic wait-time distributions across departments and peak hours.
- Correlation between consultation duration, doctor experience, and patient satisfaction scores.

---

## 🛠️ Tech Stack & Libraries
- **Language:** Python 3.x
- **Development Environment:** Jupyter Notebook (`.ipynb`)
- **Data Manipulation:** `pandas`, `numpy`
- **Data Visualization:** `matplotlib`, `seaborn`

---

## 📁 Repository Structure
```text
├── data/
│   ├── apollo_appointments_fact.csv
│   └── apollo_doctors_dim.csv
├── notebooks/
│   └── apollo_eda_analysis.ipynb
├── images/
│   └── (visualizations / charts)
├── README.md
└── requirements.txt
