# 🚗 WhatsNext Vision Motors – Salesforce CRM

A Salesforce-based automotive dealership management solution that streamlines the vehicle ordering process, automates dealer assignment, and enforces real-time stock validation.

---

## 📋 Table of Contents

- [Project Overview](#project-overview)
- [Features](#features)
- [Data Model](#data-model)
- [Automation & Apex](#automation--apex)
- [What You'll Learn](#what-youll-learn)
- [Functional Testing](#functional-testing)
- [Performance Benchmarks](#performance-benchmarks)

---

## Project Overview

WhatsNext Vision Motors is a pioneering force in the automotive industry, dedicated to transforming the mobility sector with innovative technology. This Salesforce CRM project addresses three core operational challenges:

- **Nearest Dealer Suggestion** — Automatically recommends the closest dealer to a customer based on their address, reducing friction in the ordering experience.
- **Stock Validation** — Prevents customers from placing orders for vehicles that are out of stock, avoiding confusion and improving order accuracy.
- **Automated Order Status Management** — A scheduled batch process updates bulk order records to `Confirmed` or `Pending` based on real-time stock availability.

Demo link - https://drive.google.com/file/d/1m7lv4wjME_JSO82bcF0s3uc-jDGwTCvz/view?usp=sharing
---

## Features

| Module | Description |
|--------|-------------|
| 🚘 Vehicle & Stock Management | Store vehicle details, track stock levels, and link inventory to dealers |
| 📦 Customer Order Management | Create and manage orders with automatic status assignment |
| 📍 Dealer Assignment Automation | Auto-assign orders to the nearest dealer based on customer location |
| 🔒 Stock Validation | Block order placement when a vehicle is out of stock |
| ⚙️ Batch & Scheduled Processing | Periodically update order statuses and send stock notification emails |
| 🗓️ Test Drive & Service Tracking | Schedule test drives and send automated email reminders |

---

## Data Model

```
Customer
  └── Order ──── Vehicle
        └── Dealer
  └── Test Drive
  └── Service Request
```

**Custom Objects:**

- **Vehicle** — Model, make, price, stock quantity, availability status
- **Dealer** — Name, location, address, assigned region
- **Order** — Customer, vehicle, dealer, status (`Confirmed` / `Pending`), order date
- **Test Drive** — Customer, vehicle, scheduled date, status
- **Service Request** — Customer, vehicle, issue description, status

---

## Automation & Apex

### Record-Triggered Flows
- Suggest nearest dealer when a new order record is created
- Trigger notifications on order status changes

### Apex Triggers
- **Stock Validation Trigger** — Prevents order creation if the vehicle's stock quantity is zero
- **Dealer Assignment Trigger** — Automatically assigns the nearest dealer based on customer address on order insert

> Triggers follow the **trigger handler pattern** for modularity and maintainability.

### Batch Apex
- Processes bulk order records on a schedule
- Updates order status to `Confirmed` if vehicle is in stock, `Pending` if out of stock

### Scheduled Apex
- Runs daily at **6:00 AM**
- Sends stock replenishment alerts and order processing email notifications

---

## What You'll Learn

This project covers the following Salesforce development concepts:

- **Data Modelling** — Designing custom objects, fields, and relationships
- **Fields and Relationships** — Lookup and master-detail relationships across objects
- **Lightning App Builder** — Building a custom Lightning app for the CRM experience
- **Record Triggered Flows** — Automating dealer suggestions and notifications
- **Apex and Apex Triggers** — Enforcing business rules with modular trigger handlers
- **Batch Apex** — Processing large record sets for order status updates
- **Scheduled Apex** — Running automated jobs on a daily schedule

---

## Functional Testing

| Test Case | Area | Status |
|-----------|------|--------|
| TC-01 / TC-02 | Vehicle and stock record creation | ✅ Pass |
| TC-03 | Order blocked when vehicle is out of stock | ✅ Pass |
| TC-04 | Nearest dealer auto-assigned by customer location | ✅ Pass |
| TC-05 | Apex trigger logic for dealer assignment and order validation | ✅ Pass |
| TC-06 | Batch job updates order status to Confirmed or Pending | ✅ Pass |
| TC-07 | Scheduled Apex for stock replenishment notifications | ✅ Pass |
| TC-08 | Automated test drive email reminders | ✅ Pass |
| TC-09 / TC-10 | Reports and dashboard validation | ✅ Pass |
| TC-11 | Security and role-based access validation | ✅ Pass |

---

## Performance Benchmarks

| Metric | Target | Result |
|--------|--------|--------|
| Page Load Time | < 3 seconds | ~1.7 seconds |
| Report Generation | < 5 seconds | ~3.0 seconds |
| Apex Trigger Execution | < 2 seconds | ~0.8 seconds |
| Automated Email Delivery | Operationally acceptable | ~25 seconds |
| Batch Job Execution | Daily scheduled run | Runs daily at 6 AM ✅ |

---


## 📄 License

This project is developed for educational and demonstration purposes as part of the WhatsNext Vision Motors Salesforce CRM implementation.
