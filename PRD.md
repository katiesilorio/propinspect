# Product Requirements Document
## PropInspect – AI-Powered Property Inspection & Vendor Management Platform

**Version:** 1.0  
**Status:** Draft  
**Author:** Katie Silorio 
**Last Updated:** February 2026

---

## Table of Contents
1. [Overview](#overview)
2. [Problem Statement](#problem-statement)
3. [Goals & Success Metrics](#goals--success-metrics)
4. [User Personas](#user-personas)
5. [Features & Requirements](#features--requirements)
   - [Inspection Module](#1-inspection-module)
   - [AI Move-Out Report](#2-ai-move-out-report)
   - [Vendor Management Module](#3-vendor-management-module)
   - [Work Order Generation](#4-work-order-generation)
   - [Vendor Portal](#5-vendor-portal)
   - [Security Deposit Deduction Report](#6-security-deposit-deduction-report)
6. [User Stories](#user-stories)
7. [System Architecture Overview](#system-architecture-overview)
8. [Out of Scope](#out-of-scope)
9. [Open Questions](#open-questions)
10. [Appendix](#appendix)

---

## Overview

PropInspect is a web and mobile application that streamlines the property move-out process for property managers. It enables property managers to conduct structured property inspections room-by-room, use AI to generate tenant-facing move-out reports and vendor work orders, manage vendor relationships, and produce itemized security deposit deduction summaries — all in one platform.

---

## Problem Statement

When a tenant vacates a rental property, property managers face a fragmented and time-consuming process:

- **Inspections are unstructured**, often done with pen-and-paper or generic apps not designed for property management.
- **Vendor coordination is manual**, with work orders sent via email or text with no centralized tracking.
- **Tenant communication lacks professionalism**, with no standardized, shareable documentation of property condition.
- **Security deposit disputes arise** due to poor documentation and lack of a clear, itemized record of damages and costs.

PropInspect solves these problems by providing a single platform that connects inspections, vendor coordination, and tenant documentation through AI-generated outputs.

---

## Goals & Success Metrics

### Goals
- Reduce the average time to complete a move-out inspection and issue a work order by 60%
- Provide property managers with professional, defensible documentation for security deposit deductions
- Give vendors a self-service portal to manage work and submit invoices
- Improve tenant transparency through AI-generated move-out reports

### Success Metrics
| Metric | Target |
|---|---|
| Average time to complete inspection | < 20 minutes |
| Work order generation time (post-inspection) | < 5 minutes |
| Vendor invoice submission via portal | ≥ 80% of invoices submitted digitally |
| Property manager NPS | ≥ 50 |
| Security deposit dispute rate | Decrease by 30% |

---

## User Personas

### 1. Property Manager (Primary)
- Manages single or multiple rental properties
- Needs to document move-out condition, coordinate repairs, and communicate with tenants and vendors
- Values speed, professionalism, and legal defensibility

### 2. Vendor / Contractor
- Receives work orders from property managers
- Needs a simple interface to view job details, update status, and submit invoices
- May not be tech-savvy; UX must be simple and mobile-friendly

### 3. Tenant (Recipient / Read-Only)
- Receives AI-generated move-out report via PDF
- Not a platform user, but a stakeholder in the output
- Values transparency and clear communication about their deposit

---

## Features & Requirements

---

### 1. Inspection Module

**Description:** Enables property managers to conduct a structured, room-by-room inspection of a property at move-out.

#### Functional Requirements

**Property & Room Management**
- Property managers can create a property profile (address, unit number, tenant name, move-out date)
- Property managers can add and remove rooms from a property (e.g., Living Room, Kitchen, Bedroom 1, Bathroom 1)
- Room templates may be suggested based on property type (e.g., 2BR/1BA auto-populates standard rooms)

**Room Condition Assessment**
- Each room contains a configurable list of components (e.g., walls, floors, ceiling, windows, doors, fixtures, appliances)
- Property managers can set the condition of each component using a standardized scale:
  - ✅ Good Condition
  - ⚠️ Needs Cleaning
  - 🔧 Needs Repair
  - ❌ Needs Replacement
- Property managers can add free-text notes per component
- Property managers can attach photos to individual components
- Inspection progress is auto-saved

**Inspection Summary**
- Upon completing the inspection, the system displays a summary of all flagged items (anything not marked "Good Condition")
- Property managers can review and edit before finalizing

---

### 2. AI Move-Out Report

**Description:** Generates a professional, tenant-facing PDF documenting the condition of the property at move-out.

#### Functional Requirements
- After finalizing the inspection, the property manager can trigger AI-generated report creation with one click
- The AI synthesizes inspection notes and condition ratings into a professionally written narrative per room
- The report includes:
  - Property and tenant information
  - Move-out date
  - Room-by-room condition summary with photos
  - List of items flagged for cleaning, repair, or replacement
  - Property manager signature block
- The PDF can be downloaded and/or emailed directly to the tenant from the platform
- Report tone is neutral, factual, and professional

---

### 3. Vendor Management Module

**Description:** A directory of vendors available to a property manager, organized by trade or service type.

#### Functional Requirements
- Property managers can add vendors with the following fields:
  - Name, company name, contact info (phone, email)
  - Service type(s) (e.g., Plumbing, Painting, Flooring, General Handyman, Cleaning)
  - Notes / preferred vendor flag
- Property managers can edit and remove vendors
- Vendor list is filterable by service type
- Vendors can be invited to create a Vendor Portal account (see Module 5)

---

### 4. Work Order Generation

**Description:** Allows property managers to assign vendors to specific repair items from an inspection and use AI to generate a consolidated work order per vendor.

#### Functional Requirements
- From the inspection summary, property managers can assign a vendor to each flagged item
- Multiple items can be assigned to the same vendor
- Once assignments are made, the property manager can generate a work order per vendor with one click
- The AI-generated work order includes:
  - Property address and access instructions (if provided)
  - Vendor name and contact
  - Aggregated, itemized list of all items assigned to that vendor across all rooms
  - Notes and photos attached to each item
  - Requested completion date
- Work orders are sent to the vendor via email and appear in the Vendor Portal
- Property managers can track work order status (Sent, In Progress, Completed)

---

### 5. Vendor Portal

**Description:** A lightweight, self-service web portal where vendors can view their work orders, update job status, and submit invoices.

#### Functional Requirements

**Work Order Management**
- Vendors log in via a unique invite link or credentials
- Vendors can view all open and historical work orders assigned to them
- Each work order displays: property address, itemized task list, photos, notes, and requested completion date
- Vendors can update status per work order: Accepted, In Progress, Completed
- Vendors can add notes or photos to individual line items

**Invoice Submission**
- Vendors can submit an invoice per work order
- Invoice fields include: line items, labor/materials breakdown, total amount, and date
- Vendors can upload a PDF invoice as an attachment
- Submitted invoices are visible to the property manager in their dashboard
- Property managers can mark invoices as Approved or Disputed with notes

---

### 6. Security Deposit Deduction Report

**Description:** Enables property managers to generate a formal, itemized document outlining charges to be deducted from the tenant's security deposit.

#### Functional Requirements
- Property managers can create a Security Deposit Report linked to a completed inspection
- They can select which repair/replacement items to include as deductions
- For each line item, they can input or pull the cost from an approved vendor invoice
- The system calculates the total deduction amount
- AI generates a formal narrative explaining each deduction in clear, professional language
- The report includes:
  - Tenant and property information
  - Original security deposit amount
  - Itemized deductions with descriptions, photos, and costs
  - Total deduction and refund amount
  - Legal disclaimer block (configurable by state)
- The report is exportable as a PDF and can be emailed to the tenant from the platform

---

## User Stories

### Property Manager
- As a property manager, I want to add and customize rooms for a property so that my inspection reflects the actual layout of the unit.
- As a property manager, I want to document the condition of each component in a room with photos and notes so that I have defensible records.
- As a property manager, I want AI to generate a professional move-out report so that I can share a polished document with my tenant quickly.
- As a property manager, I want to assign repair items to vendors and generate AI work orders so that I don't have to manually write up job scopes.
- As a property manager, I want to track work order status across all vendors from a single dashboard so that I have visibility into the repair process.
- As a property manager, I want to generate an itemized security deposit deduction report so that my tenant understands exactly what is being charged and why.

### Vendor
- As a vendor, I want to view my assigned work orders in a portal so that I know exactly what needs to be done and where.
- As a vendor, I want to update the status of my work orders so that the property manager stays informed without me having to call or text.
- As a vendor, I want to submit my invoice through the portal so that I get paid faster without chasing down the property manager.

---

## System Architecture Overview

> *Note: This section reflects intended architecture and is subject to technical discovery.*

| Layer | Technology (Suggested) |
|---|---|
| Frontend (Web) | React.js |
| Mobile | React Native (iOS & Android) |
| Backend | Node.js / Express or Python / FastAPI |
| Database | PostgreSQL |
| File Storage | AWS S3 (photos, PDFs) |
| AI / LLM | Anthropic Claude API (report & work order generation) |
| PDF Generation | Puppeteer or React-PDF |
| Auth | Auth0 or Supabase Auth |
| Email | SendGrid |

---

## Out of Scope (v1.0)

- Lease management or rent collection
- Tenant-facing portal or app (tenants receive PDFs only)
- Online payment processing for vendor invoices
- Multi-user / team accounts for property management companies
- Integration with property management platforms (e.g., AppFolio, Buildium)
- Move-in inspection (v2 candidate)

---

## Open Questions

| # | Question | Owner | Status |
|---|---|---|---|
| 1 | What states' legal disclaimer language should be supported at launch? | PM | Open |
| 2 | Should vendors be able to dispute work order items before accepting? | PM | Open |
| 3 | Is there a need for a native mobile app at v1, or is a mobile-responsive web app sufficient? | PM / Eng | Open |
| 4 | What is the pricing model — per property, per user, or subscription? | PM / Business | Open |
| 5 | Should AI report generation require review before sending, or allow direct send? | PM | Open |

---

## Appendix

### Condition Rating Scale
| Rating | Definition |
|---|---|
| ✅ Good Condition | No action needed; normal wear acceptable |
| ⚠️ Needs Cleaning | Professional cleaning required |
| 🔧 Needs Repair | Component is damaged and requires repair |
| ❌ Needs Replacement | Component is beyond repair and must be replaced |

### Glossary
- **Inspection** – A structured assessment of a property's condition at the time of tenant move-out
- **Work Order** – A formal document issued to a vendor detailing repair tasks for a specific property
- **Vendor Portal** – A web interface for vendors to manage their work orders and submit invoices
- **Security Deposit Deduction Report** – A formal document itemizing charges to be withheld from a tenant's security deposit
