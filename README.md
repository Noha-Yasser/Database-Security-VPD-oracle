# database-security--VPD-oracle
This repository contains my implementation of four Oracle VPD security policies on the HR schema (Job History filtering, Salary masking, Time-based access, and Department update control). All scripts, screenshots, and documentation are included.
## Overview

### What is a Virtual Private Database (VPD)?
Oracle’s Virtual Private Database (VPD) is a security feature that applies fine-grained access control directly at the database level. VPD automatically appends security predicates to user queries, ensuring that each user can only view or modify the data permitted by their role, identity, or session context.

---

## Types of VPD Policies in Oracle

### Row-Level Security (RLS)
Controls which rows a user is allowed to read or update based on specific conditions.

### Column-Level Security
Hides or masks sensitive column data from unauthorized users.

### Time-Based Access
Restricts access to certain data depending on the time or business hours.

### Operation-Specific Policies
Applies security rules only to certain SQL operations, such as SELECT, UPDATE, or DELETE.

---

## Project Overview
This project demonstrates the implementation of several Oracle VPD policies on the HR schema within the PDBORCL pluggable database.  
The goal is to enforce dynamic, context-aware security rules that control data visibility and modification at both the row and column level.  
Session context values and VPD policy functions are used to apply these restrictions transparently and securely.

---

## Implemented Policies

### Job History Access Control (Row-Level Policy)
A policy on the `JOB_HISTORY` table:
- Employees can view only their own job history.
- Managers can view the job history of employees who report to them.
- HR Managers have full access to all job history records.

---

### Salary Data Protection (Column-Level Policy)
A column filtering policy on the `EMPLOYEES` table:
- Employees can view their own salary information.
- Salary data for other employees is hidden.
- HR and Financial Managers can view all salary details without restriction.

---

### Time-Based Access Control
Restricts access to the `EMPLOYEES` table to official working hours only.  
Outside these hours, all users are prevented from accessing the data.

---

### Department Location Update Control (Row-Level Update Policy)
A policy on the `DEPARTMENTS` table:
- Department Managers can update the `LOCATION_ID` for their own department only.
- HR Managers have permission to update any department.

---
