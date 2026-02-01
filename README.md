# JMeter API Automation Framework

Enterprise-level API automation framework built using Apache JMeter with
API, Database, Jira (Xray), and Jenkins integration.

---

## 🔧 Tech Stack
- Apache JMeter 5.6.3
- Java
- JDBC (DB Validation)
- Jira + Xray
- Jenkins CI/CD
- GitHub

---

## 📁 Framework Structure
- Separate Thread Group per API
- Common Setup for variables & DB connections
- CSV-based request & response handling
- Assertions:
  - JSON Assertion
  - JSR223 Assertion (Groovy)
- Debug Sampler for troubleshooting

---

## 🔄 Integrations
### ✅ Database Validation
- JDBC Request + JSR223 assertion
- API vs DB data comparison

### ✅ Jira / Xray
- Automatic test execution update in Jira
- Token-based authentication
- Test results pushed after execution

### ✅ Jenkins
- JMeter executed from Jenkins job
- CI trigger for API automation
- Results published to Jira

---
## 🚀 Key JMeter Features Implemented

- Multiple Thread Groups (API-level isolation)
- User Defined Variables for reusability
- JDBC Connection Pooling
- Groovy-based JSR223 assertions
- CSV-based result persistence
- Debug Sampler for troubleshooting
- Token-based authentication handling

-----

## ▶️ How to Run (Local)
```bash
jmeter -n \
 -t test-plans/API_Automation.jmx \
 -q config/user.properties \
 -l reports/result.jtl
