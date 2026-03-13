# 📝 Incident Handler's Journal

---

## 📖 What is an Incident Handler’s Journal?

An **incident handler’s journal** is a structured log or diary that security professionals keep during the lifecycle of a security incident. It’s part of incident response best practices, ensuring that every step taken is documented, traceable, and reviewable for lessons learned or compliance requirements.

### 📑 What It Contains
- **Timeline of events**: When the incident was detected, escalated, contained, and resolved.  
- **Actions taken**: Specific steps performed (e.g., isolating a system, blocking an IP, resetting credentials).  
- **Evidence collected**: Logs, screenshots, forensic data, or communications relevant to the incident.  
- **Decisions made**: Why certain actions were chosen over others, including risk assessments.  
- **Communications**: Notes on who was informed (management, legal, external parties) and when.  
- **Observations**: Analyst insights, anomalies noticed, or unexpected system behavior.  
- **Lessons learned**: What worked well, what failed, and recommendations for improving future responses.  

### 🎯 Why It’s Important
- **Accountability**: Provides a clear record of who did what and when.  
- **Forensics**: Helps investigators reconstruct the incident accurately.  
- **Compliance**: Many standards (like PCI-DSS, ISO 27001, NIST) require documentation of incident handling.  
- **Continuous improvement**: Serves as a knowledge base for refining incident response plans.  

Think of it as the **black box recorder** for cybersecurity incidents—it captures everything so the organization can learn, defend itself legally if needed, and improve resilience.

---

## 📋 Incident Handler’s Journal Template

Use the following fields to document each journal entry:

### Date
Record the actual date of your journal entry.

### Entry
Provide a journal entry number (e.g., 1 for the first entry).

### Description
Write a description of the incident or the specific stage being documented.

### Tool(s) Used
List any cybersecurity tools used during the investigation or response.

### The 5 W’s
- **Who caused the incident?**  
- **What happened?**  
- **When did the incident occur?**  
- **Where did the incident happen?**  
- **Why did the incident happen?**

### Additional Notes
Add any thoughts, questions, or observations about the scenario.

---

## 🖊️ Example Entry (Template Filled)

### Date
March 13, 2026

### Entry
1

### Description
A ransomware attack disrupted operations at a small U.S. health care clinic. Employees were unable to access medical records, and a ransom note appeared demanding payment for decryption.

### Tool(s) Used
- Endpoint detection and response (EDR)  
- Antivirus/malware scanners  
- Email filtering logs  
- Network monitoring tools  

### The 5 W’s
- **Who caused the incident?** Organized hacker group targeting healthcare and transportation industries.  
- **What happened?** Phishing emails delivered malware, leading to ransomware encryption of critical files.  
- **When did the incident occur?** Tuesday morning, approximately 9:00 a.m.  
- **Where did the incident happen?** Clinic’s internal network and employee workstations.  
- **Why did the incident happen?** Employees opened malicious attachments, allowing attackers to bypass defenses.  

### Additional Notes
- Patient care was disrupted due to inaccessible medical records.  
- The clinic contacted external organizations for assistance.  
- Key question: Should the ransom be paid, or should recovery rely on backups and forensic support?  
