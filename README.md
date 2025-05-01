# Azure Sentinel Cloud Monitoring

This project demonstrates how to build a cloud-native security monitoring solution using Microsoft Sentinel. It includes end-to-end setup of Sentinel, data connector integration (Azure AD, Azure Activity), creation of custom analytics rules, automation with playbooks, and KQL-based threat hunting.

The goal is to provide a hands-on, reproducible framework for detecting and responding to security threats in a small Azure environment.

---

## 🚀 Key Features

- Microsoft Sentinel deployment
- Log Analytics Workspace setup
- Azure AD and Activity log ingestion
- Analytics rules for:
  - Multiple failed sign-ins
  - Impossible travel
  - IP address switches
- Automation rules and Logic App playbooks
- Threat hunting using KQL queries

---

## 🧰 Technologies Used

- Microsoft Sentinel
- Azure Log Analytics
- Azure Active Directory
- Azure Logic Apps
- Kusto Query Language (KQL)

---

## 📁 Directory Structure

```
azure-sentinel-cloud-monitoring/
│
├── README.md
├── setup-guide.docx               # Step-by-step instructions
├── queries/                     # Hunting queries in KQL
│   ├── multiple_failed_signins.kql
│   └── ip_switch_signins.kql
├── analytics-rules/            # configuring scheduled rules
└── playbooks/                  # Logic App JSON templates
```

---

## 🧪 How to Test

Once Microsoft Sentinel is fully deployed and data connectors are active:

### ✅ Simulate Failed Sign-ins
- Open an incognito browser and try to sign in to the Azure Portal with the correct email but **wrong password** (5+ times)
- Wait 5–10 minutes and check the **Incidents** tab in Sentinel

### ✅ Trigger Impossible Travel
- Try signing in from 2 different IPs using VPNs located in distant countries
- If the location distance exceeds threshold, the **geo-anomaly rule** will trigger

### ✅ Run Hunting Queries
- Go to **Microsoft Sentinel → Hunting**
- Run the KQL queries in `queries/` folder to manually search for anomalies

---

## ✅ Next Steps

- Add your own data sources (e.g., Azure VM, Storage)
- Export and integrate Logic Apps as playbooks
- Tune analytics rules to match your environment’s needs

