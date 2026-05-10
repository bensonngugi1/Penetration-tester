# SQL Injection Vulnerability Assessment Report

**Prepared For:Anyone it may concern**
**Prepared By:[Benson Ngugi](https://github.com/bensonngugi1)**
**Course:Certified Ethical Hacker**
**Date:10/05/2026**

## Executive Summary

### Overview

This report presents the finding of a security assessment conducted on a target web application to identify SQL Injection vulnerabilities.The assessment was focused on evaluating how user input is processed by the application and whether it could be manipulated to access unauthorized data or affect how database operates.

### Key Findings

-The assessment identifies the following issues:

* SQLi vulnerability in user input  parameters.
* Improper sanitization of user controlled input.
* Exposure of backend database behaviour through SQL errors.
* Unauthorized access of sensitive information.

### Risk Summary

* Bypass authetication.
* Access to database information.
* Modify or delete records
* Escalate privileges.
* Compromise confidentiality,integrity and availability.

### Recommendations

* Implement parameterized queries and use prepared statements.
* Validate and sanitize all user input.
* Use least privilege database accounts.
* Disable verbose database error messages.
* Conduct regular security testing.

Reference guidance from:
[Portswigger website](portswigger.net)

## Scope and Objectives

### Scope

-The assessment was covered on the following componenets:

* Web app input fields.
* Login functionality.
* URL parameters.
* Search functionalities
* Database interaction points.

**Target:**

[This website](https://0a4900e703bc229c808ea88200720015.web-security-academy.net/)

### Objectives

* Identify SQLi vulnerabilities.
* Assess the impact of discovered vulnerabilities to an organization.
* Determine exploitability.
* Provide remediation recommendations.

### Rules of Engagement

* Test the authorized target only.
* No DDOS to be performed.
* No permanent change to the production systems.
* Testing on a given timelines.

## Methodology

### Reconnaissance

-This is gathering of the information to understand the structure of application and possible attack surfaces.
-Activities include:

* Identify input fields.
* Mapping URLs and parameters.
* Understanding application behaviour.

[Proof of evidence](SCREENSHOTS/Screenshot_20260510_131952.png)

### Vulnerability Analysis

-The application was tested for potential SQLi entry points using manual testing techniques and security tools.
-The identified parameters were analyzed to determine whether user input was improperly handled within SQL queries.
-The indicator observed:

* SQL syntax errors.
* Authetication bypass behaviour.
* Abnormal application responses.

[Proof](SCREENSHOTS/Screenshot_20260510_133827.png)

### Exploitation

-We tested using the following payload

```SQL
' OR '1'='1
```

```SQL
admin' --
```

-The following outcome was observed:

* Unauthorized data access.
* Display of all items including unreleased ones.
* Authetication bypass.
  
[Display of all items](SCREENSHOTS/Screenshot_20260510_114711.png)

[Authetication bypass](SCREENSHOTS/Screenshot_20260510_115043.png)

### Reporting

-All findings were documented with:

* Evidence
* Risk ratings
* Technical explanations
* Recommended mitigations

## Tools Used

| Tool | Purpose|
|---   |---     |
| Burp Suite| For intercepting and modifying requests  |
| SQLMap   | SQLi testing   |
| Browser developer tools  | Inspecting requests and responses  |

-Official websites:

* [Burp Suite](https://portswigger.net/burp)
* [SQLMap](https://sqlmap.org/)

## Detailed Findings

-The test confirmed the presence of SQLi vulnerability on user controlled inputs within the application.

-The vulnerability allows malicious SQL queries to be injected into backend database queries.

## Vulnerability Title

### SQL Injection Vulnerability

#### Types

##### 1.Boolean-Based SQLi

-This is where two different payloads are injected to the input field to observe the difference in responses.

###### Payloads

```SQL
' OR 1=1
```

```SQL
' OR 1=2
```
