# Surgical Referral Digitization – Power Platform Solution (Microsoft Vancouver BC Campus - Fraser Health Hackathon 2024)

**Co-author**: Andrew Ihnativ  (see PowerPoint for credits)  
**Event**: Microsoft + Fraser Health Hackathon (November 2024)  
**Solution Stack**: Power Apps, Power Automate, Microsoft Dataverse, Power BI, GitHub, Azure DevOps  

---

## 🧠 Problem Statement

Surgical referrals in Fraser Health have historically relied on **faxed forms**, contributing to inefficiencies, delays, and data quality issues. Referrals pass through multiple hands (providers, clerks, schedulers), with repeated manual steps such as faxing, data entry, validation, and physical handoffs. This process not only wastes time but introduces **risks to patient safety** and **inaccurate EMR records**.

---

## 🎯 Business Requirements

The solution aimed to meet the following goals:

| Objective                        | Description |
|----------------------------------|-------------|
| **Eliminate fax dependency**     | Enable digital submission via web or e-fax ingestion |
| **Improve data quality**         | Automate validation and reduce transcription errors |
| **Reduce time-to-EMR-entry**     | Minimize manual steps between referral and EMR entry |
| **Enhance stakeholder access**   | Make referral status and information easily accessible |
| **Enable future extensibility**  | Design reusable modules for other referral pathways |
| **Secure PHI handling**          | Align with health data privacy requirements |

---

## 👤 Personas Modeled

To guide development and UX decisions, the team designed a scenario-driven model with representative users:

- **Provider** – initiates referrals  
- **Booking Clerk (MOA)** – receives and processes referral packages  
- **Patient** – indirectly affected by workflow speed and safety  
- **Developer aka Admin/IT** – ensures deployment, monitoring, and integration with EMR

---

## ⚙️ Architecture Overview

| Component             | Implementation |
|-----------------------|----------------|
| **Front End**         | Power App – responsive form interface (for staff and providers) |
| **Input Gateway**     | Two channels: Webform (direct Power App) and e-Fax via Power Automate |
| **Workflow Engine**   | Power Automate – triggered flows for form submission, validation, routing |
| **Data Layer**        | Microsoft Dataverse – structured and secured storage |
| **Monitoring & BI**   | Power BI – dashboards to track referral volume, rejection rates, and usage |
| **Security**          | M365-based authentication, access roles by user type |
| **DevOps**            | GitHub & Azure DevOps – version control, CI/CD staging pipelines |

---

## 🚀 Functional Workflow

1. **Referral Creation**
   - Option 1: Provider uses a web-based Power App form
   - Option 2: Provider sends a traditional fax to an e-Fax inbox, parsed via Power Automate OCR (AI Builder optional)

2. **Data Capture & Validation**
   - Structured fields (dropdowns, dates, checkboxes) ensure completeness
   - Conditional logic handles specialty-specific information

3. **Workflow Routing**
   - Validated data is sent to the booking clerk dashboard
   - Email notifications or Teams alerts can be triggered

4. **Booking Clerk Actions**
   - View referral list in the app
   - Mark referrals as booked or flag for missing information

5. **Analytics & Reporting**
   - Power BI dashboards measure key KPIs:
     - Time to process
     - Rejection rate
     - Source of form (Webform vs. e-Fax)
     - Provider usage trends

---

## 🧪 Testing and QA

| Test Type              | Description |
|------------------------|-------------|
| **Unit Testing**       | Power Automate expressions, data field validation rules |
| **Integration Testing**| Workflow tests with e-Fax + Power App form pathways |
| **Security Testing**   | Role-based access control simulation with test user accounts |
| **Usability Testing**  | Form inputs and dashboard interactions tested with mock users |
| **Performance Testing**| Parallel referrals, large submission stress tests using dummy data |
| **Fallback Scenarios**| Invalid fields, incomplete submissions, retry logic for flow failures |

> Outcome: Form rejection rates decreased; submission-to-EMR-entry times improved in simulated environments.

---

## 🤝 Collaboration and Team Engineering Practice

Although team development occurred during a short hackathon, we followed professional software practices:

- **Shared Design Figma Mockups** (not included here, placeholder assumed)
- **Agile task division**: Frontend, workflows, data integration, and demo scripting
- **Code & Logic Ownership by Module**
- **GitHub Repo Structure**:
/PowerApp/
/PowerAutomate/
/Documentation/
/PowerBI/
/TestCases/

- **CI/CD Readiness**:
- Solutions can be exported and imported via managed solutions
- Deployment pipelines via Azure DevOps YAML (optional GitHub Actions trigger)
- Environment variables abstracted for prod/test environments

---

## 📈 Success Metrics

These indicators were proposed to measure impact post-deployment:

| Metric | Definition |
|--------|------------|
| **# of digital referrals** | Daily/weekly count of webform or e-Fax submissions |
| **% rejection rate** | Forms bounced due to incomplete or invalid data |
| **Median time to EMR entry** | Tracked from referral time to system registration |
| **Adoption Rate by Providers** | Ratio of eligible providers using digital method |
| **Clerk satisfaction & load** | Qualitative and count-based survey results |
| **ROI estimation** | Time savings × hourly wage for manual entry avoided |

---

## 🔭 Scalability & Next Steps

The project was designed for vertical and horizontal scale-out.

**Horizontal Scale-out**:
- Public Health, LTC, MHSU, and other fax-reliant services can use the same base structure

**Vertical Enhancements**:
- EMR integration via HL7/FHIR APIs or file drops
- Referral prioritization module (based on urgency/severity)
- Built-in communication (secure messaging/chat with providers)
- Comprehensive scheduling logic

**Planned Technical Extensions**:
- Power BI integration for executive dashboards
- AI Builder: intelligent form classification and auto-routing
- Mobile experience refinement

---

## 🧩 Repository Contents

| Folder/File            | Description |
|------------------------|-------------|
| `/PowerApp`            | Canvas app exported `.msapp` file |
| `/PowerAutomate`       | `.zip` packages of automated workflows |
| `/PowerBI`             | .pbix file and sample dataset |
| `/Documentation`       | README, architecture diagrams, personas |
| `/TestCases`           | Test plan, test data, and results |
| `/Deployment`          | DevOps scripts, export/import instructions |
| `.gitignore`           | Standard exclusions for Power Platform projects |
| `README.md`            | This file |

---

## 🛡️ Security and Compliance

- All patient and provider data in the demo was **mocked** or **pseudonymized**
- Enforced Microsoft DLP policies across environments
- Power Platform environments were provisioned in Canada (Azure region)
- Role-based access control on all apps and flows
- Logging and audit trails enabled for all data operations

---

## 🧾 License

This repository is intended for educational and demo purposes within Fraser Health and Microsoft Hackathon initiatives. For use outside these contexts, please contact the repository owner (Andrew Ihnativ).
