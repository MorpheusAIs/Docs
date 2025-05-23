This is a process-specific how-to. For general how-to guides, see morpheus-how-to-guides.md.

# How to Contribute Code to Morpheus: The Six-Stage Development Process

This guide explains the step-by-step process for contributing new code or dashboards to the Morpheus project, following open source best practices. Use this as a checklist to ensure your work meets project standards from planning to deployment.

---

## Goal
Contribute new backend code or frontend dashboards to Morpheus, moving from design through deployment and final checks.

## Prerequisites
- Access to the Morpheus code repository
- Familiarity with Morpheus coding standards ([see reference](../Code%20Providers/Coder%20Guide.md))
- Understanding of the audit and deployment process ([see reference](../Protection%20Fund%20Details.md))
- Testnet and mainnet credentials (as required)

---

## Step-by-Step Process

### 1. Planning / Design
- **Action:** Write a clear description and specification for what is to be developed (backend or frontend).
- **Outcome:** Approved design/spec document.

### 2A. Backend Coding
- **Action:** Begin backend code development.
- **Outcome:** Backend code ready for testnet deployment.

### 2B. Dashboard (Frontend) Development
- **Action:** Begin dashboard/frontend development (can run in parallel to backend testnet/audit).
- **Outcome:** Dashboard code ready for testing.

### 3. Testnet for Backend Code
- **Action:** Deploy backend code to testnet. Testers verify backend is functioning as expected.
- **Outcome:** Backend code passes testnet QA.

### 4A. Audit for Backend Code
- **Action:** Submit backend code for audit. Complete any required remediations.
- **Outcome:** Audit passed and remediations complete.

### 4B. Dashboard Testing
- **Action:** Deploy dashboard for testing before mainnet deployment.
- **Outcome:** Dashboard passes QA and is ready for mainnet.

### 5A. Mainnet Deployment of Backend Code
- **Action:** Deploy backend code to mainnet or prepare a deployment guide.
- **Outcome:** Backend code live on mainnet.

### 5B. Mainnet Deployment of Dashboard
- **Action:** Deploy dashboard to mainnet or main branch, or prepare a deployment guide.
- **Outcome:** Dashboard live on mainnet.

### 6A. Final Checks of Backend Code
- **Action:** Post-deployment confirmation of correct backend deployment and expected function.
- **Outcome:** Backend code verified on mainnet.

### 6B. Final Checks of Dashboard
- **Action:** Test and verify dashboard UI with new smart contract functions.
- **Outcome:** Dashboard UI verified and functional.

---

## Quick Reference Table

| Stage | Backend Action                | Frontend Action                | Outcome                        |
|-------|-------------------------------|-------------------------------|--------------------------------|
| 1     | Planning/Design               | Planning/Design               | Approved spec                  |
| 2     | Begin Coding                  | Begin Dashboard Development   | Code ready for test/testnet    |
| 3     | Testnet QA                    |                               | Backend passes testnet         |
| 4     | Audit & Remediation           | Dashboard Testing             | Audit passed, dashboard QA     |
| 5     | Mainnet Deployment            | Mainnet Deployment            | Code/dashboard live            |
| 6     | Final Checks                  | Final Checks                  | Verified on mainnet            |

---

## Next Steps & References
- [Morpheus Coding Standards](../Code%20Providers/Coder%20Guide.md)
- [Audit & Protection Process](../Protection%20Fund%20Details.md)
- [Deployment Guide Template](../Code%20Providers/Deployment-Guide.md) *(if available)*

