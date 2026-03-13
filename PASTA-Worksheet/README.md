# 👟 Sneaker Company Security Analysis (PASTA Framework)

### *Process for Attack Simulation and Threat Analysis (PASTA)*

---

## 📑 Project Overview
This project applies the **PASTA threat modeling framework** to a sneaker company’s application. The goal is to identify business objectives, technical scope, threats, vulnerabilities, and security controls to strengthen the organization’s resilience against cyberattacks.

---

## 🥇 Stage I: Define Business & Security Objectives
Key business requirements analyzed:
- Users can create member profiles internally or by connecting external accounts.
- The app must process financial transactions securely.
- The app should comply with **PCI-DSS** standards.

---

## 🖥️ Stage II: Define the Technical Scope
Technologies used by the application:
- **Application Programming Interface (API)**
- **Public Key Infrastructure (PKI)**
- **SHA-256**
- **SQL**

APIs facilitate the exchange of data between customers, partners, and employees. They handle sensitive information and connect multiple systems, creating a larger attack surface. Prioritization of API security is critical, but specific API usage details must be considered before assigning risk levels.

---

## 🔄 Stage III: Decompose Application
📊 *Sample Data Flow Diagram*  
*(Placeholder for diagram illustration of data movement between users, APIs, databases, and authentication systems.)*

---

## ⚠️ Stage IV: Threat Analysis
Two major threats identified:
- **Injection attacks**
- **Session hijacking**

---

## 🕳️ Stage V: Vulnerability Analysis
Two vulnerabilities that could be exploited:
- Lack of prepared SQL statements
- Broken API token management

---

## 🌳 Stage VI: Attack Modeling
📌 *Sample Attack Tree Diagram*  
*(Placeholder for diagram showing possible attack paths leading to data compromise.)*

---

## 📉 Stage VII: Risk Analysis & Impact
Recommended security controls to reduce risk:
- **SHA-256** for secure hashing
- **Incident response procedures** for rapid containment
- **Password policy** enforcing strong authentication
- **Principle of least privilege** to minimize access exposure

---

## ✅ Conclusion
By applying the **PASTA framework**, the sneaker company can proactively identify risks, strengthen technical defenses, and align business objectives with robust security practices.
