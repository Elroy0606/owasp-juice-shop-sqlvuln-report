# SQL Injection Penetration Test Report – OWASP Juice Shop

**Prepared by:** Elroy Fernandes  
**Date:** January 13, 2026  

---

## Executive Summary

This report documents a successful SQL Injection attack against the OWASP
Juice Shop login functionality conducted in a controlled local environment.
The vulnerability allowed authentication bypass using a simple SQL payload,
granting unauthorized administrative access.

**Key Finding:** SQL Injection (CWE-89)  
**Severity:** Critical  
**Impact:** Full authentication bypass and administrative access  
**Status:** Proof of Concept Achieved  

---

## Scope and Objectives

### Scope
- **Application:** OWASP Juice Shop (intentionally vulnerable application)
- **Version:** v19.1.1
- **Environment:** Kali Linux (VM)
- **Target Component:** Login functionality
- **Testing Method:** Manual penetration testing

### Objectives
- Identify authentication vulnerabilities
- Demonstrate SQL Injection exploitation
- Document findings and remediation steps
- Showcase ethical security testing methodology

---

## Technical Finding: SQL Injection (Authentication Bypass)

### Description

The login form does not use parameterized queries or prepared statements when
validating user credentials. By injecting SQL syntax into the username field,
an attacker can manipulate the backend query logic to always evaluate as true,
resulting in authentication bypass.

---

## Steps to Reproduce (Proof of Concept)

### Step 1: Navigate to Login Page
<p align="center">
	<img src="screenshots/02-login.png" alt="juice shop running" 
	width="60%">
</p>

### Step 2: Inject SQL Payload

Enter the following payload into the Email/Username field:

```sql
' OR 1=1--
```
<p align="center">
	<img src="screenshots/05-SQLpayload.png" alt="juice shop"
	width="60%"
</p>

