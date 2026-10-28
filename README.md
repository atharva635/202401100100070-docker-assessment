# CA-2 Practical Assessment: Docker & Container Security

### 1. Student & Service Information
- **Name:** Atharva Gupta
- **Class:** CS - A
- **Registration Number:** 202401100100070
- **Assigned Port:** 8070 (calculated using rule: 80 + last 2 digits of REGNO -> 80 + 70 = 8070)
- **Docker Hub Username:** atharva65
- **Docker Hub Link:** https://hub.docker.com/r/atharva65/fest-backend

---

### 2. AI Tools Declaration
Used Google Gemini / ChatGPT to help format Docker Compose files with network isolation, configure multi-stage Alpine Dockerfile, verify Trivy security scanner flags, and execute cosign key generation and cryptographic verification.

---

### 3. Backend Image Digest (v1.0.0)
`sha256:9e6d2155b4d48f05c0505ce8f28c8629da6ae6c92243699b95a9adb3d8f82dd0`

---

### 4. Vulnerability Remediation Table (Stage 3.3)

| Metric | fest-backend:0.1 (Base: python:3.9) | fest-backend:0.2 (Hardened: python:3.12-alpine) |
| :--- | :--- | :--- |
| **CRITICAL Vulnerabilities** | 51 | 0 |
| **HIGH Vulnerabilities** | 151 | 0 |
| **Final Image Size** | ~1.61 GB | ~93.3 MB |

**Summary of fixes made:**
1. Switched the base image from `python:3.9` to `python:3.12.16-alpine` to eliminate bloated and outdated OS packages.
2. Created a dedicated non-root user (`appuser` with `appgroup`) inside the Dockerfile instead of running the application container as root.
3. Updated dependencies in `requirements.txt` to current secure versions (`Flask==3.1.2`, `Werkzeug==3.1.3`, `psycopg2-binary==2.9.10`).
4. Verified that running `trivy image --severity CRITICAL --ignore-unfixed --exit-code 1 fest-backend:0.2` exits with code 0.

---

### 5. Incomplete Steps
None. All 5 stages were completed according to the assessment specifications.
