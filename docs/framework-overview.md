# JMeter API Automation Framework – Overview

## Purpose
This framework is designed for enterprise-level API automation using Apache JMeter.
It supports API validation, database verification, Jira/Xray reporting, and CI execution
via Jenkins.

---

## Framework Design

### 1. Test Plan Structure
- One Thread Group per API for isolation and clarity
- Common Setup for shared configurations
- Modular and scalable design

---

### 2. Common Setup
Includes:
- User Defined Variables
- JDBC Connection Configuration (Old DB & New DB)
- Environment-level configurations

All sensitive values are externalized using property files.

---

### 3. API Layer
Each Thread Group contains:
- HTTP Request sampler
- JSON Assertion for response validation
- CSV result generation for API responses
- Debug Sampler for troubleshooting

---

### 4. Database Validation
- JDBC Request to fetch DB records
- JSR223 Assertion (Groovy) to compare API vs DB data
- Ensures backend data consistency

---

### 5. Reporting
- API responses saved in CSV format
- Execution results stored locally
- JMeter listeners used for analysis

---

### 6. Jira / Xray Integration
- Token-based authentication
- Automatic update of test execution status in Jira
- Results visible directly in Xray test executions

---

### 7. Jenkins CI Integration
- Jenkins job triggers JMeter execution
- CI-based execution without JMeter GUI
- Results automatically published to Jira

---

## Execution Modes

### Local Execution
```bash
jmeter -n -t test-plans/jmeter-api-automation.jmx
