# 🔐 **CAP-3: Privilege & Privacy-Aware Activity Compartment Codes**


## 0. Presentation
CAP-3 stands for Compartmentalized activity & privacy.
It's meant for email and username generations or account name generations while raising user's awarness of the sensivity and exposure of their data online.
It is meant for password managers.

Here is an example :
`alice.nguyen522@proton.com` could be an email use for a league of legends account.
- `5` stands for *admin level* access (managing the league account)
- `2` stands for limited (niche) but publicly available account (league), how data is exposed outside of your control 
- `2` stands for low sensitivity activity (not health or banking), how sensitive do YOU feel about data being collected about this activity
- while `alice.nguyen` is a copmpletely fictive name formated this way to avoid robot protections.

Most of your emails will start with 5, however your bitwarden email should start with `F` or `9` for example.
An email adress is somewhat protected while exposed so the 2nd digit should be between 3 and 7
Finally the last digit is the value the data held by this account is precious to you.

## 1. Overview

* **Who can access/use the activity** (privilege/sensitivity)
* **How public the data collected by this activity is** (data exposure)
* **How sensitive the activity itself is** (activity privacy)

Each 3-digit code follows the pattern:

```
A B C
│ │ └── Activity Sensitivity / Privacy (low → high)
│ └──── Data Exposure Level (0 = fully public → 10 = local + encrypted )
└────── Inward Privileges / Actor Sensitivity (0 = normal → F = vault)
```

## 2. Usage
Originally this was meant for username generation for personnal usage.
For example if I wanf to create a new email account that will hold a league of legends account I could give it the name of
* thiery.beauchamp654@cocks.li

Exposing directly the level of privacy held by the account.
A more secure way of using CAP-3 would be :
* marc.platreuxxxddd@cocks.li (helding the league account)

saving the credentials of this email account on a password manager under the name :
* Docteur Lachatte#euw 654

Protecting the digits

## 3. Security
As explained above, the security of the usage of this code relies on the multiplicity of this method on a public AND individual level.
While also looking and mimicking somewhat common username usage.

A great number of people using this code in different ways could be a way to protect its users.
But also its notoriety compromises its purpose.


**ai slop**
---

## 4. Code Architecture

### **Digit 1 — Inward Privileges / Actor Sensitivity (A)**

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

### **Digit 2 — Data Exposure / Publicness (B)**

Represents **how public the data generated/collected by this activity is**:

| Digit | Meaning                                    |
| ----- | ------------------------------------------ |
| 0-2     | Fully public / internet accessible         |
| 2-4     | Public but limited visibility              |
| 4-6     | Semi-private / internal minor companies + encrypted     |
| 6-8     | Restricted / local only not encrypted         |
| 8-9     | Controlled / local only + password protected + encrypted |

> Important: **highly sensitive activities should not map to B=0**, to avoid dangerous public exposure.

---

### **Digit 3 — Activity Sensitivity / Privacy (C)**

Represents the **intrinsic privacy of the activity itself**:

| Digit | Meaning                                                                  |
| ----- | ------------------------------------------------------------------------ |
| 0–2   | Low-sensitivity activity (gardening, hobbies, general browsing)          |
| 3–5   | Medium-sensitivity (health, social posts, financial tracking)            |
| 6–7   | High-sensitivity (banking, confidential work)                            |
| 8–9   | Critical / top-secret activity (cryptography, ssh, vault access) |

---

## 5. Generating a Code
mmm.  l n. llml
1. **Determine Inward Privilege (Digit A)**

   * Who can perform/use this activity?
   * Examples:

     * Account holds no privileges → `0`
     * Account used for community moderation → `4`
     * Admin devops operations → `7`
     * Vault-level credentials → `F`

2. **Determine Data Exposure (Digit B)**

   * How public is the data generated/collected by this activity?
   * Examples:

     * Publicly exposed username → `0`
     * username is a little protected → `3`
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


