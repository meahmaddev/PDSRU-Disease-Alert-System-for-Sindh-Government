# PDSRU Disease Alert System for Sindh Government

An automated WhatsApp Surveillance Bot and Alert System built using **n8n** for the Provincial Disease Surveillance & Response Unit (PDSRU) and District Disease Surveillance & Response Units (DDSRU) under the Director General Health Services, Government of Sindh.

---

## 📁 Repository Structure

```text
PDSRU-Disease-Alert-System-for-Sindh-Government/
├── config/
│   ├── high_priority_diseases.json   # Configured alert list for high-priority diseases
│   ├── static_divisions.json         # Administrative divisions and district mappings for Sindh
│   └── users.example.json            # RBAC user credentials template (PDSRU & DDSRU roles)
├── workflows/
│   └── PDSRU-Disease-Alert-System-for-Sindh-Government.json  # Main n8n Workflow
├── .env.example                      # Template for environment variables
├── .gitignore                        # Git exclusion rules for secrets
└── README.md                         # Documentation
```

---

## ✨ Features

- **Role-Based Access Control (RBAC):**
  - **PDSRU Role:** Full access to province-wide, division-wise, and district-wise disease surveillance reports.
  - **DDSRU Role:** Restricted access strictly scoped to their assigned district.
- **Session-Based Authentication:** Automated 10-minute sliding timeout session management for authorized WhatsApp users.
- **Dynamic Query Parsing:** Natural language query matching for high-priority disease filtering, disease searches, top-N rankings, and district/division summaries.
- **Interactive WhatsApp Menus:** Native WhatsApp list menus dynamically served based on user role permissions.

---

## 🚀 Getting Started

### Prerequisites

- [n8n](https://n8n.io/) instance (Self-hosted or Cloud)
- Meta WhatsApp Business API Account

### Setup Instructions

1. **Clone the Repository:**
   ```bash
   git clone [https://github.com/your-username/PDSRU-Disease-Alert-System-for-Sindh-Government.git](https://github.com/your-username/PDSRU-Disease-Alert-System-for-Sindh-Government.git)
   cd PDSRU-Disease-Alert-System-for-Sindh-Government
   ```

2. **Configure Environment Variables:**
   ```bash
   cp .env.example .env
   ```
   Fill in your actual WhatsApp API credentials, base URLs, and access tokens in `.env`.

3. **Set Up User Roster:**
   Create a non-committed `users.json` file inside `config/` using `users.example.json` as a template:
   ```bash
   cp config/users.example.json config/users.json
   ```

4. **Import Workflow into n8n:**
   - Open your **n8n Dashboard**.
   - Click **Workflows** > **Import from File**.
   - Select `workflows/PDSRU-Disease-Alert-System-for-Sindh-Government.json`.
   - Configure your WhatsApp credentials inside the respective node settings and activate the workflow.

---

## 🛡️ Security

- Real phone numbers, passwords, and API secret keys **must never** be committed to version control.
- Ensure `config/users.json` and `.env` remain listed inside `.gitignore`.