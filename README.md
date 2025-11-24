# 📘 **CAP-3: Privilege & Privacy-Aware Activity Compartment Codes**


# 1. Overview

* **Who can access/use the activity** (privilege/sensitivity)
* **How public the data collected by this activity is** (data exposure)
* **How sensitive the activity itself is** (activity privacy)

Each 3-digit code follows the pattern:

```
A B C
│ │ └── Activity Sensitivity / Privacy (low → high)
│ └──── Data Exposure Level (0 = fully public → 4 = restricted public)
└────── Inward Privileges / Actor Sensitivity (0 = normal → F = vault)
```

---

# 2. Code Architecture

## **Digit 1 — Inward Privileges / Actor Sensitivity (A)**

Represents the **privilege level required to perform or access this activity**:

| Digit | Meaning                                              |
| ----- | ---------------------------------------------------- |
| 0     | Standard / everyday user                             |
| 1–4   | Elevated privileges / internal teams                 |
| 5–9   | Admin-level access / sensitive operations            |
| A–E   | Highly restricted / specialized                      |
| F     | Vault-level / top-secret / cryptographic credentials |

> This digit controls **who inside the system may perform this activity**. Higher letters = more sensitive access needed.

---

## **Digit 2 — Data Exposure / Publicness (B)**

Represents **how public the data generated/collected by this activity is**:

| Digit | Meaning                                    |
| ----- | ------------------------------------------ |
| 0     | Fully public / internet accessible         |
| 1     | Public but limited visibility              |
| 2     | Semi-private / logged by third parties     |
| 3     | Restricted / internal company only         |
| 4     | Controlled / minimal access / private data |

> Important: **highly sensitive activities should not map to B=0**, to avoid dangerous public exposure.

---

## **Digit 3 — Activity Sensitivity / Privacy (C)**

Represents the **intrinsic privacy of the activity itself**:

| Digit | Meaning                                                                  |
| ----- | ------------------------------------------------------------------------ |
| 0–2   | Low-sensitivity activity (gardening, hobbies, general browsing)          |
| 3–5   | Medium-sensitivity (health, social posts, financial tracking)            |
| 6–7   | High-sensitivity (banking, confidential work)                            |
| 8–9   | Critical / top-secret activity (cryptography, credentials, vault access) |

---

# 3. Generating a Code

1. **Determine Inward Privilege (Digit A)**

   * Who can perform/use this activity?
   * Examples:

     * Standard personal hobby → `0`
     * Accessing company HR data → `4`
     * Admin system operations → `7`
     * Vault-level credentials → `F`

2. **Determine Data Exposure (Digit B)**

   * How public is the data generated/collected by this activity?
   * Examples:

     * Public gardening posts → `0`
     * Health tracking in a private app → `3`
     * Bank transactions → `4`

3. **Determine Activity Sensitivity (Digit C)**

   * How intrinsically sensitive is the activity itself?
   * Examples:

     * Browsing hobbies → `1`
     * Health logging → `4`
     * Banking credentials → `9`

> Compose the three digits: `ABC`

---
### **Personal / Hobby Activities**

| Code | Meaning                                         |
| ---- | ----------------------------------------------- |
| 001  | Personal browsing, public info, low sensitivity |
| 013  | Personal browsing, semi-private, hobby          |
| 024  | Health notes, restricted, low-medium activity   |

### **Finance / Banking**

| Code | Meaning                                                               |
| ---- | --------------------------------------------------------------------- |
| 347  | Bank transactions, internal company exposure, medium-high sensitivity |
| 4F9  | Vault-level banking access, controlled exposure, high-critical        |

### **Technical / Dev / Admin**

| Code | Meaning                                                               |
| ---- | --------------------------------------------------------------------- |
| 703  | Admin development tasks, restricted, medium privacy                   |
| F42  | Vault credentials, private internal data, medium activity sensitivity |

### **Forbidden / Invalid Examples**

* `909` → Publicly available + top-secret credentials → invalid
* `F00` → Vault access + fully public → invalid
