# 🛡️ Security Analysis: Malicious USB Entry Vector
### *Parking Lot Social Engineering Exercise*

---

## 📑 Project Overview
This project involves a controlled security assessment of a potentially malicious USB drive discovered in a corporate parking lot. The objective was to investigate the device's contents within a **hardened virtual environment** to identify potential attack vectors, data exposure risks, and mitigation strategies for an organization.

---

## 🔍 Scenario & Discovery
Upon mounting the device in a sandbox workstation, the contents were identified as belonging to **Jorge Bailey**, the Human Resource Manager at **Rhetorical Hospital**. The drive contained a high-risk mixture of personal and professional data, creating a significant surface area for social engineering.

### 📂 Directory Structure & File Inventory
- **Personal Folders:** `Family photos`, `Our dog pics`
- **Personal Documents:** `Vacation ideas.gdoc`, `Wedding list.gslides`, `JB_Resume.gdoc`
- **Corporate/HR Documents:** `New hire letter.gdoc`, `Shift schedules.gsheet`, `Employee budget.gsheet`

---

## ⚠️ Risk Assessment & Impact Analysis
The following table summarizes the vulnerabilities identified during the analysis of the device's metadata and file contents:

| Category | Technical Impact |
| -------- | ---------------- |
| **Data Exposure** | Several documents contain sensitive information, including Jorge's private data and the PII of third parties found within the work files. Additionally, these files disclose confidential operational data belonging to the hospital. |
| **Attacker Mindset** | The timesheets represent a significant security risk, providing actionable intelligence regarding Jorge's professional network. Malicious actors could execute sophisticated social engineering or phishing attacks—such as spoofing communications from coworkers—to compromise credentials. |

---

## 🛠️ Security Lab Setup
### *Malware Analysis Environment*
To perform this assessment without risking the host machine, a hardened sandbox environment was utilized. This prevents "guest-to-host" escapes and ensures any malicious payloads are contained within a disposable instance.

- **Isolation:** The analysis was conducted in a virtualized workstation with no network connectivity to local production assets.
- **Peripheral Handling:** The suspicious USB was mounted as a pass-through device to the virtual environment, ensuring the host operating system's AutoPlay remained inactive.
- **Persistence:** All analysis was performed in a non-persistent session, where any changes or potential infections were discarded upon completion.

---

## 📝 Technical Analysis of Device Contents
The following findings were documented during the deep-dive of the mounted volume:

### 1. Data Sensitivity & PII Exposure
The device contained a high volume of unencrypted data that poses a risk to both individual and organizational privacy:
- **Personal Data Leakage:** Several documents contain sensitive information, including Jorge's private data and the PII (Personally Identifiable Information) of third parties found within the work files.
- **Corporate Intel:** These files disclose confidential operational data belonging to the hospital, which could be used to facilitate corporate espionage or operational disruption.

---

## 🛡️ Risk Mitigation & Recommended Controls
To reduce the risk of a successful incident via removable media, the following multi-layered controls are recommended:

| Control Type | Implementation Strategy | Impact |
| ------------ | ----------------------- | ------ |
| **Managerial** | Implement employee awareness programs regarding suspicious peripherals. | Reduces human susceptibility to "lost USB" baits. |
| **Operational** | Establish routine antivirus and malware scans for all external devices. | Detects known signatures before execution. |
| **Technical** | Disable **AutoPlay/AutoRun** via Group Policy on all company PCs. | Prevents the automatic execution of malicious code. |
