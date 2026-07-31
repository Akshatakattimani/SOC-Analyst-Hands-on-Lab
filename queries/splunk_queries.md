# Splunk SPL Queries

This document contains SPL (Search Processing Language) queries used during my SOC Analyst hands-on lab.

---

## 1. Total Events by Sourcetype

```spl
index=data
| stats count by sourcetype
```

### Purpose

Displays the number of events grouped by sourcetype.

---

## 2. Failed Login Attempts

```spl
index=_audit action="login attempt" info=failed
| stats count as failed_attempts by user
| sort - failed_attempts
```

### Purpose

Identifies users with the highest number of failed login attempts.

---

## 3. Successful Login Attempts

```spl
index=_audit action="login attempt" info=granted
| stats count by user
```

### Purpose

Shows successful user logins.
