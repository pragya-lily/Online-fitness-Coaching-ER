#  Online Fitness Coaching Platform – ER Diagram

##  Overview

This project represents the **Entity-Relationship (ER) Diagram** for an online fitness coaching platform designed for fitness influencers and trainers.

The platform supports:

* Client onboarding
* Selling fitness plans/programs
* Subscription management
* Consultation/session scheduling
* Progress tracking (check-ins, body metrics)
* Trainer feedback and notes

Unlike traditional gym systems, this platform focuses on a **fully online coaching ecosystem** where trainers manage clients remotely.

---

##  Objective

The goal of this ER diagram is to model a scalable database that can answer key business questions such as:

* Who are the trainers and clients?
* Which plans are offered and who subscribed to them?
* How are subscriptions and payments handled?
* How are consultations and sessions managed?
* How is client progress tracked over time?

---

##  Core Entities

###  USER

* Stores basic information for all users
* Differentiates between **Trainer** and **Client** using `role_type`

---

###  TRAINERPROFILE

* Extends USER for trainers
* Contains:

  * Bio
  * Specialty
  * Social handle
  * Onboarding date

---

###  CLIENTPROFILE

* Extends USER for clients
* Stores:

  * Physical details (height, gender)
  * Goals
  * Join date

---

###  PROGRAMPLAN

* Represents coaching plans created by trainers
* Includes:

  * Plan type (consultation / full coaching)
  * Duration
  * Pricing
  * Feature flags (diet, workout, live sessions)

---

###  SUBSCRIPTION

* Tracks recurring plan purchases
* Includes:

  * Billing cycle
  * Start and end dates
  * Auto-renew status

---

###  CLIENTENROLLMENT

* Connects clients with plans and trainers
* Supports:

  * Multiple enrollments over time
  * Optional subscription linkage

---

###  PAYMENT

* Stores transaction details
* Can be linked to:

  * Subscription OR
  * One-time enrollment

---

###  SESSION

* Represents scheduled consultations or live sessions
* Includes:

  * Time
  * Meeting link
  * Status
  * Notes summary

---

###  CHECKIN

* Weekly/periodic client updates
* Tracks:

  * Adherence
  * Energy levels
  * Sleep
  * Comments

---

###  PROGRESSMETRIC

* Stores detailed body metrics per check-in:

  * Weight
  * Body fat %
  * Measurements (waist, chest, etc.)
  * Progress photos

---

###  TRAINERNOTE

* Trainer feedback and observations
* Can optionally relate to:

  * A session OR
  * A check-in

---

##  Relationships & Cardinality

* One **Trainer** ➝ Many **Program Plans**
* One **Trainer** ➝ Many **Clients**
* One **Client** ➝ Many **Enrollments**
* One **Plan** ➝ Many **Clients**
* One **Enrollment** ➝ Many:

  * Sessions
  * Check-ins
  * Trainer Notes
* One **Check-in** ➝ Many **Progress Metrics**
* One **Subscription** ➝ Many **Payments**

---

##  Key Design Decisions

### 1. User Abstraction

* A single `USER` table is used with role differentiation
* Profiles are separated to avoid null-heavy tables

---

### 2. Enrollment vs Subscription

* **Enrollment** = access to a plan
* **Subscription** = payment model (recurring)
* This allows flexibility for:

  * One-time purchases
  * Subscription-based coaching

---

### 3. Separation of Check-ins & Sessions

* Sessions = interaction (calls/meetings)
* Check-ins = progress reporting
* This keeps tracking structured and scalable

---

### 4. Flexible Plan Features

Boolean flags allow plans to differ:

* Consultation-only
* Full coaching
* Diet/workout inclusion

---

### 5. Modular Progress Tracking

* Metrics are separated from check-ins
* Allows:

  * Multiple entries
  * Future expansion (new metrics)

---

### 6. Trainer Notes Decoupled

* Notes are independent entities
* Can optionally relate to sessions or check-ins
* Improves flexibility in feedback tracking

---

##  Scalability Considerations

* Supports multiple trainers and clients
* Allows clients to purchase multiple plans over time
* Easily extendable for:

  * Mobile apps
  * Analytics dashboards
  * AI-based recommendations

---

##  Submission Details

* ER Diagram File: online fitness coaching ER diagram.pdf
* Format: Horizontal layout
* Includes:

  * Primary Keys (PK)
  * Foreign Keys (FK)
  * Clearly defined relationships

---

##  Conclusion

This ER diagram provides a **practical and scalable database design** for an online fitness coaching platform, balancing flexibility with real-world usability.

---
