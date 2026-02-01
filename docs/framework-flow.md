# Framework Execution Flow

1. Jenkins triggers JMeter execution
2. JMeter loads configuration from property files
3. Thread Group executes API request
4. JSON assertions validate API response
5. JDBC query fetches DB data
6. JSR223 assertion compares API vs DB
7. Results stored in CSV files
8. Jira/Xray updated with execution status
