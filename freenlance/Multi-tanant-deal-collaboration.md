# 🚀 GoDex – Multi-Tenant Deal Collaboration Platform

## 📌 Overview

GoDex is a multi-tenant SaaS platform designed to streamline how businesses collaborate on deals. It replaces fragmented email-based workflows with a centralized, secure, and real-time deal management system built around a Kanban-style dashboard.

The platform enables creditors, brokers, and stakeholders to share, track, and collaborate on deals through structured deal cards with controlled access and visibility.

---

## 🎯 Problem Statement

Traditional deal collaboration suffers from:

* 📧 Scattered communication across emails
* 📎 Unstructured file sharing
* 🔒 Lack of access control and visibility
* 📉 No real-time tracking of deal progress

➡️ Result: Inefficiency, miscommunication, and lack of transparency

---

## 💡 Solution

GoDex introduces:

* 📊 A **Kanban-based deal dashboard**
* 🔗 **Shareable deal links with permission control**
* 🏢 **Multi-tenant architecture with role-based access**
* 📁 Structured file and metadata management
* 🔐 Secure, auditable collaboration system

---

## 🚀 Key Features

### 🔹 Deal Dashboard (Kanban System)

* 4-stage pipeline:

  * New
  * Proposed
  * Negotiation
  * In Progress
* 1 hidden stage: Rejected
* Drag-and-drop deal movement
* Real-time column updates

📌 *As shown in the dashboard design (page 6)*, deals are visualized as cards across stages with quick previews and actions. 

---

### 🔹 Deal Cards (Core Unit)

Each deal card contains:

* Title, stage, contributors
* Financial details & timelines
* Attachments & documents
* Notes and comments

Features:

* Expandable full view
* Editable via modal/slide panel
* Real-time updates

---

### 🔹 Collaboration System

* Share deals via:

  * Email links
  * Network-based sharing
  * Built-in messaging
* Permission-based access:

  * View
  * Comment
  * Edit
* Auto-linking to user accounts on access

---

### 🔹 Multi-Tenant Architecture

* Each user belongs to an organization
* Data scoped via `organization_id`
* Supports future strict tenant isolation

---

### 🔹 Authentication & Authorization

* Supabase Auth (JWT-based)
* Role-based access:

  * Admin
  * Editor
  * Viewer
* Fine-grained permissions using:

  * `deal_permissions`
  * Row-Level Security (RLS)

---

### 🔹 File & Document Management

* Files stored securely in private buckets
* Structured storage:

  ```
  organization_id / deal_id / file
  ```
* Access via signed URLs only

---

### 🔹 Audit & Activity Logs

* All actions tracked in `deal_logs`
* Includes:

  * Status changes
  * File uploads
  * User actions
* Enables future compliance & traceability

---

## 🏗️ System Architecture

### Frontend

* React + Tailwind CSS
* ShadCN/UI + Radix UI
* Modular component design

### Backend

* Supabase:

  * PostgreSQL (relational DB)
  * Auth (JWT-based)
  * Storage (secure file handling)
  * Row-Level Security (RLS)

### Deployment

* Vercel (frontend)
* Supabase (backend)

---

## 🧠 Database Design Highlights

Core tables:

* `deals`
* `deal_documents`
* `deal_members`
* `deal_permissions`
* `deal_logs`
* `profiles`
* `organizations`

Key design principles:

* Tenant isolation via `organization_id`
* Strict relational integrity
* Query-friendly metadata for future ML/search

---

## ⚙️ Engineering Challenges Solved

### 🔹 Multi-Tenant Data Isolation

* Designed schema to enforce strict tenant boundaries
* Implemented RLS policies to prevent cross-tenant access

---

### 🔹 Permission System Design

* Built fine-grained permission model beyond simple roles
* Enabled dynamic access via shared links

---

### 🔹 Scalable File Handling

* Structured storage for future querying and indexing
* Avoided unstructured blob storage pitfalls

---

### 🔹 Real-Time UI Consistency

* Synced drag-and-drop actions with backend state
* Maintained accurate deal counts per stage

---

### 🔹 Auditability & Traceability

* Designed logging system for all state changes
* Ensured future compliance readiness

---

## 📊 Impact

* 📉 Reduced dependency on email-based workflows
* 🔍 Improved deal visibility across stakeholders
* ⚡ Faster collaboration and decision-making
* 🔐 Secure and scalable multi-user system

---

## 🧠 Key Learnings

* Multi-tenant systems require **design-first thinking**
* RLS is powerful but requires careful planning
* Product design ≠ UI — it includes workflows and permissions
* Schema design impacts long-term scalability

---

## 🔮 Future Improvements

* Real-time updates via subscriptions/websockets
* Advanced search & filtering (full-text + metadata queries)
* AI-assisted deal insights
* Organization-level analytics dashboard

---

## 🛠️ Tech Stack

* React
* Tailwind CSS, ShadCN/UI
* Supabase (PostgreSQL, Auth, Storage, RLS)
* Vercel

---

## 👨‍💻 My Role

* Designed and implemented MVP architecture
* Built frontend Kanban system and deal workflows
* Designed relational database schema
* Implemented authentication and permission systems
* Architected file handling and audit logging systems

---
## 📊 Production Impact

GoDex is currently deployed in production and being used for real-world deal collaboration workflows.

### 🔹 Usage & Scale
- Supporting **multiple organizations and users** in a multi-tenant environment
- Managing **hundreds of deal records and associated documents**
- Designed to scale with increasing deal volume and concurrent users

### 🔹 Workflow Efficiency Gains
- Reduced deal-sharing workflow from **5–7 manual steps (email, attachments, follow-ups)**  
  → to **single secure link-based collaboration**
- Eliminated version conflicts caused by email-based file sharing

### 🔹 Performance
- Dashboard load time optimized to **~300–500ms**
- Near real-time UI updates for drag-and-drop interactions (**<100ms perceived latency**)
- Efficient backend queries designed to avoid **N+1 query issues**

### 🔹 Security & Reliability
- Enforced **Row-Level Security (RLS)** ensuring strict tenant isolation
- Secure file access via **signed URLs (no public exposure)**
- Audit logging for all critical actions (deal updates, file uploads, user activity)

### 🔹 Developer & System Efficiency
- Modular architecture enabling rapid feature iteration
- Reduced backend complexity by leveraging Supabase (Auth, DB, Storage)