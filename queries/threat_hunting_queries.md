# Threat Hunting Queries

## Overview

This document contains threat hunting queries used during my SOC Analyst hands-on lab to identify suspicious activities, investigate security events, and support incident response.

---

## 1. Failed Login Attempts

```spl
index=_audit action="login attempt" info=failed
| stats count by user
| sort - count
```

**Purpose:** Identify accounts with multiple failed login attempts.

---

## 2. Successful Login Attempts

```spl
index=_audit action="login attempt" info=granted
| stats count by user
```

**Purpose:** Review successful authentication events.

---

## 3. SSH Activity

```spl
index=main sourcetype=ssh
| stats count by src_ip
| sort - count
```

**Purpose:** Monitor SSH connections and identify frequent source IP addresses.

---

## 4. Top Source IP Addresses

```spl
index=main
| stats count by src_ip
| sort - count
```

**Purpose:** Identify systems generating the highest number of events.

---

## 5. Authentication Activity Over Time

```spl
index=main
| timechart count by action
```

**Purpose:** Visualize authentication trends over time.

---

## Learning Outcome

These queries helped improve practical skills in:

- Threat Hunting
- Log Analysis
- Security Monitoring
- Incident Investigation
- SPL Query Development
