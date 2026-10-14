# HR Bulk Employee Import – Database System API (`hr-emp-db-sys-api`)

**2027 Nurture Partner Network (NPN) MuleSoft Hackathon Challenge – Cognizant**

---

## 📌 Overview
`hr-emp-db-sys-api` is the System API layer connecting the MuleSoft integration ecosystem to the underlying MySQL database (`hr_import`). It abstracts data persistence and master reference caching behind a clean, RESTful RAML contract on port `8081`.

---

## 🚀 Key Endpoints & Capabilities
- **Master Reference Data**:
  - `GET /api/departments`: Active departments (`department_key`, `department_code`, `department_name`).
  - `GET /api/locations`: Active office locations (`location_key`, `location_code`, `location_name`).
  - `GET /api/designations`: Job title to corporate grade mappings (`designation`, `grade`).
- **Operational Employees**:
  - `GET /api/employees`: Query existing employees with email filtering (`?email=...`) for duplicate prevention.
  - `GET /api/employees/{employeeId}`: Retrieve individual employee record.
  - `POST /api/employees/batch`: Bulk upsert clean records (`INSERT INTO employees ... ON DUPLICATE KEY UPDATE`).
- **Run Audit & Tracking**:
  - `GET /api/import-runs`: Check for file duplicates using SHA-256 checksums.
  - `POST /api/import-runs`: Register a new processing run (`RUN-<timestamp>-<hash>`).
  - `PUT /api/import-runs/{runId}`: Finalize run counts, status (`SUCCESS`, `PARTIAL_SUCCESS`, `ABORTED_THRESHOLD`), and completion timestamps.

---

## 📖 Complete Documentation
- **[PROJECT_DOCUMENTATION.md](PROJECT_DOCUMENTATION.md)**: Architecture, components, and data flows.
- **[ERRORS_FACED_AND_RESOLUTIONS.md](ERRORS_FACED_AND_RESOLUTIONS.md)**: Technical challenges and solutions.
- **[STEP_BY_STEP_EXECUTION_GUIDE.md](STEP_BY_STEP_EXECUTION_GUIDE.md)**: Complete execution guide.
- **[HLD_HR_Bulk_Employee_Import.md](HLD_HR_Bulk_Employee_Import.md)**: High-Level Design document.
