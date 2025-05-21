# 📋 TODO: P2Inpoint Exposure Detection & Scoring (Crawler-Based)

This project aims to identify and score the risk of Personally Identifiable Information (PII) exposure on URLs from crawled domains, with a focus on detecting **open forms collecting sensitive data**.

---

## 🔍 PHASE 1: Foundations & Research

- [ ] Survey available PII detection tools and frameworks
  - Compare: Microsoft Presidio, spaCy with custom NER, regex-based approaches
  - Evaluate locale-specific support (e.g., CPF, RG)
- [ ] Define what constitutes “sensitive” form fields
  - Examples: `name`, `email`, `cpf`, `birthdate`, `phone`, `address`
- [ ] Define scoring model for PII signals
  - Assign weights (e.g., email = 5, login name = 5,  full name = 10, personal id number = 15, etc)
  - Include penalties (e.g., no HTTPS = +10 risk, GET method = +15 risk, etc)

---

## 🧠 PHASE 2: Crawler Integration & Extraction

- [ ] Enhance crawler to capture DOM snapshots
- [ ] Build HTML form extractor
  - Parse: `form`, `input`, `textarea`, `select`
  - Extract `name`, `id`, `label`, `placeholder`, etc.
- [ ] Identify exposed forms with sensitive fields
  - Match field names/labels to predefined sensitive keywords
- [ ] Check form security posture
  - Detect missing HTTPS
  - Detect use of GET method for form submission

---

## 🧪 PHASE 3: PII Detection in Page Content

- [ ] Apply selected PII detection tool to visible text
  - Exclude scripts, styles, non-user-visible content
- [ ] Detect PII for documents (pdf, xlsx, docx, odt, etc)
- [ ] Normalize PII detection results
  - Classify and score: emails, phones, ID numbers, etc.

Poc kql

min_webcontent: cpf and raw_webcontent: "name="cpf""

---

## 📊 PHASE 4: Scoring and Aggregation

- [ ] Implement per-URL scoring logic
  - Combine content PII, form presence, and security checks
- [ ] Aggregate risk at host/domain level
  - Metrics: average score, max score, high-risk URL count
- [ ] Define alerting thresholds
  - Example: trigger alert if host score > 70 or form collects CPF/email

---

## 🖼️ PHASE 5: Reporting and Visualization

- [ ] Create structured output report (CSV, JSON, or HTML)
  - Include: URL, risk score, detected PII types, form fields
- [ ] Build dashboard or summary CLI tool
  - Group by domain
  - Include links to original pages or crawl logs

---

## 🛠️ PHASE 6: Testing and Tuning

- [ ] Build test cases with known PII patterns and decoys
- [ ] Tune detection rules and scoring model
  - Minimize false positives and false negatives
- [ ] Set up periodic or on-demand scanning schedule

---

## 🛡️ Optional Future Enhancements

- [ ] Use ML models to classify form risk

---
